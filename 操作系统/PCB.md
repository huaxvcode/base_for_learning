---
title: PCB
header-includes:
 - \usepackage{fvextra}
 - \DefineVerbatimEnvironment{Highlighting}{Verbatim}{breaklines,commandchars=\\\{\}}
output:
  pdf_document:
    latex_engine: xelatex
    toc: true
    template: C:/Huaxv/Huaxv-Tool/markdown-preview=enhanced/template.tex
    highlight: tango
    path: C:/Users/huaxv/Desktop/PCB.pdf
---

# PCB

进程的PCB是指进程控制块（Process Control Block），

它是操作系统用来**描述和控制进程的数据结构**，

是进程存在的唯一标志。

进程的PCB包含了进程的各种信息，例如：

- 进程标识符（PID）：用来唯一地区分不同的进程。
- 进程状态：用来表示进程当前所处的状态，如就绪、执行、阻塞等。
- 进程优先级：用来表示进程的重要性，影响进程的调度顺序。
- 程序计数器（PC）：用来记录进程下一条要执行的指令的地址。
- 程序状态字（PSW）：用来记录进程的运行状态，如标志位、中断屏蔽等。
- CPU寄存器：用来保存进程的运行结果，如累加器、索引寄存器、通用寄存器等。
- 进程地址空间：用来存放进程的正文段、数据段和堆栈段等。
- 进程资源：用来记录进程所占用或请求的各种资源，如内存、文件、设备等。
- 进程链接：用来将具有相同特征的进程链接在一起，如就绪队列、阻塞队列等。
  
进程的PCB是操作系统管理进程的重要依据，它在进程的创建、运行、切换、撤销等过程中起着关键的作用。
