---
layout: post
category : WEB前端
tagline: "Supporting tagline"
tags : [WEB, jekyll, 教程]
---
{% include JB/setup %}


# 安装命令

## 安装

```
sudo pacman -S ruby
gem install jekyll
gem install bundler
gem install jekyll-sitemap
gem install pygments.rb
```

## 配置
~/.bashrc PATH 加入 `$(ruby -e 'print Gem.user_dir')/bin`

## 运行
```
jekyll --version
jekyll serve --host=0.0.0.0
```

## 管理

- 安装主题

```
rake theme:install git="https://github.com/jekyllbootstrap/theme-twitter.git"
```

- 切换主题

```
rake theme:switch name="bootstrap-3"
```


# 参考链接

- [ArchLinux 安装 ruby](https://wiki.archlinux.org/index.php/Ruby#RubyGems)
- [jekyll 官方文档](http://jekyllbootstrap.com/usage/jekyll-quick-start.html)
- [如何让jekyll服务可以在局域网中访问](http://www.jianshu.com/p/650b96306013)
- [Jekyll 的安装](https://havee.me/internet/2013-07/jekyll-install.html)
- [Windows上安装Jekyll](http://blog.csdn.net/itmyhome1990/article/details/41982625)
