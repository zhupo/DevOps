#1，登录到机器上
```
ssh root@x.x.x.x
```

#2,用git clone 代码
```
cd /var/www/

git clone xxx
```

#3，添加配置文件，开放端口。
```
打开ECS => 实例 => 配置安全组规则 => 手动添加

如下图所示，端口范围填：8888/8888，授权对象填：0.0.0.0/0
```

#4, 配置nginx
```
请查看Centos 配置php环境 => Nginx的安装与配置md
```
