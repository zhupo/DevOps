# 配置yum源

#1.配置yum源
# #下载mysql源安装包
```
wget http://dev.mysql.com/get/mysql57-community-release-el7-8.noarch.rpm
```
# #安装mysql源
```
yum localinstall mysql57-community-release-el7-8.noarch.rpm
```
# #检查mysql源是否安装成功
```
yum repolist enabled | grep "mysql.*-community.*"
```

#2.安装Mysql
```
yum install mysql-community-server
```

#3.启动mysql

# #启动Mysql服务
```
systemctl start mysqld
```

# #查看Mysql的启动状态
```
systemctl status mysqld
```

# #设置Mysql开机启动
```
systemctl enable mysqld
systemctl daemon-reload
```

#4.修改root默认密码

# #找到root默认密码
```
grep 'temporary password' /var/log/mysqld.log
```
# #进入mysql控制台，输入上述查询到的默认密码
```
mysql -uroot -p
```
# #设置root管理员的密码
```
set password for 'root'@'localhost'=password('newPassword'); 
```

#5.添加远程登录用户
#默认只允许root账户在本地登录，如果要在其他机器上连接mysql, 可以修改root允许远程连接，或者添加一个允许远程连接的账户
# #添加远程账户
```
GRANT ALL PRIVILEGES ON *.* TO 'yourname'@'%' IDENTIFIED BY 'YourPassword@123' WITH GRANT OPTION;
```
# #使配置立刻生效
```
FLUSH PRIVILEGES;
```
# #退出Mysql
```
EXIT;
```

#6.配置默认编码为utf8
#修改配置文件/etc/my.conf, 添加下面两行，utf8编码配置
```
character_set_server=utf8 
init_connect='SET NAMES utf8'
```

