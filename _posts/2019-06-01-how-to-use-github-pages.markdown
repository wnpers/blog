---
layout: post
title:  "应该如何使用Github Pages"
date:   2019-06-01 10:52:25
categories: github-pages
---

GitHub是一个“公共编码”网站。

它允许您上传代码存储库并存储在 Git 版本控制系统上。然后，您可以在代码项目上进行协作，默认情况下系统是开源的，这意味着世界上任何人都可以找到您的GitHub代码，使用它，从中学习，并改进它。同样的，对于其他人的代码您也可以这么做！本文提供了一个基本的指南，即使用Github的gh-pages功能发布内容。
<!--more-->
### 1、发布内容节

GitHub是一个非常重要和有用的社区，值得参与其中，Git / GitHub也是一个非常受欢迎的版本控制系统 - 现在大多数科技公司在其工作流程中使用它。 GitHub有一个非常有用的功能，称为GitHub Pages，它允许您在Web上实时发布网站代码。

### 2、基本Github设置节

首先，在您的机器上安装Git。这是GitHub工作的底层版本控制系统软件。
接下来，注册一个GitHub帐户。这很简单易操作。
注册后，用您的用户名和密码登录github.com。

### 3、准备上传代码节

您可以将任何您喜欢的代码存储在Github资源库中，但要使用GitHub Pages功能实现全面效果，您的代码应该被构造为典型的网站，例如主入口点是一个名为index.html的HTML文件。

第一步，您需要做的另一件事是将您的代码目录初始化为Git存储库。按照下述步骤：
将命令行指向您的test-site目录（或者任何一个您能调用的包含有您的网站的目录）。
为此，请使用cd命令（即“更改目录”）。如果您已经将您的网站放到了位于桌面上的test-site目录中，则可以输入以下内容：

	cd Desktop/test-site

当命令行指向您的网站所在目录时，键入以下命令，该命令告诉git工具将目录转换为git仓库：

	git init

命令行界面
将代码上传到Github的最佳方法是通过命令行 - 这是一个窗口，您可以在其中输入命令来执行诸如创建文件和运行程序等操作，而不是在用户界面内单击。它看起来像这样：

*注意*: 您也可以考虑使用Git图形用户界面来执行相同的工作，如果您不熟悉命令行。
每个操作系统都附带有一个命令行工具：
Windows: 可以通过按Windows键，键入命令提示符，并从出现的列表中选择命令提示符。请注意，Windows具有与Linux和OS X不同的命令约定，因此以下命令可能因您的机器而异。
OS X: 终端可以在应用程序>实用程序中找到。
Linux: 通常你可以用Ctrl + Alt + T启动一个终端。如果不行，请在应用程序栏或菜单中查找Terminal。
起初这可能看起来有点吓人，但不要担心 - 你很快就会得到基本的窍门。您可以通过键入命令并按Enter键来告诉计算机在终端中执行某些操作，如上所示。
为您的代码创建一个仓库节
接下来，您需要为您的文件创建一个新的仓库。单击GitHub主页右上角的加号（+），然后选择“ New Repository”。
在此页面的“Repository name”框中，为您的代码库起一个名字，例如:my-repository。
还要填写一个描述来说明您的存储库将包含哪些内容。你的屏幕应该是这样的

单击Create repository;您将会看到如下页面：

将您的文件上传到GitHub节
在当前页面上，您可能对本节的这部分感兴趣“…or push an existing repository from the command line（或者从命令行推送一个现有存储库）”。您应该看到本节中列出的两行代码。复制整个第一行，将其粘贴到命令行中，然后按Enter键。命令应该看起来像是这样的：

	git remote add origin https://github.com/chrisdavidmills/my-repository.git

接下来，键入以下两个命令，每个命令之后按Enter。这些指令将会把代码上传到GitHub，并要求Git管理这些文件。

	git add --all
	git commit -m 'adding my files to my repository'

最后，将代码推送到GitHub，通过您正在访问的GitHub网页，然后输入我们看到的两个命令中的第二个命令“ …or push an existing repository from the command line（或从命令行部分推入现有存储库）部分”：

	git push -u origin master

现在你需要为你的仓库创建一个gh-pages分支;刷新当前页面，您将看到一个类似下面的存储库页面。您需要点击Branch：master按钮，在文本输入框中输入gh-pages，然后按蓝色按钮，即创建分支Create branch: gh-pages。这将创建一个特殊的代码分支，称为gh-pages，该分支会在特殊位置发布。它的URL采用username.github.io/my-repository-name的格式，所以在我的例子中，URL是https://chrisdavidmills.github.io/my-repository。显示的页面是index.html页面。

在新的浏览器标签中浏览您的GitHub Pages的网址，您将能够在线访问您的网站！通过电子右键把地址发送给你的朋友，炫耀你的掌握的成果吧。
注意 ：如果卡住了，GitHub Pages主页也是非常有帮助的。
更多的GitHub知识节
如果您想对test-site进行更多更改并将其上传到GitHub，那么您只需像以前一样对文件进行更改。然后，您需要输入以下命令（在每个之后按Enter键）将这些更改推送到GitHub：

	git add --all
	git commit -m 'another commit'
	git push

您可以使用更合适的消息替换上一次的提交信息，以描述您刚刚做出的更改。
我们仅仅提供了Git的浅显基本的信息。要了解更多信息，请先从GitHub帮助站点开始。
<!--more-->
 
