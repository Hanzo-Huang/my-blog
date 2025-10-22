---
title: Windows 从零部署 WordPress 全流程指南
published: 2024-04-26
description: "Windows配置Nginx、PHP并部署WordPress"
image: ""
tags: [Windows]
category: "Web部署"
draft: false
lang: "zh_CN"
---

> 在 Linux 中，借助运维面板和 Docker 可以非常方便地部署 WordPress；但在 Windows Server 上，我尚未发现类似工具，因此尝试使用最原始的方式进行部署，以此记录全过程。

> 本文环境：Windows Server 2022

---

## 准备工作

1. [Microsoft Visual C++ Redistributable Package](https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist?view=msvc-170)（MySQL 依赖环境）
2. [MySQL](https://dev.mysql.com/downloads/installer/)
3. [nginx](https://nginx.org/en/download.html)
4. [php](https://windows.php.net/download/)
5. [WordPress](https://wordpress.org/download/) 或 [WordPress（简体中文）](https://cn.wordpress.org/download/)（本教程以英文版为例）
6. [RunHiddenConsole](https://github.com/wenshui2008/RunHiddenConsole/releases/tag/1.0)

![download.png](https://img.hanzogenji.cn/i/2025/07/09/686e34369ba47.png)

---

## 安装各组件

### Microsoft Visual C++ Redistributable Package

直接运行安装程序并同意许可协议。

![VC++.png](https://img.hanzogenji.cn/i/2025/07/09/686e343ba874d.png)

---

### MySQL

用于 WordPress 的数据库支持。

- 启动安装程序，选择 `Server only`，其余保持默认设置。
- 安装过程中设置 `root` 密码，请务必牢记。

![mysql-1.png](https://img.hanzogenji.cn/i/2025/07/09/686e34379b574.png)
![mysql-2.png](https://img.hanzogenji.cn/i/2025/07/09/686e3438a694a.png)

---

### nginx

作为 Web 服务器，负责响应网页请求。

- 解压至任意位置（如：`C:\server\nginx`）
- 运行 `nginx.exe`，在浏览器访问 [http://127.0.0.1](http://127.0.0.1) 显示成功页面即代表运行正常。

![nginx.png](https://img.hanzogenji.cn/i/2025/07/09/686e343929517.png)

**停止 nginx：**

```bash
cd C:\server\nginx
nginx.exe -s stop
```

---

### php

WordPress 是使用 php 编写的，必须安装。

- 解压至 `C:\server\php`，后续进行配置。

---

### WordPress

- 解压至 `C:\server\wordpress`，即为网站根目录。

---

### RunHiddenConsole

- 解压 `x64` 中的 `RunHiddenConsole.exe` 至 `C:\server`，用于后台静默运行服务。

最终目录结构如下：

![folder.png](https://img.hanzogenji.cn/i/2025/07/09/686e34371e82a.png)

---

## 配置步骤

### 1. 创建数据库

打开 `MySQL 8.0 Command Line Client`，输入密码后执行：

```sql
CREATE DATABASE wordpress;
```

---

### 2. 配置 nginx

编辑 `nginx\conf\nginx.conf`：

#### 修改 `location /`

```nginx
location / {
    root   C:/server/wordpress;
    index  index.html index.htm index.php;
}
```

#### 启用并修改 `location ~ \.php$`

取消注释，修改如下：

```nginx
location ~ \.php$ {
    root           C:/server/wordpress;
    fastcgi_pass   http://127.0.0.1:9000;
    fastcgi_index  index.php;
    fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
    include        fastcgi_params;
}
```

---

### 3. 配置 php

复制 `php.ini-development` 为 `php.ini`，并修改以下内容：

#### 设置扩展目录：

```ini
extension_dir = "C:\server\php\ext"
```

#### 启用 pathinfo 支持：

```ini
cgi.fix_pathinfo=1
```

#### 启用 MySQL 扩展：

在文件末尾添加：

```ini
;mysql extension
extension=php_mysqli.dll
```

---

### 4. 启动 nginx 和 php

在命令行中运行：

```bat
start C:\server\nginx\nginx.exe
C:\server\php\php-cgi.exe -b http://127.0.0.1:9000 -c C:\server\php\php.ini
```

> 注意：第二条命令窗口会停留，不要关闭。

![run nginx and php.png](https://img.hanzogenji.cn/i/2025/07/09/686e343991cb1.png)

---

## 自动化启动脚本

**start.bat**

```bat
@echo off
set PHP_FCGI_MAX_REQUESTS=1000

RunHiddenConsole C:\server\php\php-cgi.exe -b http://127.0.0.1:9000 -c C:\server\php\php.ini
RunHiddenConsole C:\server\nginx\nginx.exe
exit
```

**stop.bat**

```bat
@echo off
taskkill /F /IM nginx.exe > nul
taskkill /F /IM php-cgi.exe > nul
exit
```

---

## 初始化 WordPress

1. 浏览器访问 [http://127.0.0.1](http://127.0.0.1)，点击 `Let’s go`
2. 填写数据库信息：

   - **Database Name**: wordpress
   - **Username**: root
   - **Password**: 安装 MySQL 时设置的密码
   - 其余默认

![wordpress_setup_1.png](https://img.hanzogenji.cn/i/2025/07/09/686e343ae1ce7.png)

3. 点击 `Submit` → `Run the installation`

4. 设置网站信息：

   - Site Title
   - Username / Password（用于登录后台）
   - Email

![wordpress_setup_3.png](https://img.hanzogenji.cn/i/2025/07/09/686e343ca7473.png)

5. 安装成功页面：

![wordpress_setup_4.png](https://img.hanzogenji.cn/i/2025/07/09/686e343c30e15.png)

6. 访问主页：[http://127.0.0.1](http://127.0.0.1)

7. 登录后台：[http://127.0.0.1/wp-admin](http://127.0.0.1/wp-admin)

![wordpress_setup_7.png](https://img.hanzogenji.cn/i/2025/07/09/686e343ed241f.png)

---

## 参考资料

- [Windows 下搭建 nginx+php 开发环境 - 博客园](https://www.cnblogs.com/wwjchina/p/9804576.html)
- [如何更改 WordPress 语言为中文 - CSDN](https://huaweicloud.csdn.net/635665e1d3efff3090b5d33a.html)
