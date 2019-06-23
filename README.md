#create-a-flasrum-for-deep-learning  

在centOS7环境上安装`php7+`  
---------------------------  

首先先卸载原来的版本  
```yum - y remove php*```  
由于yum中原来不存在`php7*`的资源，所以我们要更改源
```rpm -Uvh https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm```  
```rpm -Uvh https://mirror.webtatic.com/yum/el7/webtatic-release.rpm```  
然后安装各种php的包，看自己需要而定  
```yum -y install php72w php72w-cli php72w-common php72w-devel php72w-embedded php72w-fpm php72w-gd php72w-mbstring php72w-mysqlnd php72w-opcache php72w-pdo php72w-xml```   
新建一个用户，增加安全性  
``` \#adduser flarum```  
暂时停留在root权限下执行命令，创建用户`flarum`的原因是为了在运行的时候以这个用户的权限运行。  

使用这条命令可以安装flarum  
```composer create-project flarum/flarum . --stability=beta```   
安装成功之后，必须要设置nginx的目录才能访问   
``` vim /etc/nginx/conf.d/default.conf```   
如果是lnmp   
```vim /usr/local/nginx/conf/vhost/www.****.***.conf```   
在此文件件中找到server{}，其中修改 如下所示：
```root  /home/flarum/flarum/public;
   include /home/flarum/flarum/.nginx.conf;
```
保存退出

