---
layout:     post
title:      下载jekyll静态博客模板并上传至github
author:     葱葱
tags: 		jekyll github
subtitle:   To learn how to use a jekyll blog model and push it on the github.
category:  project1

---
### 1.下载一个jekyll静态模板解压；
### 2.创建一个本地的jekyll文件夹（jekyll_demo）；
### 3.在终端输入命令进入该文件夹；
```python
cd jekyll_demo
```
### 4.初始化git；
```python
 git init
```
### 5.创建根节点gh-pages；
```python
git checkout --orphan gh-pages
```
### 6.将已下载的模板的全部内容复制进根目录（jekyll_demo）下；
### 7.修改_config.yml文件内容；
>* 要修改的具体内容：<br/>
(此处仅为上传至github使其可以访问的必要部分，其它部分可在使用过程中自定义修改)
    * 将url改为要访问的网址
    * baseurl改为根目录
    * 修改文件中的绝对路径
    * 修改siteurl

### 8.把内容添加到本地git库；
```python
git add .
git commit -m "first post"
```
### 9.在github上新建一个仓库（这里起名为jekyll_demo）；
### 10.将本地内容推送至github仓库；
```python
    //将username替换为自己的github用户名

　　$ git remote add origin https://github.com/username/jekyll_demo.git
　　$ git push origin gh-pages
```
### 11.访问http://username.github.com/jekyll_demo/即可。（将username替换为自己的github用户名）。
