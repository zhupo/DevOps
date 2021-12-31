#1,安装教程
```
https://www.cnblogs.com/stulzq/p/9291237.html
```

#2,jenkins 下载地址
```
https://www.cnblogs.com/stulzq/p/9291237.html
```

#3,安装
```
rpm -ivh jenkins-2.156-1.1.noarch.rpm
```

#4,配置
```
vi /etc/sysconfig/jenkins

#监听端口
JENKINS_PORT="8080"

#开启阿里云jenkins8080端口
```

#5,配置权限
```
vim /etc/sysconfig/jenkins

#修改配置
$JENKINS_USER="root"

#修改目录权限
chown -R root:root /var/lib/jenkins
chown -R root:root /var/cache/jenkins
chown -R root:root /var/log/jenkins
```

#6,启动
```
systemctl start jenkins
```

#7,安装
```
cat /var/lib/jenkins/secrets/initialAdminPassword

查看此目录密码，并粘贴到管理员密码
```
