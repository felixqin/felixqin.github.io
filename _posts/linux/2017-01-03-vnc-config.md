---
layout: post
category : Linux系统维护
tagline: "Supporting tagline"
tags : [linux, Archlinux, 教程]
---

# Archlinux 配置 VNC 要点

## 桌面启动脚本

xstartup 内需要启动 dbus，否则桌面启动不成功。

~/.vnc/xstartup 文件内容：


```sh

#!/bin/sh

. /etc/profile

export LANG=zh_CN.UTF-8
export XKL_XMODMAP_DISABLE=1

eval `dbus-launch --sh-syntax`

autocutsel -fork

exec startxfce4
#exec startlxqt

```

