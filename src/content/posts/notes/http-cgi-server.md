---
title: CGI Server
published: 2025-10-30
description: "使用C语言学习网络编程并编写CGI Server"
image: ""
tags: []
category: "notes"
draft: false
lang: "zh-CN"
---

### 流程图

![CGI chart](https://img.hanzogenji.cn/i/2025/10/30/69031ea354cb5.png)

### Code

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <unistd.h>
#include <arpa/inet.h>
#include <time.h>

#define PORT 8080

typedef struct
{
    char method[64];
    char path[1024];
    char query_string[512];
    char version[64];
    char host[256];
    char connetion[64];
    char user_agent[512];
    char accept[512];
    char cookie[2048];
    char content_type[256];
    int content_length;
    char body[1024];
} http_request_t;

void log_request(const char *client_ip, http_request_t *request, int status_code)
{
    time_t now;
    char timestamp[64];

    time(&now);
    strftime(timestamp, sizeof(timestamp), "%Y-%m-%d %H:%M:%S", localtime(&now));

    printf("[%s] %s %s %s - Status: %d - Content-Length: %d - User-Agent: %s\n",
           timestamp,
           client_ip,
           request->method,
           request->path,
           status_code,
           request->content_length,
           request->user_agent[0] ? request->user_agent : "N/A");

    if (request->query_string[0])
    {
        printf("  Query: %s\n", request->query_string);
    }

    fflush(stdout);
}

int http_buf_parse(const char *buf, size_t len, http_request_t *request)
{
    memset(request, 0, sizeof(http_request_t));
    char *buffer_copy = strdup(buf);
    if (!buffer_copy)
        return -1;
    char *saveptr;
    char *line = strtok_r(buffer_copy, "\r\n", &saveptr);

    if (line)
    {
        if (sscanf(line, "%s %s %s", request->method, request->path, request->version) != 3)
        {
            free(buffer_copy);
            return -1;
        }

        // Prepend '.' to path for local file access
        memmove(request->path + 1, request->path, strlen(request->path) + 1);
        request->path[0] = '.';

        // split path and query string
        char *query_pos = strchr(request->path, '?');
        if (query_pos)
        {
            *query_pos = '\0';
            strncpy(request->query_string, query_pos + 1, sizeof(request->query_string) - 1);
        }

        line = strtok_r(NULL, "\r\n", &saveptr);
        while (line && strlen(line) > 0)
        {
            if (strncmp(line, "Host: ", 6) == 0)
                strncpy(request->host, line + 6, sizeof(request->host) - 1);
            else if (strncmp(line, "User-Agent: ", 12) == 0)
                strncpy(request->user_agent, line + 12, sizeof(request->user_agent) - 1);
            else if (strncmp(line, "Accept: ", 8) == 0)
                strncpy(request->accept, line + 8, sizeof(request->accept) - 1);
            else if (strncmp(line, "Content-Type: ", 14) == 0)
                strncpy(request->content_type, line + 14, sizeof(request->content_type) - 1);
            else if (strncmp(line, "Content-Length: ", 16) == 0)
                request->content_length = atoi(line + 16);
            else if (strncmp(line, "Cookie: ", 8) == 0)
                strncpy(request->cookie, line + 8, sizeof(request->cookie) - 1);
            else if (strncmp(line, "Connection: ", 12) == 0)
                strncpy(request->connetion, line + 12, sizeof(request->connetion) - 1);
            line = strtok_r(NULL, "\r\n", &saveptr);
        }

        const char *body_start = strstr(buf, "\r\n\r\n");
        if (body_start && request->content_length > 0)
        {
            body_start += 4; // Skip \r\n\r\n
            size_t body_size = strlen(body_start);
            size_t copy_size = (body_size < sizeof(request->body)) ? body_size : sizeof(request->body) - 1;
            memcpy(request->body, body_start, copy_size);
            request->body[copy_size] = '\0';
        }
    }
    free(buffer_copy);
    return 0;
}

int cgi_service(int socket, http_request_t request)
{
    // Check if CGI script exists before forking
    if (access(request.path, X_OK) != 0)
    {
        return -1;
    }

    int in_pipe[2], out_pipe[2];
    if (pipe(in_pipe) == -1 || pipe(out_pipe) == -1)
    {
        perror("Pipe failed");
        return -1;
    }
    pid_t pid = fork();
    if (pid < 0)
    {
        perror("Fork failed");
        return -1;
    }

    if (pid == 0)
    {
        dup2(in_pipe[0], STDIN_FILENO);
        close(in_pipe[0]);
        close(in_pipe[1]);
        dup2(out_pipe[1], STDOUT_FILENO);
        close(out_pipe[0]);
        close(out_pipe[1]);

        char port_str[16];
        char content_length_str[16];

        snprintf(port_str, sizeof(port_str), "%d", PORT);
        snprintf(content_length_str, sizeof(content_length_str), "%d", request.content_length);

        setenv("GATEWAY_INTERFACE", "CGI/1.1", 1);
        setenv("SERVER_PROTOCOL", "HTTP/1.1", 1);
        setenv("SERVER_PORT", port_str, 1);
        setenv("REDIRECT_STATUS", "200", 1);
        setenv("REQUEST_METHOD", request.method, 1);
        setenv("QUERY_STRING", request.query_string, 1);
        if (strcmp(request.method, "POST") == 0)
        {
            setenv("CONTENT_LENGTH", content_length_str, 1);
            setenv("CONTENT_TYPE", request.content_type, 1);
        }
        execl(request.path, request.path, NULL);
        perror("Exec failed");
        exit(1);
    }
    else
    {
        close(in_pipe[0]);
        close(out_pipe[1]);
        if (strcmp(request.method, "POST") == 0 && request.content_length > 0)
        {
            write(in_pipe[1], request.body, request.content_length);
        }
        close(in_pipe[1]);

        const char *http_header = "HTTP/1.1 200 OK\r\n"
                                  "Server: CGI Server\r\n";
        write(socket, http_header, strlen(http_header));

        char buffer[4096];
        char out_buffer[8192];
        ssize_t bytes_read;

        while ((bytes_read = read(out_pipe[0], buffer, sizeof(buffer) - 1)) > 0)
        {
            char *src = buffer;
            char *dest = out_buffer;
            char *end = buffer + bytes_read;
            while (src < end)
            {
                if (*src == '\n')
                {
                    *dest++ = '\r';
                    *dest++ = '\n';
                }
                else
                {
                    *dest++ = *src;
                }
                src++;
            }
            write(socket, out_buffer, dest - out_buffer);
        }

        close(out_pipe[0]);
        waitpid(pid, NULL, 0);
    }
    return 0;
}

int http_service(int socket, const char *client_ip)
{
    char buffer[4096];
    ssize_t bytes_read = read(socket, buffer, sizeof(buffer) - 1);
    if (bytes_read <= 0)
    {
        return -1;
    }

    http_request_t request;
    if (http_buf_parse(buffer, bytes_read, &request) != 0)
    {
        const char *bad_request = "HTTP/1.1 400 Bad Request\r\nContent-Length: 0\r\n\r\n";
        write(socket, bad_request, strlen(bad_request));
        log_request(client_ip, &request, 400);
        return -1;
    }

    if (strstr(request.path, "/cgi-bin/"))
    {
        if (cgi_service(socket, request) == 0)
        {
            log_request(client_ip, &request, 200);
        }
        else
        {
            const char *not_found = "HTTP/1.1 404 Not Found\r\nContent-Length: 0\r\n\r\n";
            write(socket, not_found, strlen(not_found));
            log_request(client_ip, &request, 404);
        }
    }
    else
    {
        const char *not_found = "HTTP/1.1 404 Not Found\r\nContent-Length: 0\r\n\r\n";
        write(socket, not_found, strlen(not_found));
        log_request(client_ip, &request, 404);
    }
    return 0;
}

int main()
{
    int server_socket, client_socket;
    struct sockaddr_in address;
    socklen_t addrlen = sizeof(address);

    server_socket = socket(AF_INET, SOCK_STREAM, 0);
    if (server_socket == -1)
    {
        perror("Socket creation failed");
        exit(EXIT_FAILURE);
    }

    address.sin_family = AF_INET;
    address.sin_addr.s_addr = INADDR_ANY;
    address.sin_port = htons(PORT);
    if (bind(server_socket, (struct sockaddr *)&address, sizeof(address)) < 0)
    {
        perror("Bind failed");
        close(server_socket);
        exit(EXIT_FAILURE);
    }

    if (listen(server_socket, 3) < 0)
    {
        perror("Listen failed");
        close(server_socket);
        exit(EXIT_FAILURE);
    }
    printf("CGI HTTP Server is listening on port %d\n", PORT);

    while (1)
    {
        struct sockaddr_in client_addr;
        socklen_t client_len = sizeof(client_addr);

        client_socket = accept(server_socket, (struct sockaddr *)&client_addr, &client_len);
        if (client_socket < 0)
        {
            perror("Accept failed");
            continue;
        }

        char client_ip[INET_ADDRSTRLEN];
        inet_ntop(AF_INET, &client_addr.sin_addr, client_ip, INET_ADDRSTRLEN);

        http_service(client_socket, client_ip);

        close(client_socket);
    }

    close(server_socket);
    return 0;
}
```
