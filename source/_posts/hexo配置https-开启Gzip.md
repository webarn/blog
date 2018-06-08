---
title: hexo配置https && 开启Gzip
date: 2018-06-08 15:01:46
tags: 
  - https
  - Gzip
categories:
  - 服务器
---

#### 开启 https:

1.  阿里云有 1 年免费的 https 申请活动,域名页面点击 ssh 证书开通
2.  填写相关资料等待审核通过下载文件,解压后得到两个文件
3.  通过 `scp /本地路径 服务器用户名@服务器ip地址 :/服务器地址` 上传文件 (注意权限)
    <!-- more -->
4.  在 Nginx 的安装目录下创建 cert 目录，并且将下载的全部文件拷贝到 cert 目录中。如果申请证书时是自己创建的 CSR 文件，请将对应的私钥文件放到 cert 目录下并且命名为 xxxxxx.key；
5.  打开 Nginx 安装目录下 conf 目录中的 nginx.conf 文件
6.  复制

```nginx
server {
  listen 443;
  server_name localhost;
  ssl on;
  ssl_certificate   cert/xxxxxx.pem;
  ssl_certificate_key  cert/xxxxxxxx.key;
  ssl_session_timeout 5m;
  ssl_ciphers ECDHE-RSA-AES128-GCM-SHA256:ECDHE:ECDH:AES:HIGH:!NULL:!aNULL:!MD5:!ADH:!RC4;
  ssl_protocols TLSv1 TLSv1.1 TLSv1.2;
  ssl_prefer_server_ciphers on;
  location / {
      root html;  #注意路径
      index index.html index.htm;
  }
}
```

7.  如果 http 强制转 https 则在 80 端口配置添加

```nginx
return 301 https://$server_name$request_uri;
```

8.  nginx -t 测试通过后重启

#### 开启 Gzip:

nginx 文件  添加

```nginx
gzip on;
gzip_proxied any;
gzip_min_length 1100;
gzip_buffers 16 8k;
gzip_types text/plain text/css application/javascript application/x-javascript text/xml application/xml application/xml+rss text/javascript;
```
