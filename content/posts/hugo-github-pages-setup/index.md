+++
date = '2026-05-22'
draft = false
title = 'GitHub Pages + Hugo 搭建个人技术博客'
categories =  ["运维"]
tags =  ["Hugo", "GitHub", "博客搭建"]
summary = "从零开始，使用 Hugo 生成静态网站并部署到 GitHub Pages，实现 git push 自动发布。"
+++

## 前言

探索使用GitHub Pages 结合 Hugo 搭建博客环境。

对比博客园/CSDN

1. 主要是不想在博客园或CSDN 上折腾，毕竟现在都是AI 时代，博客看的人已经很少了; 
2. 和个人github 分离，两边关联需要人为在博客中注明；

对比自己开发

1. 要花费时间开发相应功能，当前没必要
2. 开发出来的服务需要服务器运行，再折腾服务器当前也没必要

GitHub Pages

1. 直接使用个人github 账号
2. 提交代码自动部署
3. 免费，快速上手

[Hugo](https://github.com/gohugoio/hugo)

​	基于Go 语言开发的高性能、现代静态网站生成器。github 88K start。 使用markdown 写内容，自动生成相应的主题页面。

## 环境准备

1. Git 
2. GitHub
3. Hugo

## 整体流程

从Hugo 文档中看大体流程，[host on GitHub Pages](https://gohugo.io/host-and-deploy/host-on-github-pages/)

因为只是从hugo 文档上看有可能找不到相关的功能在哪里，还是建议github 的文档 + hugo 的文档结合一起看，我把自己操作的大体步骤总结如下，可以给部分参考。



### GitHub 配置

[官方文档](https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-github-pages-site) 

1. 在github 中创建一个仓库，仓库必须为public 类型，如果不是public ，后续步骤配置部署时将看不到相关功能。
2. 仓库的名称必须为： \<user\>.github.io 或\<organization\>.github.io
3. 选择如何部署网站: [官方文档](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site) 
4. 按文档中照片操作即可，setting->pages->build and deployment->branch ，选择main 分支，点击save即可
5. 再次点击build and deployment-> 选择 GitHub Actions

### 本地git 仓库

1. 提前安装好git 
2. 选择一个目录

### Hugo 

1. 提前安装好hugo,[下载地址](https://github.com/gohugoio/hugo/releases)
2. 查看[快速启动文档](https://gohugo.io/getting-started/quick-start/)

```shell
# 这里最好要在上一步git 仓库中选择的目录,两边的步骤能对应上
# 创建新网站
hugo new project quickstart # 注意这里的项目名称要和Github 上的项目名称一致
cd quickstart
# 仓库初始化
git init
# 添加网站主题
git submodule add https://github.com/adityatelange/hugo-PaperMod themes/papermod
```

3. 执行 host on github pages 第二步，修改hugo.toml ,使用主题，以及修改缓存

```toml
# 这个最好是github pages 的网站名称一致
baseURL = 'https://tomato-ho.github.io/' 
locale = 'zh-cn'
title = 'Person Porfile'
theme = 'papermod'

[caches]
[caches.images]
dir = ':cacheDir/images'
```

4. github pages 网站地址: setting->pages 页面第一行即可看到
5. 在项目目录中创建github actions 相关配置，执行 host on github pages 第三步、第四步，配置过长，本文 不记录，直接复制粘贴即可
6. 将本地仓库与远程仓库关联

```shell 
git remote add origin xxx # 这里最好是使用SSH 方式
git fetch origin/main # 拉取远程仓库最新提交
git merge origin/main --allow-unrelated-histories # 合并远程仓库到本地
```

7. 回到hugo 的快速启动文档,添加新的页面后，提交git 并推送到远程即可看到github actions 有执行新的任务，任务通过后，刷新网站即可完成页面更新

## 后续

1. 添加新的网站内容。
2. 提交git, 推送到github 即可完成网站更新。
