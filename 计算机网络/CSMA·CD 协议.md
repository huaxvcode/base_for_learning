---
title: CSMA·CD 协议
header-includes:
 - \usepackage{fvextra}
 - \DefineVerbatimEnvironment{Highlighting}{Verbatim}{breaklines,commandchars=\\\{\}}
output:
  pdf_document:
    latex_engine: xelatex
    toc: true
    template: C:/Huaxv/Huaxv-Tool/markdown-preview=enhanced/template.tex
    highlight: tango
    path: C:/Users/huaxv/Desktop/CSMA·CD 协议.pdf
---

# CSMA·CD 协议

![Snipaste_2023-12-15_22-58-28](/assets/Snipaste_2023-12-15_22-58-28_so5hjpf60.png)

单一共享网络传输信道

多个站公用一个网络信道上，如果多个站同时发送数据，可能因信号传播延迟而发生碰撞

CSMA/CD 协议，也称为带冲突检测的载波侦听多路访问技术

它协调哪些计算机可以访问共享的介质（网络信道）

- 首先检测目前网络上正在发送的信号
  - 如果空闲，就发送自己的帧
  - 否则就一直监听

- 如果其他站碰巧同时发送，则发生重叠的电信号被检测为一次碰撞
  - 每个站都等待一个随机时间，然后再次尝试发送

最终每个站都会得到机会发送，或者在尝试了一定次数后超时

采用 CSMA/CD 协议，在任何给定的时间内，**网络中只能有一个帧传输**

像 CSMA/CD 协议这样的访问方式，更确切的名称为：介质访问控制（MAC）协议

CSMA/CD 协议是基于竞争的 MAC 协议

交换机的出现，CSMA/CD 协议逐渐变得不流行

---

CSMA/CD 意思是：载波监听多点接入技术

载波监听就是不管在想要发送数据之前，还是在发送数据之中，每个站都必须不停地检测信道

在发送前检测信道，就是为了避免冲突

在发送中检测信道，就是为了及时发现如果有其他站也在发送就立即终止本质的发送

一个站不可能同时发送和接收信息，但必须是同时发送同时监听信道

因此，使用 CSMA/CD 协议的以太网不可能进行全双工通信，而只能进行双向交替通信（半双工通信）
