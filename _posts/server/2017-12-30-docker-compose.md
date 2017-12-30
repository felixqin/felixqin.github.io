---
layout: post
category : docker
tagline: "Supporting tagline"
tags : [docker, docker-compose, container]
---

# docker-compose 常见问题

## docker-compose 安装失败

运行 docker-compose 出现以下错误：

```
[root@dev ~]# docker-compose
Traceback (most recent call last):
  File "/usr/bin/docker-compose", line 9, in <module>
    load_entry_point('docker-compose==1.9.0', 'console_scripts', 'docker-compose')()
  File "/usr/lib/python2.7/site-packages/pkg_resources/__init__.py", line 570, in load_entry_point
    return get_distribution(dist).load_entry_point(group, name)
  File "/usr/lib/python2.7/site-packages/pkg_resources/__init__.py", line 2751, in load_entry_point
    return ep.load()
  File "/usr/lib/python2.7/site-packages/pkg_resources/__init__.py", line 2405, in load
    return self.resolve()
  File "/usr/lib/python2.7/site-packages/pkg_resources/__init__.py", line 2411, in resolve
    module = __import__(self.module_name, fromlist=['__name__'], level=0)
  File "/usr/lib/python2.7/site-packages/compose/cli/main.py", line 17, in <module>
    from . import errors
  File "/usr/lib/python2.7/site-packages/compose/cli/errors.py", line 10, in <module>
    from docker.errors import APIError
  File "/usr/lib/python2.7/site-packages/docker/__init__.py", line 6, in <module>
    from .client import Client, AutoVersionClient, from_env # flake8: noqa
  File "/usr/lib/python2.7/site-packages/docker/client.py", line 5, in <module>
    import requests
  File "/usr/lib/python2.7/site-packages/requests/__init__.py", line 58, in <module>
    from . import utils
  File "/usr/lib/python2.7/site-packages/requests/utils.py", line 32, in <module>
    from .exceptions import InvalidURL
  File "/usr/lib/python2.7/site-packages/requests/exceptions.py", line 10, in <module>
    from .packages.urllib3.exceptions import HTTPError as BaseHTTPError
  File "/usr/lib/python2.7/site-packages/requests/packages/__init__.py", line 95, in load_module
    raise ImportError("No module named '%s'" % (name,))
ImportError: No module named 'requests.packages.urllib3'
```

重新安装 python-urllib3，失败：
```
[root@dev ~]# yum install python-urllib3
已加载插件：fastestmirror
Loading mirror speeds from cached hostfile
正在解决依赖关系
--> 正在检查事务
---> 软件包 python-urllib3.noarch.0.1.10.2-3.el7 将被 安装
--> 解决依赖关系完成

依赖关系解决

================================================================================================================================================================
 Package                                    架构                               版本                                      源                                大小
================================================================================================================================================================
正在安装:
 python-urllib3                             noarch                             1.10.2-3.el7                              base                             101 k

事务概要
================================================================================================================================================================
安装  1 软件包

总下载量：101 k
安装大小：377 k
Is this ok [y/d/N]: y
Downloading packages:
python-urllib3-1.10.2-3.el7.noarch.rpm                                                                                                   | 101 kB  00:00:00
Running transaction check
Running transaction test
Transaction test succeeded
Running transaction
  正在安装    : python-urllib3-1.10.2-3.el7.noarch                                                                                                          1/1
Error unpacking rpm package python-urllib3-1.10.2-3.el7.noarch
error: unpacking of archive failed on file /usr/lib/python2.7/site-packages/urllib3/packages/ssl_match_hostname: cpio: rename
  验证中      : python-urllib3-1.10.2-3.el7.noarch                                                                                                          1/1

失败:
  python-urllib3.noarch 0:1.10.2-3.el7

完毕！
```

解决方法：先删除 urllib3，再安装 python-urllib3，即可成功。
```
pip uninstall urllib3
yum install python-urllib3
```

