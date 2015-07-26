#小课堂番外篇4-GCC的安装与使用
把源代码翻译成计算机能够运行的程序，需要编译器。

GCC是C的一套编译器，后来变得可处理C++。之后也变得可处理Pascal、Objective-C、Java等等。

而Clang则是一个C、C++、Objective-C和Objective-C++编程语言的编译器前端。它采用了底层虚拟机（LLVM）作为其后端。它的目标是提供一个GNU编译器套装（GCC）的替代品。

LLVM是一种编译器的基础建设。它是为了任意一种编程语言写成的程序，利用虚拟技术，创造出编译时期，链结时期，运行时期以及“闲置时期”的最优化。它最早是以C/C++为实现对象，目前则还支持了诸多其他语言，包括Haskell、Java bytecode、Python、Ruby、Rust、Scala、C#等等。

既然大家都要学C，我们可以安装一下`GCC`/`Clang`。

实测windows的`Clang`会有一些奇怪的问题，所以我们先用`GCC`。

首先你应该已经安装了包管理器，如果没有安装，请看番外1。

##一份GCC的学习教程
这个教程比较清楚地介绍了GCC的基本用法，可以参考：[GCC五分钟系列](https://github.com/lexdene/gcc_five_minute)

##Windows
###安装
打开cmd/powershell，使用
```
choco install mingw
```

如果碰到问题可以重新来一遍看看，mingw应该没有被墙。
安装完毕以后，输入命令`gcc -v`或者`gcc --help`可以看到版本信息和简单的使用说明。
###使用
然后我们可以去Sublime里写一个简单的C程序，如下，它的意思是打印字符串`Hello World!`：
```
#include <stdio.h>
int main()
{
	printf("Hello World!\n");

	return 0;
}
```
然后把它保存到桌面（Desktop），命名为`hello.c`；

接着我们打开cmd/powershell，然后你默认在`C:\Users\你的用户名`这个目录（也就是你的home）里，我们使用：
```
cd Desktop
```
就进入到桌面（Desktop）目录（cd命令是什么？自己查哦），然后我们：
```
gcc -o hello.exe hello.c
```
上面这两步，也可以用一句命令替代：
```
gcc -o Desktop\hello.exe Desktop\hello.c
```
（其实这个文件随便放在哪个目录都可以，但因为你的默认位置一开始在`C:\Users\你的用户名`，所以你至少要让gcc找到你的文件在哪。）

这样，在你的Desktop目录下就会出现一个`hello.exe`的可执行文件，我们在命令行里运行它：
```
.\hello.exe
```
窗口中就会出现`Hello World!`啦。



##OS X/Linux
###安装
可以先在终端运行一下命令诸如`gcc -v`or`gcc --help`看看有没有反应，如有且无报错，则gcc已安装。

若显示找不到此命令，则终端运行相应的安装包命令，一般软件包是叫gcc，也可以自己查找一下。

类似（Ubuntu，如果提示需要权限，就在前面加`sudo`）：
```
apt-get install gcc
```
（OS X）
```
brew install gcc
```
###使用
接下来的操作可以参考上面windows的方法，当然你可能没有桌面（Desktop）文件夹，总之放在哪里都可以，或者在程序所在的目录下运行`gcc`，或者让`gcc`找到这个程序，就可以了。

终端terminal的默认目录也是在home里，就是`～`。

需要注意的是在*nix（Linux/Unix，OS X是Unix）系统下，我们不需要把这个程序编译成exe文件，直接编译成`hello`就可以了。

另外，执行它的命令也稍有差别：
```
./hello
```
