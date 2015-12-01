---
layout: post
title:  "codeigniter-nginx-rewrite"
date:   2012-11-21 21:08:59
categories: codeigniter
---

一直以来都使用Apache作为web server,因为它稳定性高,随着应用服务的不断更新,对web server的要求也更高了,首先就是对高访问量的承载能力,这时nginx进入到我们的视野,它的用户数量逐渐赶上apache,甚至在很多超高访问量的网站中已经取代了Apache,下面我们也进行了一次尝试:
<!--more-->
### 1.下载codeingniter

	sudo wget -c http://codeigniter.com/download.php -O ci.zip

wget是个下载工具，如果没有安装请执行下面语句:

	sudo apt-get install wget

#### 2.解压ci.zip并修改文件夹名称

	sudo unzip ci.zip
	sudo mv CodeIgniter_2.1.3/ ci/

好了,来测试以下http://localhost/ci/
ok,看到没有,是不是熟悉的welcome页面.

那么我们来试试这个地址:http://localhost/ci/welcome
apache有mod_rewrite,nginx有什么呢
	
	in apache
	-------------------
	RewriteEngine On
	RewriteBase /
	RewriteCond $1 !^(index\.php|images|js|css|)
	RewriteCond %{REQUEST_FILENAME} !-f
	RewriteCond %{REQUEST_FILENAME} !-d
	RewriteRule ^(.*)$ index.php/$1 [L]

#### 3.配置nginx
	sudo vi /etc/nginx/sites-available/default

#### 4.修改配置
{% highlight ruby %}
	server {
        server_name domain.tld;
 
        root /var/www/nginx-default/ci;#这里直接将地址指向了ci
        index index.php index.html;
 
        
    ################################################

        #这里
        # set expiration of assets to MAX for caching
        location ~* \.(ico|css|js|gif|jpe?g|png)(\?[0-9]+)?$ {
                expires max;
                log_not_found off;
        }

        location / {
                # Check if a file exists, or route it to index.php.
                try_files $uri $uri/ /index.php;
        }
    ################################################

        location ~* \.php$ {
                fastcgi_pass 127.0.0.1:9000;
                fastcgi_index index.php;
                fastcgi_split_path_info ^(.+\.php)(.*)$;########还有这里
                include fastcgi_params;
                fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
        }
	}
{% endhighlight %}
#### 5.修改ci配置
	cd /var/www/nginx-default/ci/application/config
	sudo vi config.php

    $config['base_url'] = "这里些域名以/结束"
    $config['index_page'] = "" #这里引号中去掉index.php
    $config['uri_protocol'] = "REQUEST_URI" #这里的设置原来是AUTO
    测试了一下AUTO一般的应用没有问题,在ci2.0之后默认支持get,所以这里不改也行，只要你没有特殊的url要求ok

好了我们来试试http://localhost/welcome（因为我们在nginx中设置了`root /var/www/nginx-default/ci;`所以不用http://localhost/ci/welcome了）

再看看http://localhost/user_guide/  (这里要用'/'结尾)

哈哈成功了ok
