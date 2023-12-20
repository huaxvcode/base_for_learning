---
title: P、V操作
header-includes:
 - \usepackage{fvextra}
 - \DefineVerbatimEnvironment{Highlighting}{Verbatim}{breaklines,commandchars=\\\{\}}
output:
  pdf_document:
    latex_engine: xelatex
    toc: true
    template: C:/Huaxv/Huaxv-Tool/markdown-preview=enhanced/template.tex
    highlight: tango
    path: C:/Users/huaxv/Desktop/P、V操作.pdf
---

# P、V操作

P、V操作是一种用于实现进程同步和互斥的机制，

它由两个不可中断的原语组成，分别是P操作和V操作。

P操作和V操作都是对信号量进行操作，

信号量是一种表示资源数量或状态的整数变量。

P操作是请求资源，如果资源不足，就让进程等待；

V操作是释放资源，如果有等待的进程，就唤醒一个。

P、V操作必须成对出现，且不能嵌套使用。
