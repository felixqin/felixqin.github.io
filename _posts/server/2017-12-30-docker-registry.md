---
layout: post
category : docker
tagline: "Supporting tagline"
tags : [docker, container]
---

# docker registry 部署和使用

## 启动

```shell
docker run -d -p 5000:5000 --restart=always --name registry -v /data/registry:/var/lib/registry registry:2
```

## 停止

```shell
docker stop registry && docker rm -v registry
```

## 使用

linux 配置 insecure registry:

```
sudo nano /etc/docker/daemon.json
{"registry-mirrors": ["http://xxx.m.daocloud.io"], "insecure-registries": ["registry.xxx.com:10050"]}
```

windows/macos 配置 insecure registries 如图：
![set insecure registry](http://www.linuxidc.com/upload/2017_03/170304103023911.png)

推送镜像：
```
docker tag joyteam-account registry.joyteam.cc:10050/joyteam-account:stage
docker pull registry.joyteam.cc:10050/joyteam-account:stage
```


## 参考

[使用官方 docker registry 搭建私有镜像仓库及部署 web ui](http://blog.csdn.net/mideagroup/article/details/52052618)



