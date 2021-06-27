---
layout: post
title: "新MacBookPro 避坑git hexo主题博客"
date: 2021-6-27 11:16
comments: true
reward: true
tags: 
	- M1_MBP
	- Hexo
	- Git
---
换新电脑笔记本MacBookPro M1 16G内存 512固态
昨天今天来重新部署发布环境，特此记录一下遇到的坑
<!-- more -->
## 一、安装Git、设置邮箱 username ssh连接GitHub
### M1本身已装好Git可以直接开始
```bash
git config --global user.name "yourgithubname"
git config --global user.email "yourgithubemail"
ssh-keygen -t rsa -C "youremail@example.com"
```
### 到GitHub上 settings--ssh keys--new keys 添加私钥

### 生成后填到github和coding上（有coding平台的话）
```bash
ssh -T git@github.com
#(有coding平台的话)
ssh -T git@git.coding.net 
```
## 二、M1安装nodejs
### 修改hosts 才可以安装nvm
```bash
sudo vim /etc/hosts
#按i，添加以下
199.232.68.133 raw.githubusercontent.com
#wq保存退出
```
### 兼容安装nvm
```bash
arch -x86_64 zsh
#然后回车
#终端进入Rosetta 2模式
#安装nvm
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.37.2/install.sh | bash
#使用nvm -v是出错的，提示找不到nvm
#操作：在.nvm中新建一个.bash_profile的文件，将下面这两句话写入文档

#tips: .nvm 和 .bash_profile 是隐藏文件，在终端显示需要输入ls -a。
#然后
cd .nvm
vim .bash_profile

export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh" # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion

source .bash_profile启用文件

nvm install 13

node -v
npm -v
```
## 克隆博客hexo文件
```bash
git clone @git
#进入目录
npm install hexo
npm install -g hexo-cli
npm install
npm install hexo-deployer-git --save

hexo g -d
```
## 每次写文章
```bash
git pull
git add .
git commit -m""
git push origin hexo
hexo g -d
```
## 遇到的问题
### Hexo错误：spawn failed
排查git的ssh连接
git@github.com: Permission denied (publickey).


### hexo | TypeError [ERR_INVALID_ARG_TYPE]
问题原因node版本过高
安装node13版本就冇问题
```bash
nvm install 13
```





