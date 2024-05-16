# 手动代理

这个就在网络设置中将网络代理设为手动。然后添加代理地址和代理端口就可以在网站上访问了;

# 全局代理

在～/.bashrc文件中

export http_proxy='http 127.0.0.1：7890‘

export https_proxy='http 127.0.0.1:7890'

在/etc/apt/apt.conf中

Acquire::http::proxy "http://127.0.0.1:7890/";

这样设置后我们的终端就可以ping一些网站了，同样sudo apt update之类的自然能用；

但这里有个小问题会导致我们在ping一些google之类的会出现域名解析错误；这时候我们需要更换节点就可以;

目前我的代理地址用的是ip route show 出来的

10.0.2.2

# DNS污染

由于防火墙之类的伟大发明，我们的DNS会被攻击，就像刚我ping google可以，但是ping github是不行的，等待很久后会出现一个域名解析错误，很让人难受；

然后我打开 /etc/resolve.conf 一堆东西，我记得我上次该dns还很干净；这时候我们将他删除，重新配置 dns;

sudo rm /etc/resolve.conf

sudo vim /etc/resolve.conf

然后添加两个nameserver

nameserver 8.8.8.8

nameserver 1.1.1.1

然后再去ping一下github会发现能ping了，很舒服;

这时候防止该文件被篡改，我们给他锁住

sudo chattr +i /etc/resolv.conf

如果你自己要改，解锁既可以；

sudo chattr -i /etc/resolv.conf
