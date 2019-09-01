---
layout: post
title: "填坑，宝塔、laravel、wordpress部署云端"
date: 2019-8-31 8:55
comments: true
reward: true
tags: 
	- 云端部署
	- laravel 
---
感谢游神的指点，让我可以快一点下班，开心~

##注意事项

1.大小写问题。本地laragon服务路径大小写不敏感，一到云端Linux，开始斤斤计较了，折腾啊。

2.wordpress对应的数据库端口号、数据库名（大小写）、账号密码、字符集这些。

3.宝塔面板LNMP，伪静态文件生成laravel 5的；入口目录是/public。

4.laravel路由没有生效，主要问题在于：PHP版本7以上、storage目录权限777、key问题解除putenv()函数限制。

key的命令需要在项目的根目录下，php artisan key:generate
