#安装宝塔面板： 
```
https://developer.aliyun.com/ask/233242
https://www.zjszjs.com/notes/81.html
http://tencent.yundashi168.com/327.html?spm=a2c6h.13066369.0.0.4e5679c6krIx7d&userCode=28kqeewo
```

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

#6.常用命令
```
systemctl start php-fpm #启动
systemctl stop php-fpm #停止
systemctl restart php-fpm #重启
```

#7.java LNMP 环境
```
OneinStack
```

#8. 宝塔安装步骤
```
阿里云服务器安装宝塔面板图文教程
购买完云服务器ECS后，对于新手而言如何搭建Web环境是比较棘手的，分享一款简单易用的主机面板：宝塔面板，分享阿里云服务器安装宝塔面板图文教程：


本文以：Linux云服务器，CentOS 7.4 64位系统为例。

一：开放安全组端口
什么是安全组？是阿里云ECS云服务器特有的虚拟防火墙，是一种安全机制，默认情况下宝塔面板依赖的端口并没有开放，所以我们第一步是自定义安全组开放端口，如下图所示：


我们以开放8888号端口为例：
1、登录到云服务器ECS控制台；
2、点击“更多”--“网络和安全组”--“安全组配置”，点击“配置规则”
3、如下图所示，端口范围填：8888/8888，授权对象填：0.0.0.0/0


端口范围按照格式，填写我们需要开放的端口；授权对象填0.0.0.0/0的意思是对所有人开放这个端口，授权范围大家可以按照自己的需求自定义。
宝塔面板需要开放的端口有：8888、888、80、443、20、21，这6个端口都需要开放，大家按照上面的方法开放即可。

安全组不会操作，可以参考阿里云官方文档： 阿里云安全组的典型应用示例

二：安装宝塔面板
SSH的方式登录到你的云服务器ECS上，命令：ssh root@你的服务器IP
执行命令：
yum install -y wget && wget -O install.sh http://download.bt.cn/install/install_6.0.sh && sh install.sh然后输入字母“y”，等待程序自行安装，大约2分钟

三：保存宝塔面板后台登录名和密码
执行上述命令后，程序自动安装，安装完毕后，会出现宝塔后台登录的账户名和密码，大家保存下来
Complete!
==================================================================
Congratulations! Install succeeded!
==================================================================
Bt-Panel: http://47.104.71.103:8888
username: admin
password: 66d52887
Warning:
If you cannot access the panel,
release the following port (8888|888|80|443|20|21) in the security group
==================================================================
宝塔面板后台登录地址为：http://你的服务器IP/8888
默认登录名为：admin
密码：安装完成后，会随机生成一段密码，请保存好

四：登录到宝塔面板后台，安装web环境
使用刚才保存的账户名和密码，登录到宝塔面吧后台，一键安装Web环境，登录宝塔面板后台，地址：http://你的服务器IP/8888，输入刚才保存好的账户和密码

登录后会自动弹出安装Web环境页面，如下图所示：


可选LNMP和LAMP两种Web环境，大家按需选择（推荐选择第一个LNMP），然后点击“一键安装”，等待即可。大约需要8分钟。

五：创建站点
Web环境一键安装完毕后，点击左侧“网站”---“添加站点”，如下图所示：



输入域名后，默认不会自动创建FTP和MySQL数据库，我们可以选择自动创建，方便省事，点击“提交”，创建成功后，会显示你的FTP和MySQL数据信息，例如：

FTP账号资料
用户：aliyunbaike_com
密码：625GcrKSc3
只要将网站上传至以上FTP即可访问!
数据库账号资料
数据库名：aliyunbaike_com
用户：aliyunbaike_com
密码：e8QZfQDPDT


大家将新建站点的FTP账户密码、数据库账户密码都保存好。
  
六：域名解析
将域名解析到你的服务器IP，解析出成功后，会显示“恭喜，站点创建成功！”

七：网站安装
将你的网站程序上传到域名所对应的根目录，如果是新站，输入第五步的数据库账户和密码。
```
