## Chapter 1
__Git是一个版本管理控制系统__
### 1.a 下载安装Git
Linux使用 
```bash 
sudo apt-get install git
```
Windows
前往https://git-scm.com/downloads 下载


### 1.b 初次运行Git的配置
当我们安装好Git后，需要在Git bash或者terminal进行作者和邮箱的设置
```bash
git config --global user.name "Your Name"
git config --global user.email "email@example.com"
```
_双引号可加可不加，好像Git新版本没加也是可以的_

__End of Chapter 1__

## Chapter 2

### 2.a 创建Git仓库
可以 __初始化现有文件夹来创建__
```shell
cd 文件夹 
git init
```
也可以 __克隆远程仓库创建__ (如GitHub上的repo) 
```shell
git clone <url>
```
_在尾部加入参数 __自定义本地文件夹名称__，而不会使用默认的远程仓库名_
```
git clone <url> 自定义本地文件夹名称
```


__Git 支持多种数据传输协议。__ 上面的例子使用的是 https:// 协议，不过你也可以使用 git:// 协议或者使用 SSH 传输协议，比如 user@server:path/to/repo.git 。 在服务器上搭建 Git 将会介绍所有这些协议在服务器端如何配置使用，以及各种方式之间的利弊

### 2.b 文件状态
```
git status
```
git status 命令的输出十分详细，但其用语有些繁琐。 Git 有一个选项可以帮你缩短状态命令的输出，这样可以以简洁的方式查看更改。 如果你使用 git status -s 命令或 git status --short 命令，你将得到一种格式更为紧凑的输出。
```
git status -s
git status --short
```
简单看颜色就行
- <font color=Red>红色</font>就是当前文件状态未同步到暂存区
- <font color=Green>绿色</font>就是已同步

<font color=Green>A</font> 文件已被跟踪，并且未修改，已经放入暂存区

<font color=Green>D</font> 对一个已经备份到git仓库中的文件，进行本地文件删除时，查看状态你就会看到绿色D

<font color=Red>M</font> 本地文件和git暂存区文件不一样，出现红色M
<font color=Green>M</font> 本地文件和git暂存区文件一样，出现绿色M
![Alt text](image.png)
<font color=Red>??</font>没有追踪该文件，需要```git add```追踪
![Alt text](image-1.png)