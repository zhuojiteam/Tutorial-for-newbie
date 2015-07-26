#小课堂番外篇1-工具之包管理器
包管理器即软件包管理系统，通过它可以使用相关命令较为简便地搜索、安装、更新、卸载软件包（主要是开发向）。

简便是……嗯，如果翻墙的话，就是绝对简便的0.0……但墙内可能会碰到一些网络问题导致报错。

下面提供一个简单的指导。
##for Linux
一般是自带的，不同发行版对应的包管理器不一样，可以自己查。
##for OS X
请查阅[homebrew主页](http://brew.sh/index_zh-cn.html)。

扼要地介绍了homebrew的安装与使用。

安装完毕后，使用`brew install packageName`就可以安装各种软件包。

例如，安装scala：
```
brew install packageName
```
此外，可以使用命令`brew -h`查看命令的基本使用说明。
##for Windows
建议把cmd/powershell固定到任务栏，这样用起来比较方便。
###如果你是Windows7及以上版本
试着阅读这个[页面](https://chocolatey.org/)。

简单的解释：

打开cmd，复制粘贴
```
@powershell -NoProfile -ExecutionPolicy Bypass -Command "iex ((new-object net.webclient).DownloadString('https://chocolatey.org/install.ps1'))" && SET PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin
```
回车以后会开始下载安装chocolatey，中途可能因为网络原因等报错，如果刷屏显示连接失败，就`crtl+C`终止，然后重新运行上面这段话。

安装完毕后，重启cmd，输入命令`choco`，会出现一句简短的版本号，则成功。

使用`choco -h`可以查看命令的基本使用说明。

使用`choco install packageName`就可以安装各种软件包。

例如，安装scala：
```
choco install scala.install
```
可能会网络原因报错，重新来就好，如果让你yes/no，打yes，墙内亲测可下载；

窗口上方会出现一个绿色的长条，那是进度条，没关系的；

然后可能跳出一个安装界面，让它装就好。

装完重启cmd，输入命令scala，若有相应且无报错，则成功。

此外还可以下载一下**vim**……日后也会非常管用。使用方法请自查。
###如果你是Windows XP
……我建议你换电脑。

此外可以自己安装powershell，但需要首先安装.net，具体的教程请自查0.0

然后参照上面win7及以上系统安装包管理器的办法进行安装。
