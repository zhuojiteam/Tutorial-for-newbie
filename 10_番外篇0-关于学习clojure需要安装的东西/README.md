#小课堂番外篇0-关于学习clojure需要安装的东西
关于clojure是个啥，请阅读总结（一）。

装完这些东西不要问我去哪里打开，要怎么打开……它们装起来像个软件，但不是像普通软件那么用的，目的是给你们一个clojure的开发环境。以后其他的语言，开发环境的配置也是大同小异。（所以即使最后你学不会clojure，至少你了解了这个过程……）

另外如果不是通过包管理器下载东西的话，用迅雷吧^ ^，新建任务把下载链接丢进去就好，速度会快很多。

（为什么会快呢？大家不妨思考一下；另外，也可以查一查**HTTP、HTTPS、SSH**这些词的意思。）

另外，本群不提供特殊情况（特别麻烦的）以外的软件包下载，因为不会有人永远帮你准备好这些东西哒，授人以渔的故事大家明白吧^ ^这也是很多关键词窝不解释而让各位自己查的原因。也许现在你检索信息的能力尚不完备，但，总可以学会。窝才不要把饭喂到你们嘴边呢，哼。（窝已经整理得要吐血了……卒）

这篇总结里窝会帮大家翻译英文……目的是教大家怎么读取页面上的关键信息，以后就要各位自求多福啦。
再提醒一次，勤查粗体字，百度以外，还可以使用[必应](http://cn.bing.com/)。当然你会翻墙，能谷歌就更好啦。

关于翻墙和接下来会频繁提到的**包管理器**，我们下期再见^ ^

##1 JDK
###1.1 for windows ：
请参见总结（二）的JDK的安装与配置部分
###1.2 for Linux/OS X：
####1.2.1途径一：
如果你有包管理器，一般可以直接用**包管理器**下载。不同的系统有它们各自的包管理器。
####1.2.2途径二：
去[官网](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)下载，点击选择  Accept License Agreement  ，选择你的系统对应的版本链接进行下载，然后安装即可。
###1.3检验JAVA是否安装成功：
1. 打开cmd，一般是快捷键win+R，然后在出来的小窗口中键入cmd，回车，就会出现命令行界面；
2. 依次输入`java`回车，`javac`回车，`java -version`回车，然后会返回类似下图，没有报错并且有反应，则安装成功。
![Alt text](./image.gif)
			
##2 Clojure
去群文件下载clojure然后解压到一个目录（windows最好是C盘），找到clojure1-7.0.jar的路径并记住这个路径； 
###2.1 for windows
打开cmd，输入java -cp "clojure-1.7.0.jar的路径" clojure.main回车，就可以运行Clojure。
###2.2 for Linux/OS X
打开你的终端/terminal，输入java -cp "clojure-1.7.0.jar的路径" clojure.main回车，就可以运行Clojure。
- 不知道终端是什么，请自己去查。
- Mac用户打开你的spotlight，查找terminal.app或终端.app
###2.3要点
注意，路径是clojure-1.7.0-jar的路径。如果你的系统没有显示文件扩展名，请去文件夹属性里设置显示扩展名。

关于如何显示文件扩展名，不会的请自己搜索。

回车以后若没有报错，会出现类似下面的文字：
```
Picked up JAVA_TOOL_OPTIONS: -javaagent:/usr/share/java/jayatanaag.jar 
Clojure 1.7.0
user=> 
```
则成功（不需要每个字都一样0.0，类似，类似，具体会因为你自己的设置有所区别）
##3 leiningen
Leiningen是一个用于自动化（构建）clojure项目的工具，安装了它以后，我们就可以在编辑器里写clojure代码，而不是在命令行中逐条解释。怎么使用它，我们以后会说。
###3.1 如果你有包管理器（OS X的homebrew，Windows的Chocolatey）
直接使用命令行下载，先打开你的终端terminal（OS X，如何开看本文档2.2 部分）/powershell（powershell是windows7及以后才有的功能哦，打开方式应该和cmd类似，或者去cmd里输入powershell回车）；
- for OS X homebrew：`brew install leiningen`
- for Windows chocolatey：`choco install lein`or`cinst lein`

没翻墙的话有一定几率碰到下不了的问题。

如果安装成功。请输入继续输入`lein -v`查看leiningen的版本，若版本在2.X以下（X只是一个未知数），哇，那你可能要去手动安装了……

然后你可以卸载一下：
- for homebrew：`brew uninstall leiningen`
- for chocolatey：`chocolatey uninstall lein`or` cuninst lein`

Linux的命令就是对应的包管理器的命令，不提。
###3.2 手动安装方法（没有包管理器或者包管理器安装失败/版本过低）
首先，请大家来到leiningen的Github项目地址：https://github.com/technomancy/leiningen
####3.2.1 for LINUX/OS X
下拉，然后我们在`Installation`模块阅读到这样的说明：

前面那一堆话就是我在本文档3.1里让大家干的……可以不管。
- Make sure you have a Java JDK version 6 or later.
- Download the lein script from the stable branch of this project.
- Place it on your $PATH. (~/bin is a good choice if it is on your path.)
- Set it to be executable. (chmod 755 ~/bin/lein)
- Run it.

它们是啥意思呢，让我来翻译一下0.0
- 首先，确认你装了jdk吗：如果你按照窝的这个番外篇走到了这里，那你应该是装好了，跳过；
- 第一步：下载
	- 下载它给的那个[链接](https://raw.githubusercontent.com/technomancy/leiningen/stable/bin/lein)，保存的名字叫lein.这是一个脚本。
- 第二步：放到你的PATH里
	- 首先我们来看一下**PATH**（它是啥，可以自己查，窝以后也会补充）
	- 输入命令（不会再要我提醒你去哪里输入命令了吧）`echo $PATH`，系统会告诉你哪里是你的PATH；
	- 比如在我的系统里，它告诉我的PATH是这样的：
	`/usr/local/bin:/usr/bin:/bin:/usr/local/games:/usr/games:/sbin:/usr/sbin`
	- 我的系统用冒号分隔了不同的PATH，也有可能是分号分隔的，总之你把lein挪到随便哪个PATH下就好；
	- 怎么移动呢？输入命令`mv lein 目标PATH/lein`，它可能告诉你没有权限，那你就在前面加`sudo`然后空格：
	- 比如我是这样做的`sudo mv lein /usr/bin/lein`，然后它可能让你输入password也就是密码，你输入你的密码就好（就是你的账户密码啦），注意为了保密，密码不会在屏幕上出现，你输好回车就可以了。
- 第三步：我们要让它变成一个可执行文件
	- 输入命令`chmod +x 目标PATH/lein`or`chmod 755 目标PATH/lein`
- 第四步：让我们运行这个脚本
	- 输入命令`./目标PATH/lein`
	- 然后就开始下载安装leiningen啦，是在线安装，注意保持网络的畅通；
	- 安装成功以后，会出现类似下面的文字（后面还有一堆说明就不贴了），你就成功啦：
```
Picked up JAVA_TOOL_OPTIONS: -javaagent:/usr/share/java/jayatanaag.jar 
Leiningen is a tool for working with Clojure projects.
```
####3.2.2 for Windows
有两种方法
#####安装包安装
我们下拉页面到`Windows`模块，它给了你一个installer也就是安装包的[链接](http://leiningen-win-installer.djpowell.net/)。

然后呢在这个页面里的`Installation`模块，它给了两个链接，一个是JDK的，一个是leiningen的，JDK我们已经装了，不管，点击下面那个或者绿色大箭头下面的链接，下载leiningen的安装包；

哇然后后面有好多话……暂时不管（因为你们可能看不懂2333）……直接下拉页面到`Detailed installation`
- 子模块`Install location`向你说明了安装位置，窝不复制了，直接翻译一下：
	- 建议安装到用户主目录下，这样呢相关的文件会被写入PATH，而且这也是leiningen默认写入文件的位置；
	- 那么用户主目录在哪里呢？一般是`C:\Users\用户名`,然后你的安装路径就应该写为`C:\Users\用户名\.lein`；
	- 用户名是你自己的用户名，比如窝叫Lulucici，那么窝的安装路径就是`C:\Users\Lulucici\.lein`；
	- 但一般来说，默认的安装路径就是这个，不用改。
- 然后你就安装，就好啦，注意是在线安装哦。

#####else：对于热爱折腾的朋友们，我们在windows上也可以用批处理文件安装
在窝一开始给出的leiningen项目页面的`Windows`模块里还有一句话，就是说你可以用**批处理文件**来安装。

它给了一个链接：[the batch file](https://raw.githubusercontent.com/technomancy/leiningen/stable/bin/lein.bat)

然后你下载，把它弄到PATH里：
- Windows查看PATH的命令，是`echo %PATH%`
	- 然后具体怎么看，你们参考本文档3.2.1的第二步；
	- 注意有一点区别，就是你们的`lein`是有扩展名的，是`lein.bat`
	- 然后窝不知道`mv`这个命令在windows是否生效，如果没有用那你可能要手动移动这个`lein.bat`文件去PATH里了……
- 然后你运行命令`lein self-install`，它就自动安装啦，注意是在线安装。





