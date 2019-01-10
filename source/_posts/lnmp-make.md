---
title: Brew下安装php7.3+nginx+mysql+pecl(swoole、debug、igbinary、redis)
date: 2019-01-10 16:42:14
tags:
top: 3
---
### 一、安装php7.3
1、运行命令
``` bash
	brew search php7.3
```
查看是否有7.3版本的php，正常是存在的，不存在的话请更新brew，
``` bash
	brew update
```
,然后执行安装
``` bash
	brew install php@7.3
```
安装后再次执行brew search php7.3，可以查看到当前已经安装成功![](./lnmp-make/WX20190110-135803.png)
cd 到该版本php的执行目录下，![](./lnmp-make/1547100608023.jpg)，发现已经安装好了pear、pecl和phpize
![](./lnmp-make/1547100734305.jpg)，然后可以查看下php中已经启用的扩展信息，当前目录下
``` bash
	./php -m
```
2、为php设置一个未使用的端口，编辑php启动文件（注意，php7之前是php-fpm.conf文件，php7后的启动项配置是www.conf文件）
``` bash
	vim /usr/local/etc/php/7.3/php-fpm.d/www.conf
```
修改，![](./lnmp-make/WX20190110-144533.png),这里为了举例，姑且改为9073。
3、开启守护进程，打开
``` bash
	vim /usr/local/etc/php/7.3/php-fpm.conf
```
修改 ，![](./lnmp-make/1547101508207.jpg)，这样在启动php的时候就可以在后台运行而不必中断后在执行其他命令了
4、设置软连接
``` bash
	ln -s  /usr/local/Cellar/php/7.3.0_1/sbin/php-fpm   /usr/local/bin/php-fpm73
```
这样之后再启动php7.3时，只需要执行php-fpm73就可以再后台运行了，很方便吧，运行后可以用php自带的服务查看


### 二、安装nginx



### 三、安装mysql


### 四、安装php扩展swoole，xdebug，igbinary，redis
1、swoole安装
cd 到该版本php的执行目录下，![](./lnmp-make/1547100608023.jpg)，执行
``` bash
sudo ./pecl install swoole
``` 
注意：1、执行哪个版本的php命令，就是把扩展安装在那个版本的php中（这里就是装在php7.3中）。2、要使用sudo执行才会成功，否则报错。3、如果想使用socket或者异步redis，可以在安装过程中的提示中对应项输入yes。
然后一路回车即可。可以参考知乎文章
https://zhuanlan.zhihu.com/p/35974610

2、xdebug安装

3、igbinary安装

4、redis安装


### 五、配置并联合启动
