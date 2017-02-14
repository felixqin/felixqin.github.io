---
layout: post
category : Server
tagline: "Supporting tagline"
tags : [Linux, Docker, Server]
---


# Windows Docker 安装与使用

## 下载

国内网络环境直接下载官网安装包，非常慢，推荐从 [DaoCloud](https://www.daocloud.io/) 下载。

[WindowsDocker on DaoCloud](https://dn-dao-github-mirror.qbox.me/docker/install/windows/InstallDocker.msi)

[DockerToolbox on DaoCloud](https://dn-dao-github-mirror.daocloud.io/docker/toolbox/releases/download/v1.13.0/DockerToolbox-1.13.0.exe)



## 加速

同样，直接访问Docker Hub 下载镜像也是非常慢，需要从 DaoCloud 加速。

登录 DaoCloud，进入加速页面，按照提示配置好 Windows Docker。



## 运行



```
  PS C:\Users\jdoe> docker --version
  Docker version 1.12.0, build 8eab29e, experimental

  PS C:\Users\jdoe> docker-compose --version
  docker-compose version 1.8.0, build d988a55

  PS C:\Users\jdoe> docker-machine --version
  docker-machine version 0.8.0, build b85aac1
```



```
PS C:\Users\jdoe> docker ps

CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
```



```
PS C:\Users\jdoe> docker version
Client:
Version:      1.13.0-rc3
API version:  1.25
Go version:   go1.7.3
Git commit:   4d92237
Built:        Tue Dec  6 01:15:44 2016
OS/Arch:      windows/amd64

Server:
Version:      1.13.0-rc3
API version:  1.25 (minimum version 1.12)
Go version:   go1.7.3
Git commit:   4d92237
Built:        Tue Dec  6 01:15:44 2016
OS/Arch:      linux/amd64
Experimental: true
```



```
PS C:\Users\jdoe> docker info
Containers: 0
Running: 0
Paused: 0
Stopped: 0
Images: 0
Server Version: 1.13.0-rc3
Storage Driver: overlay2
  Backing Filesystem: extfs
  Supports d_type: true
  Native Overlay Diff: true
Logging Driver: json-file
Cgroup Driver: cgroupfs
Plugins:
  Volume: local
  Network: bridge host macvlan null overlay
Swarm: inactive
Runtimes: runc
Default Runtime: runc
Init Binary: docker-init
containerd version: 03e5862ec0d8d3b3f750e19fca3ee367e13c090e
runc version: 51371867a01c467f08af739783b8beafc154c4d7
init version: 949e6fa
Security Options:
  seccomp
    Profile: default
Kernel Version: 4.8.12-moby
Operating System: Alpine Linux v3.4
OSType: linux
Architecture: x86_64
CPUs: 2
Total Memory: 1.934 GiB
Name: moby
ID: EODE:VBXI:Y4EL:JXRJ:STRS:HCAI:LDLF:P4KW:B5XU:QPNE:LKTM:RG32
Docker Root Dir: /var/lib/docker
Debug Mode (client): false
Debug Mode (server): true
  File Descriptors: 13
  Goroutines: 21
  System Time: 2016-12-07T19:02:41.3287973Z
  EventsListeners: 0
Registry: https://index.docker.io/v1/
Experimental: true
Insecure Registries:
  127.0.0.0/8
Live Restore Enabled: false
```



```
PS C:\Users\jdoe> docker run hello-world

Hello from Docker.
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
1. The Docker client contacted the Docker daemon.
2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
3. The Docker daemon created a new container from that image which runs the executable that produces the output you are currently reading.
4. The Docker daemon streamed that output to the Docker client, which sent it to your terminal.
```



```
PS C:\Users\jdoe> docker run -it ubuntu bash

Unable to find image 'ubuntu:latest' locally
latest: Pulling from library/ubuntu
5a132a7e7af1: Pull complete
fd2731e4c50c: Pull complete
28a2f68d1120: Pull complete
a3ed95caeb02: Pull complete
Digest: sha256:4e85ebe01d056b43955250bbac22bdb8734271122e3c78d21e55ee235fc6802d
Status: Downloaded newer image for ubuntu:latest
```





