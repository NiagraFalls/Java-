# 学习shell和shell script
## vim程序编辑器
### vi与vim
在Linux系统使用文本编辑器来编辑Linux参数配置文件，是一件很重要的事情。

纯文本文件里面有一般可见字符、换行、制表符等少数格式控制字符。

为什么要学习vi?
很多软件的编辑接口都会主动调用vi(like crontab、visudo、edquota)

所有Linux发行版都会有vi,vim是vi的高级版本比如highlight。vi用于文本编辑、vim用于程序开发
### vi的使用
一、简单执行范例

vi分为三种mode:command mode、insert mode、command-line mode

vi filename进入command mode

按下i进入insert mode

按下esc进入一般模式

进入命令行模式，文件保存并退出vi环境

二、按键说明

三、一个案例练习
练习经常做一做
四、vim的缓存、恢复、与打开时的警告信息

### vim的额外功能
alias命令查看vi和vim是否一致
一、可视区块

二、多文件编辑

三、多窗口功能

四、vim的关键词补全功能

五、vim环境设置与记录：~/.vimrc、~/.viminfo

六、vim常用命令示意图
### 其他vim使用注意事项
## 认识与学习BASH
### 认识BASH这个Shell
我们必须通过shell将输入的命令和kernel沟通，以控制硬件来工作。

Shell程序狭义理解指的是命令行方面的软件，比如bash。广义理解包括GUI软件。

为什么要学习bash?

一、大家都一样。一法通，万法通。
二、远程管理：命令行模式就是比较快
三、Linux的任督二脉：Shell是也。

Shell都有哪些？sh,C shell,K shell,TCSH,bash

查看可用shell:/etc/shells

bash 的功能：history,命令与文件补全功能，alias,shell scripts

通过type来查看命令是否为内置命令。
### Shell的变量功能
OS\Shell的变量功能.md
## 正则表达式与文件格式化处理
## 学习shell脚本