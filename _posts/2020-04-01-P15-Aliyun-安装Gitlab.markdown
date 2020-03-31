---
layout: post
title:  "阿里云服务器学习 - Gitlab安装"
date:   2020-04-01 00:55:00 +0800
categories: posts learn Aliyun Gitlab
header-img: img/post/P7-headimg.jpeg
tags:
    - Gitlab
    - Aliyun

pid: P15
---

## Gitlab使用

### 一、环境准备
#### (一)、安装和打开 http 和 ssh 的权限
<pre class="prettyprint">
sudo yum install -y curl policycoreutils-python openssh-server
sudo systemctl enable sshd
sudo systemctl start sshd

sudo firewall-cmd --permanent --add-service=http
# 可能会报说 FirewallD is not running ,
# 运行防火墙服务
systemctl start firewalld.service

sudo systemctl reload firewalld
</pre>

#### (二)、安装邮件服务 postfix
<pre class="prettyprint">
sudo yum install postfix
sudo systemctl enable postfix
sudo systemctl start postfix
</pre>

### 二、安装
官网地址：https://about.gitlab.com/install/#centos-8
访问外网网速感人，页面半天也没打开，所以决定切换成国内镜像
清华大学的镜像站：https://mirror.tuna.tsinghua.edu.cn/help/gitlab-ce/
#### (一)、新建镜像 repo
新建` /etc/yum.repos.d/gitlab-ce.repo`，内容为:
<pre class="prettyprint">
[gitlab-ce]
name=Gitlab CE Repository
baseurl=https://mirrors.tuna.tsinghua.edu.cn/gitlab-ce/yum/el$releasever/
gpgcheck=0
enabled=1
</pre>

#### (二)、执行命令下载
<pre class="prettyprint">
sudo yum makecache
sudo yum install gitlab-ce
</pre>

#### (三)、配置使用
安装完成之后，可以在`/etc/gitblab/gitlab.rb`中按照需求修改配置，
主要需要修改`external_url`，改成自己使用的 url 地址。
![](/img/post/P15-gitlab1.png)
执行命令配置生效：
<pre class="prettyprint">
# 注意，这个会将配置还原，一般用restart
gitlab-ctl reconfigure
gitlab-ctl restart
</pre>


