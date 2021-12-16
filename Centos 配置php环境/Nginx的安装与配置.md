#1.下载安装包
```
Nginx 下载地址: http://nginx.org/download/
wget http://nginx.org/download/nginx-1.20.2.tar.gz
```
#2.解压Nginx的tar包，并进入解压好的目录
```
tar -zxvf nginx-1.20.2.tar.gz
cd nginx-1.20.2/
```
#3.安装Zlib、pcre、openssl库
```
yum install zlib zlib-devel
yum install pcre pcre-devel
yum install openssl openssl-devel
```
#4.配置、编译并安装
```
./configure --with-http_ssl_module
make && make install
```
#5.启动nginx
```
/usr/local/nginx/sbin/nginx
```
#6.将nginx添加到环境变量
```
1, vim /etc/profile

2, Add:
PATH=$PATH:/usr/local/nginx/sbin
export PATH

3, source /etc/profile
```
#7.nginx 常用命令
```
fuser -k 80/tcp #杀死80端口
nginx -s stop #停止
nginx -s reopen #重启
nginx -s reload #重新载入配置文件(热启动)
```
#8.nginx配置php
```
server {
        listen       80;
        server_name  xx.xxx.xxx.xxx; # 你的域名
        root /var/www/film-backend/frontend/web/;
        index index.html index.htm index.php;
        location / {
            try_files $uri $uri/ /index.php?$args;
            #index index.php;
        }
        location ~ ^(.+\.php)(.*)$ {
            fastcgi_param  SCRIPT_FILENAME $document_root$fastcgi_script_name;
            fastcgi_pass   127.0.0.1:9000;
            fastcgi_index  index.php;
            include        fastcgi_params;
        }
    }
```