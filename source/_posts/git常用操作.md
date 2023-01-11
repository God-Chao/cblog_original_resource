---
title: git常用操作
category: 笔记
tags:
  - git
banner_img: /img/banner/git.jpg
index_img: /img/cover/git.jpg
excerpt: 常用git指令以及操作
date: 2023-01-01 16:52:06
---

## 创建仓库

```bash
# 第一种方式
# 克隆远程仓库代码到该目录下，并设置为默认分支
git clone git@github.com:用户名/仓库名.git

# 第二种方式
# git初始化，在当前目录下生成一个.git目录
git init
# 添加远程仓库
git remote add 远程仓库简称 git@github.com:用户名/仓库名.git
# 查看远程仓库列表（有v的输出包含url）
git remote (-v)
```

## 提交与推送代码
```bash
# 将所有文件放入缓存区中等待被提交（支持通配符表达式）
git add *

# 提交上面放入缓存区中的所有文件，提交信息linux下为单引号，windows下为双引号
git commit -m "提交信息"

# 将提交的所有文件推送到远程仓库上去
git push
```

## 分支管理
```bash
# 查看所有的分支，结果列表中带*号的为当前分支
git branch

# 添加分支
git branch 新分支名称

# 切换分支，切换成功后代码会自动更新为目标分支的代码
git checkout 目标分支

# 合并目标分支的代码到当前分支（可能产生合并冲突）
git merge 目标分支

# 查看源分支与目标分支的差异，一般用于合并代码之前
git diff 源分支 目标分支
```

## 本地分支与远程分支映射
```bash
# 使用git在本地新建一个分支后，需要做远程分支关联。如果没有关联，git会在下面的操作中提示你显示的添加关联。关联目的是在执行git pull, git push操作时就不需要指定对应的远程分支，你只要没有显示指定，git pull的时候，就会提示你。

# 查看本地分支与远程分支的映射关系
git branch -v
```

## 上传到Gitee
```bash
# 在Gitee中创建好仓库

# 进入文件夹，初始化git
$ git init

# 添加远程仓库
$ git remote add origin https://gitee.com/Chao_j/仓库名称.git

# 提交代码
$ git add *

$ git commit -m "提交信息"

# 推送代码
$ git push --set-upstream origin master
```

## 上传到Github
```bash
# 在Github中创建好仓库

# 进入文件夹，初始化git
$ git init

# 添加远程仓库
$ git remote add origin git@github.com:God-Chao/仓库名称.git

# 提交代码
$ git add *

$ git commit -m "提交信息"

# 推送代码
$ git push --set-upstream origin master
```