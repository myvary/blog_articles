```
tags: centos
```

Centos 7 firewall 

命令：
查看已经开放的端口：<!--more-->

```
rewall-cmd --list-ports
```

开启端口

```
ewall-cmd --zone=public --add-port=80/tcp --permanent
```
命令含义：
```
–zone #作用域
–add-port=80/tcp #添加端口，格式为：端口/通讯协议
–permanent #永久生效，没有此参数重启后失效
```
重启防火墙
```
firewall-cmd --reload #重启firewall
systemctl stop firewalld.service #停止firewall
systemctl disable firewalld.service #禁止firewall开机启动
```

CentOS 7 以下版本 iptables 命令
如要开放80，22，8080 端口，输入以下命令即可
```
/sbin/iptables -I INPUT -p tcp --dport 80 -j ACCEPT
/sbin/iptables -I INPUT -p tcp --dport 22 -j ACCEPT
/sbin/iptables -I INPUT -p tcp --dport 8080 -j ACCEPT
```
然后保存：
```
/etc/rc.d/init.d/iptables save
```

查看打开的端口：
```
/etc/init.d/iptables status
```
关闭防火墙 
1） 永久性生效，重启后不会复原

开启： `hkconfig iptables on`

关闭： `hkconfig iptables off`

2） 即时生效，重启后复原

开启： `ervice iptables start`

关闭：`service iptables stop`