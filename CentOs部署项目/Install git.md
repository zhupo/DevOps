#0,廖雪峰的git教程
```
https://www.liaoxuefeng.com/wiki/896043488029600
```
#1,安装git
```
ssh root@x.x.x.x
yum install git
```
#2，验证
```
git --version
```
#3, 配置基本信息
```
git config --global user.name = "xxx"
git config --global user.email = xxx@qq.com

check:
git config --list
```
#4，配置别名
```
git config --global alias.ck checkout
git config --global alias.cm commit
git config --global alias.br branch
```
#5,配置多用户,(这玩意没难度，看到陌生的东西别太紧张~,静下心来好好学)
a,学习链接
```
博客园:https://www.cnblogs.com/sese/p/12850889.html
简书:https://www.jianshu.com/p/12badb7e6c10
```
b,生成一个新的SSH KEY
```
cd ~/.ssh
ls
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
your_email@example.com 替换你成 Git账号的电子邮件地址。
网上可能很多都是用的  ssh-keygen -t rsa -C "your_email@example.com" 。
这2者的区别是上面那条命令（有-b 4096的）可以让本地机器ssh登录远程机器上的GitHub账户无需输入密码。

注意事项：
SSH默认的生成文件是 id_rsa.pub 和 id_rsa，如果你已经生成过SSH了，那么你在新建另一个账号的SSH的时候，
它会提示你 "Your public key has been saved in /c/Users/admin/.ssh/id_rsa.pub",这个时候你需要另取一个名字，
如生成github账号的你可以设置为 /c/Users/admin/.ssh/id_rsa_github。
```
c,把对应的公钥添加到对应的平台上
```
ssh 生成完之后，把每个账号的SSH的公钥分别添加到对应的平台。
```
d,修改.ssh目录下的config文件,没有就创建一个
该文件用于配置私钥对应的服务器，主要的两项就是User和IdentityFile, Host和Hostname可以随意填写。
```
example:
#Default github
Host github.com
HostName github.com
User git
IdentityFile ~/.ssh/id_rsa

#zhupo
Host github-zhupo
HostName github.com
User git
IdentityFile ~/.ssh/pan_rsa
```

e,将私钥添加到SSH agent(这一步是为了让SSH识别新的私钥)
```
ssh-agent bash
ssh-add ~/.ssh/id_rsa_github
ssh-add ~/.ssh/id_rsa_wxapp
```

f,检查配置是否成功
```
ssh -T git@github.com
ssh -T git@github-zhupo
```

g, 将GitHub SSH仓库地址中的git@github.com替换成新建的Host别名。
```
old: git@github.com:zhupo/DevOps.git
new: github-zhupo:zhupo/DevOps.git

git remote set-url origin github-zhupo:zhupo/DevOps.git

check:
git remote -v
git pull
git fetch
```
# Git 删除多个分支:
```
Git 删除本地除master分支外所有分支：git branch | grep -v "master" | xargs git branch -D
```
