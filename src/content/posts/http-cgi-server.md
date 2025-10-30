---
title: [C] CGI Server
published: 2025-10-30
description: "使用C语言学习网络编程并编写CGI Server"
image: ""
tags: []
category: "program"
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

int main(void)
{
    char *pQuery = NULL;
    char *pMethod = NULL;

    pMethod = getenv("REQUEST_METHOD");

    printf("Content-Type: text/html\n\n");
    printf("<html><body>");
    printf("<h1>CGI Login Test</h1>");

    if (!strcmp(pMethod, "POST"))
    {
        int len = atoi(getenv("CONTENT_LENGTH"));
        char *data = (char *)malloc(len + 1);
        fgets(data, len + 1, stdin);
        data[len] = '\0';
        if (strcmp(data, "username=admin&password=123456") == 0)
        {
            printf("<p>Login successful!</p>");
        }
        else
        {
            printf("<p>Invalid username or password</p>");
        }
    }
    else
    {
        printf("<p>Use POST.</p>");
    }

    printf("</body></html>\n");

    return 0;
}
```

