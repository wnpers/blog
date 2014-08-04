---
layout: post
title:  "jekyll-install-on-windows"
date:   2014-08-04 09:15:15
categories: jekyll
---

jekyll安装在windows

先安装railsinstaller
	railsinstaller.org
里面包括了需要用的ruby和devkit

更新gem的源 用淘宝镜像
	gem sources --remove http://rebygems.otg/
	gem sources -a http://ruby.taobao.org/

然后用gem来安装jekyll和相关bundle

	gem search --remote jekyll #看下版本
	gem install jekyll --no-ri --no-rdoc
	gem install rdiscount --no-ri --no-rdoc
	gem install wdm --no-ri --no-rdoc


在c:\sites下

	jekyll new wnpers

生成了一个blog

	cd wnpers
	jekyll serve

用localhost:4000访问

然后将他发到github

现在github加一个版本库blog 设置成发布网页
然后将版本库clone下来

	git clone https://github.com/wnpers/blog.git

然后将之前由jekyll产生的wnpers网站文件拷贝到 clone下来的 blog文件夹中 可以先删除blog中的文件和文件夹

记住要配置拷贝过来的根目录下的_config.yml文件 baseurl:blog

这样就可以了发布了

	git add --all
	git commit -m "jekyll first"
	git push

输入用户名 密码就行了