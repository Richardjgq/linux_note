# 软件应用

**架构 - LNMP**

* 安装软件

  * wget
  * screen
  * curl
  * python

* L:CentOS7.2

* N:Nginx1.10.2

* M:MySQL5.6

* P:PHP7.1

  * Zend Opcache
  * ionCube
  * ImageMagick

* 其他

  * PureFTPd
  * phpMyAdmin
  * Redis
  * Memcached

**软件目录说明**

Apache:/usr/local/apache        \#LAMP、LANMP环境存在

Nginx:/usr/local/nginx              \#LANMP、LNMT环境存在

Tomcat:/usr/local/tomcat        \#LNMT环境存在,访问方式:[http://ip](http://ip/)地址:8080,一般情况下8080端口关闭状态,无法直接访问

JAVA:/usr/java

PHP:/usr/local/php

MySQL:/usr/local/mysql

Pureftpd:/usr/local/pureftpd

Redis:/usr/local/redis

Memcached:/usr/local/memcached

phpMyAdmin：/data/wwwroot/default/phpMyAdmin \#建议修改

Jemalloc:/usr/local/Jemalloc     \#CentOS6.0以上环境存在

软件安装包:/root/oneinstack/src \#如果是web服务器需要新安装模块,可以使用

**数据存储目录**

数据库\(MySQL\):/data/mysql

Web访问日志:/data/wwwlogs

默认ip直接访问内容对应根目录:/data/wwwroot/default,该目录包含首页demo、Opcache  缓存管理、phpinfo、phpmyadmin、探针等文件，如果不需要默认首页，替换该目录中的index.html即可.

PHPINFO地址:[http://IP地址/phpinfo.php](http://IP地址/phpinfo.php)                        \#php版本和组件信息

Opcache地址:[http://IP地址/ocp.php](http://IP地址/ocp.php)

phpmyadmin管理地址:[http://IP地址/phpMyAdmin](http://IP地址/phpMyAdmin)         \#注意大小写,为了数据库安全建议重命名

PHP运行环境探针地址:[http://IP地址/tz.php](http://IP地址/tz.php)

**关于网站根目录权限**

网站根目录权限遵循:

文件 644

文件夹 755

权限用户和用户组 www

出现权限问题,可以使用下面3条命令:

chown -R www.www /data/wwwroot/

find /data/wwwroot/ -type d -exec chmod 755 {} \;

find /data/wwwroot/ -type f -exec chmod 644 {} \;

> FAQ:对于phpMyAdmin的配置文件权限过大问题,也可通过修改phpMyAdmin配置文件解决.
>
> 找到phpMyAdmin目录/libraries/config.default.php文件,把$cfg\['CheckConfigurationPermissions'\]的值从true修改为false.

**服务管理**

Nginx:_service nginx {start\|stop\|status\|restart\|reload\|configtest}_

> 注：如手工更改配置文件,强烈建议reload

MySQL:_service mysqld {start\|stop\|restart\|reload\|status}_

PHP:_service php-fpm {start\|stop\|restart\|reload\|status}    _\#apache服务器中只需要启动Apache服务

Pure-Ftpd:_service pureftpd {start\|stop\|restart\|status}_

Redis:_service redis-server {start\|stop\|status\|restart\|reload}_

Memcached:_service memcached {start\|stop\|status\|restart\|reload}_

Apache:_service httpd {start\|stop\|status\|restart\|reload}_

Tomcat:_service tomcat _{start\|stop\|status\|restart\|reload}  \#仅存在LNMT_环境中_

HHVM:service supervisord {start\|stop\|status\|restart\|reload}

> 注:hhvm进程交给supervisord管理,查看[https://blog.linuxeye.com/408.html](https://blog.linuxeye.com/408.html)



