#阿里云解释： Centos 8在2021年12月31日已经停止服务,官方源已经下线,解决办法:
#0，原网址：
```
http://www.manongjc.com/detail/29-sxyzcufosjarqtv.html
```
#1，删除AppStream源，
```
rm -f /etc/yum.repos.d/CentOS-AppStream.repo

最好不要删除，使用mv更改名字比较稳妥
```
#2,取消并备份旧yum源（可直接删除）
```
mv /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo.backup
```
#3,下载vault源
```
curl -o /etc/yum.repos.d/CentOS-Base.repo https://mirrors.aliyun.com/repo/Centos-vault-8.5.2111.repo
```
#4,清除yum缓存
```
yum clean all
```
#5,生成新的缓存
```
yum makecache
```

#附加
```
如果出现 Couldn't resolve host 'mirrors.cloud.aliyuncs.com' ，非阿里云服务器无法访问其内网域名，需要作替换，eg：

sed -i -e '/mirrors.cloud.aliyuncs.com/d' -e '/mirrors.aliyuncs.com/d' /etc/yum.repos.d/CentOS-Base.repo
转自：https://www.dianjilingqu.com/
```

#6，更新yum
```
yum update -y
```

#7, 下载php插件
```
yun search php

yum -y install php-mysqlnd php-pdo
```