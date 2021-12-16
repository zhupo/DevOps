#1.安装php 和php-fpm
# #首先安装epel
```
yum -y install epel-release
```
# # 安装php php-fpm
```
yum -y install php php-fpm
```
# #查看php版本
```
php -v
```

#2.安装php-mysql(安装其他扩展也可以这样)
```
yum install php-mysql
```

#3.设置php-fpm开机自动启动
```
systemctl enable php-fpm
```

#4.启动php-fpm
```
systemctl start php-fpm
```

#5.查看php进程
```
ps -ef | grep php
```