---
title: wsl-ubuntu22.04使用
header-includes:
 - \usepackage{fvextra}
 - \DefineVerbatimEnvironment{Highlighting}{Verbatim}{breaklines,commandchars=\\\{\}}
output:
  pdf_document:
    latex_engine: xelatex
    toc: true
    template: C:/Huaxv/Huaxv-Tool/markdown-preview=enhanced/template.tex
    highlight: tango
    path: C:/Users/huaxv/Desktop/wsl-ubuntu22.04使用.pdf
---

# wsl-ubuntu22.04使用

## 添加用户

```bash
# 进入管理员模式
sudo su

# 创建新用户，会提示你输入密码、手机号等
adduser lrq

# 设置新用户权限，添加 sudo 权限
usermod -aG sudo lrq

# 为新用户创建一个 home 目录
mkhomedir_helper lrq

# 切换新用户
su - lrq

# 删除用户
deluser lrq
```

## 换源

```bash
sudo gedit /etc/apt/sources.list


```
