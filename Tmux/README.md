# tmux
**tmux** 是一个终端复用软件，通过一个终端登录远程主机并运行tmux后，在其中可以开启多个窗口而无需再“浪费”多余的终端来连接这台远程主机，并且可以在远程服务器上持久地保存工作状态。

## tmux的最大好处

> 不怕断网，迅速恢复工作环境。

* 公司开了一堆窗口，下班了到家后灵感突发，想要继续`coding`，登陆`VPN`，`SSH`连上后又要重新打开各种窗口！！！这个时候你就可以装个`tmux`。同一组工作环境，在多处共享。
* 公司服务器上调试程序，开了一堆窗口。出去吃了个饭，发现`SSH`超时了，`attach`就能找回原来打开的那些窗口。

## tmux基本概念
> tmux的主要元素分为三层

* `Session` 一组窗口的集合，通常用来概括同一个任务。`session`可以有自己的名字便于任务之间的切换。
* `Window` 单个可见窗口。`Windows`有自己的编号，也可以认为和`ITerm2`中的`Tab`类似。
* `Pane` 窗格，被划分成小块的窗口，类似于`Vim`中 `C-w +v` 后的效果。

![tmux.png](../statics/tmux.png?raw=true)


### Install

#### homebrew安装

    $ brew install tmux
   
### 运行截图
![tmux.jpg](../statics/tmux.jpg?raw=true)
