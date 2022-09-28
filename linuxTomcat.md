# 二、安装tomcat

- 安装tomcat需要先有java环境，先配置好上一步环境
- 首先去下载tomcat安装包https://link.csdn.net/?target=https%3A%2F%2Ftomcat.apache.org%2Fdownload-80.cgi

![](.\images\image-20220928152446619.png)

- 下载成功后将压缩包传到linux服务器上，一般放在/usr/local下面。在local下创建tomcat文件夹，将压缩包放进去后解压

```c
sudo tar -zxvf apache-tomcat-8.5.56.tar.gz
```

![image-20220928154527728](.\images\image-20220928154527728.png)

-  解压后进入解压的目录下，bin目录下,启动tomcat

```c
./startup.sh
```

![image-20220928154616129](.\images\image-20220928154616129.png)

- 记得开放防火墙8080端口，然后根据ip:8080去访问 ,马赛克部分是你的服务器IP地址

![image-20220928154637159](.\images\image-20220928154637159.png)

## 开放端口

linux [centos7](https://so.csdn.net/so/search?q=centos7&spm=1001.2101.3001.7020) 默认防火墙是关闭的，设置了开启端口后一定要重启防火墙，否则端口开启会不起作用

- 查看已开启的端口

```c
firewall-cmd --list-ports
```

- 查看防火墙状态

```c
firewall-cmd --state
```

- 开启防火墙

```c
systemctl start firewalld
```

- 开启端口

```c
firewall-cmd --zone=public --add-port=8080/tcp --permanent
```

- 重启防火墙

```c
firewall-cmd --reload
```

- 再次查看已开启的端口

```c
firewall-cmd --list-ports
```

![image-20220928154902579](.\images\image-20220928154902579.png)