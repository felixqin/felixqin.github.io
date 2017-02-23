---
layout: post
category : Server
tagline: "Supporting tagline"
tags : [Linux, Docker, Server, nginx]
---



# Docker 部署 nginx 代理访问宿主机端口



## 环境说明

宿主机RESTful服务绑定在8090端口，nginx运行在docker。

宿主机在docker上的IP为172.18.0.1。

## 配置 nginx

default.conf

```nginx
server {
        listen 80;

        server_name localhost;

        location /api/ {
            proxy_pass  http://172.18.0.1:8090;
        }
}
```

## 启动 docker

```shell
sudo docker run -d --name webapp -p 80:80 -v `pwd`/config:/etc/nginx/conf.d -v `pwd`/logs:/var/log/nginx nginx
```



## 登录docker虚拟机

```shell
sudo docker exec -it webapp /bin/bash
```



## 参考

- [在Docker下部署Nginx](http://blog.shiqichan.com/Deploying-Nginx-with-Docker/)
- [[docker从容器中怎么访问宿主机](http://blog.csdn.net/ownfire/article/details/48006893)]



