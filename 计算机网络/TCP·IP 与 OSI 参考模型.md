---
title: IP 与 OSI 参考模型
header-includes:
 - \usepackage{fvextra}
 - \DefineVerbatimEnvironment{Highlighting}{Verbatim}{breaklines,commandchars=\\\{\}}
output:
  pdf_document:
    latex_engine: xelatex
    toc: true
    template: C:/Huaxv/Huaxv-Tool/markdown-preview=enhanced/template.tex
    highlight: tango
    path: C:/Users/huaxv/Desktop/IP 与 OSI 参考模型.pdf
---

# TCP/IP 与 OSI 参考模型

![Snipaste_2023-12-14_21-12-36](/assets/Snipaste_2023-12-14_21-12-36.png)

## 互联网层

互联网层使用『IP协议』，基于 IP地址 转发包数据。

### IP

IP 不具有重发机制，即使分组数据包未能到达对端主机也不会重发

因此，IP 属于非可靠性传输协议

### ICMP

IP 数据包在发送途中，一旦发生异常导致无法到达对端目标地址时，需要给发送端发送一个『发生异常』的通知

ICMP 就是为这一功能而制定的，有时也会被用来诊断网络的监看状况

### ARP

从分组数据包的 IP地址 中解析出物理地址的一种协议

『IP地址』→ 『MAC地址』

## 传输层

传输层最主要的功能：让应用程序之间实现通信

### TCP

TCP 是一种面向连接的传输层协议，保证两端主机之间的通信可达

能够处理传输过程中丢包、传输顺序错乱等异常情况

还能有效利用带宽，缓解网络拥堵

但是为了建立与断开连接，有时至少需要 $7$ 次的发包收包，导致网络流量的浪费

不利于视频会议等场合的使用

### UDP

UDP 有别于 TCP，它是一种面向无连接的传输层协议

UDP 不会关注对端是否真的收到了传送过去的数据

UDP 常用于分组数据较少或多播、广播通信以及视频通信等多媒体领域

## 应用层


