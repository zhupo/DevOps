#1，安装地址：
```
https://zhuanlan.zhihu.com/p/34527270
```

#2, 安装Redis
```
yum -y install redis
```

#3, 启动Redis
```
systemctl start redis
```

#4, 修改配置使Redis能被远程连接
```
vi /etc/redis.conf

注释这一行：
#bind 127.0.0.1

//设置密码
另外，推荐给Redis设置密码，取消注释这一行
#requirepass foobared
foobared即当前密码，可以自行修改为
requirepass 密码

//重启服务
systemctl restart redis
```

#5, 常用命令
```
systemctl start redis.service #启动redis服务器

systemctl stop redis.service #停止redis服务器

systemctl restart redis.service #重新启动redis服务器

systemctl status redis.service #获取redis服务器的运行状态

systemctl enable redis.service #开机启动redis服务器

systemctl disable redis.service #开机禁用redis服务器
```

#二，压缩包安装
#1,在官网下载tar.gz的安装包，或者通过wget的方式下载
```
wget http://download.redis.io/releases/redis-4.0.1.tar.gz
```

#2,解压
```
tar -zxvf redis-4.0.1.tar.gz
```

#3,编译
```
cd redis-4.0
make
```

#4,安装
```
make install
实际上，就是将这个几个文件加到/usr/local/bin目录下去。这个目录在Path下面的话，就可以直接执行这几个命令了。

可以看到，这几个文件就已经被加载到bin目录下了
```

#5，启动服务器，来看看安装是否成功
```
使用redis-server命令。
再启动一个linux客户端，redis-cli打开客户端　　
```

#6, 关闭服务器
```
再启动一个linux客户端，通过server-cli shutdown来关闭服务器。
```

#7, 设置redis服务器后台启动
```
daemonize no 修改为daemonize yes
```

#8, 卸载redis
```
卸载redis服务，只需把/usr/local/bin/目录下的redis删除即可
rm -rf /usr/local/bin/redis*
甚至可以把解压包也删除掉
rm -rf /root/redis-stable
```
