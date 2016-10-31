# Visual Studio Code 使用Git进行版本控制全攻略

>本来认为此类教程，肯定是满网飞了。今天首次使用VS Code的Git功能，翻遍了
所有中文教程，竟没有一个靠谱的。遂动笔写一篇，造福网友吧。

>* 请确保你安装了最新的VS Code.http://code.visualstudio.com/
>* 请确保安装了最新版的Git。https://git-scm.com/download。git安装到环境变量里，
确保任意路径可以访问。
>* 参考链接：https://code.visualstudio.com/Docs/editor/versioncontrol

VS Code 集成了Git功能，并支持基本的git命令，这使得我们能够在开发过程方便的提交和获取代码。

## 1.1 初始化

首先我们创建一个名为gittest的文件夹，当然它不在git的版本控制管理中。

![](1.jpg)

用VS Code 打开这个文件夹，单击左侧的git图标。

![](2.jpg)

我们可以看到“初始化GIT存储库”的按钮，单击。

![](3.jpg)
初始化之后，我们首先看到的是git栏里显示了当前所有文件，有4个更改。

![](4.jpg)

全部或者单个文件都可以选择暂存或者清理掉。

![](5.jpg)

在上方有提交和刷新按钮，下拉菜单里有更多选项。
再回到我们的文件中，刚才的操作创建了一个.git文件夹，放置了当前仓库的所有
配置文件，如下图。

![](6.jpg)

到目前为止我们在本地创建了一个代码仓库，下面来看一下VS Code的git功能。

## git 输出

我们可以在隐藏的菜单中选择git输出，这样我们每个操作都会显示
在输出区域，方便我们查看对应的git命令。

![](7.jpg)

## 提交保存

提交保存的第一步是暂存文件。

第二步是输入提交信息。

第三步然后使用状态栏的提交按钮提交全部更改。

![](8.png)

## git命令列表

ctrl+shift+P，输入git，会看到VS CODE支持的所有git命令。

![](9.jpg)

### 撤销操作

输入 Undo Last Commit，撤销上次操作。输入Unstage,撤销暂存。

![](10.jpg)

### 分支

输入Branch可以创建当前内容的分支。创建分支时需要输入分支名称。

![](11.jpg)
![](12.jpg)

### checkout

创建分支后，使用checkout命令可以拉取特定的分支内容。

![](13.png)

### 冲突合并

VS Code 会检测文件冲突，并以<<<<<,>>>>,====和颜色区分出来。

![](14.png)

解决冲突之后，直接提交就行了。

### 文件比较

在git文件列表中，单击一个未提交更改的文件，就会打开两个窗口来显示变更的内容。

![](15.jpg)

## 连接远程代码仓库

说了这么多，现在问题来了，在本机初始化一个代码库，一般没什么卵用。
我们大多数情况是要连接远程的代码服务器的。

下面我们在github上创建一个Repository，复制地址备用。

![](16.jpg)
![](17.jpg)

接下来到当前Repository文件夹根目录中，如果没有初始化过，安装文章开始初始化的方法，进行初始化。
然后执行下面的命令

``` shell
git remote add origin https://github.com/xuanhun/vscode.git
git pull origin master
```

现在我们查看一下.git文件夹下的config文件，可以看到添加了远程Reps地址。

![](18.jpg)

接下来我们从下拉菜单中执行发布命令。

![](19.jpg)

这时会提醒我们输入账号和密码。

![](20.jpg)

输入之后，会把本地提交的文件同步到github。同步之后再打开git的隐藏菜单，可以看到
同步等命令可以直接使用了。

![](21.jpg)

## 简化一点的方法

当然我们也可以使用git 的clone命令，从远程克隆一个Reps，然后直接用vscode打开文件夹，
VS Code 会自动识别各项配置。

### 持久化账号

远程连接git的问题解决了，如果你不想每次同步的时候都输入账号信息，可以全局存储账号，
解决这个问题。

``` shell
git config --global credential.helper wincred
```

## 小结

本文的大部分内容都能从官方的文档上找到，不过中文很多教程没有解决连接远程
服务的问题，所以特地做了说明，希望对各位有所帮助。
最后，本篇文章作为实验内容，同步到github的地址为：
[VS Code 集成git](https://github.com/xuanhun/vscode/blob/master/Visual%20Studio%20Code%20%E4%BD%BF%E7%94%A8Git%E8%BF%9B%E8%A1%8C%E7%89%88%E6%9C%AC%E6%8E%A7%E5%88%B6.md)
