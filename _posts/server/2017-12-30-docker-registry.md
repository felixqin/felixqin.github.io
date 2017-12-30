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



## 参考

[使用官方 docker registry 搭建私有镜像仓库及部署 web ui](http://blog.csdn.net/mideagroup/article/details/52052618)



