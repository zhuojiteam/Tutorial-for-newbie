#小课堂专题篇3-makefile
##编译时发生了什么
你知道C语言编译时发生了什么吗？

我们可以写一个小程序测试一下，比如最简单的打印`Hello World`，把它取名为`hello.c`。

我们之前让大家安装了GCC并介绍了它的简单使用。

已知的命令例如`gcc -c`能够编译生成目标文件，`gcc -o`则能够输出文件名。

比如我们使用类似`gcc -o hello hello.c`的命令，会把一个文件编译成叫hello的可执行文件；不过注意`-o`参数其实是让gcc输入到指定的文件中，无论是可执行文件、目标文件、汇编文件还是预编译C代码。

实际上，C语言的编译流程具体经历了四个步骤：
- 预处理（Pre-Processing）
- 编译（Compiling）
- 汇编（Assembling）
- 链接（Linking）


我们可以体验一下这个过程。
###编译预处理（Pre-Processing）
先输入这一行命令：gcc -E 目标文件.c
```
gcc -E hello.c
```
回车后我们会被一大堆代码刷屏，把它们用命令`gcc -E hello.c > hello2.c`导入`hello2.c`中，大概有800多行，拉到最后，才会出现`hello.c`的代码片段。

这就是编译预处理，它的主要作用如下：
- 将源文件中以”include”格式包含的文件复制到编译的源文件中；
- 用实际值替换用“#define”定义的字符串（C语言中define的作用类似文本替换）；
- 根据“#if”后面的条件决定需要编译的代码。
###编译（Compiling）
下面用 gcc -S 目标文件.c 来编译，用C的源代码生成汇编语言
```
gcc -S hello.c
```
然后呢你可以打开`hello.s`查看一下里面的内容……

嗯……更加看不懂了……

这就是汇编语言啦。
###汇编（Assembling）
用 gcc -c 目标文件.s　
```
gcc -c hello.s
```
我们会得到`hello.o`的二进制文件，打开它，你就会看到一堆看了要报警的符号，这就是传说中的机器码。
###链接（Linking）
刚刚一直到这个步骤，其实代码都不能执行。最后一步链接，需要在二进制文件`hello.o`的基础上，生成可执行文件（默认是.out文件，也可以自己加上-o参数）
```
gcc hello.o
```
然后你才终于得到了一个可以运行的C程序啦。

## 多文件工程makefile
当然啦，编译hello.c，日常并不会使用到这么多命令，只要`gcc -o hello hello.c`就够了。

但实际应用中，大部分时候我们并不能靠这一条命令来编译出一个可执行文件，因为一个可执行文件可能不是一个文件编译出来的。

比如下面这个程序：
```
#include <stdio.h>
#include <lib.c>
int main()
{
	printf("%d\n", mul(5,7))
}
```
我们用到了一个函数`mul`，但它不在main中，在lib里：

这是lib.c；
```
#include <stdio.h>
int mul(int a, int b)
{
	return a * b;
}
```
这是lib.h。
```
#ifndef LIB

#define LIB

int mul(int a, int b);
#endif 
```

这时候，如果我们直接`gcc -o main main.c`,就会出现类似下面的报错：
```
/tmp/xxxx.o: In function `main':
main.c:(.text+0xf): undefined reference to `mul'
collect2: ld returned 1 exit status
```
这时候，我们就需要先把它们编译成目标文件（object file）：
```
gcc -c main.c -o main.o
gcc -c lib.c -o lib.o
```
然后链接起来：
```
gcc -o main main.o lib.o 
```
实际上gcc这时候发挥的就是ld（链接）的作用，但如果我们使用`ld main.o lib.o -o main`却无法成功链接它们，这是因为gcc还链接了标准库，比如`printf`就在标准库里，如果使用ld，就找不到标准库了。

但这样很烦，尤其是文件多的时候，所以我们可以新建一个`Makefile`文件，内容为：
```
main: main.o lib.o
	cc -o main main.o lib.o
main.o: main.c lib.h
	cc - c main.c
lib.o: lib.c
	cc -c lib.c
```
它们的意思，比如`main: main.o lib.o`，表示`main`依赖`main.o`和`main.c`，而第二行，`cc`表示C compiler，指编译器，在我们这里是gcc（在OS X里其实就是clang）。

