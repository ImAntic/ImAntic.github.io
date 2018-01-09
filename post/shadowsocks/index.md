### 基于   
阿里云香港服务器  
系统 centos7.3
1. 使用repo安装shadowsocks-libev
```
 wget https://copr.fedorainfracloud.org/coprs/librehat/shadowsocks/repo/epel-7/librehat-shadowsocks-epel-7.repo
mv librehat-shadowsocks-epel-7.repo /etc/yum.repos.d/
```
```
yum install epel-release -y   
yum install gcc gettext autoconf libtool automake make pcre-devel asciidoc xmlto c-ares-devel libev-devel libsodium-devel mbedtls-devel -y    
yum install shadowsocks-libev
```
２．配置文件
```
vim /etc/shadowsocks-libev/config.json
```
```
{
    "server":"0.0.0.0",
    "server_port":6666,
    "local_port":1080,
    "password":"你的密码",
    "timeout":60,
    "method":"aes-256-cfb"
}
```
```注意：```
server是服务器IP，默认127.0.0.1 , 只监听本地，不允许远程连接，设置为0.0.0.0时监听全部IP。server_port为服务器监听的端口。


3.启动       
```
systemctl enable shadowsocks-libev.service
systemctl start shadowsocks-libev.service
```
查看运行状态  
```
 status shadowsocks-libev -l
```  
4.开放端口  
* firewall
```
systemctl start firewalld
firewall-cmd --permanent --add-port=6666/tcp
firewall-cmd --reload  
```

5.相关  
* https://github.com/shadowsocks/shadowsocks-libev