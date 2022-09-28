# 一、安装jdk：

详情来源：https://blog.csdn.net/zhang_m_h/article/details/106833492?spm=1001.2014.3001.5502

- 进入到/usr/local 目录下，创建文件夹存放下载的安装包  这里放在了/usr/local/java中

- ```c
  cd /usr/local
  mkdir java
  ```

**先查看centos中自带的jdk并卸载**

```c
[root@root ~]# rpm -qa | grep java     //查看
tzdata-java-2016c-1.el6.noarch
java-1.6.0-openjdk-1.6.0.38-1.13.10.4.el6.x86_64
java-1.7.0-openjdk-1.7.0.99-2.6.5.1.el6.x86_64
[root@root ~]# rpm -e --allmatches --nodeps java-1.6.0-openjdk-1.6.0.38-1.13.10.4.el6.x86_64   //卸载
[root@root ~]# rpm -e --allmatches --nodeps java-1.7.0-openjdk-1.7.0.99-2.6.5.1.el6.x86_64 //卸载
[root@root ~]# rpm -qa | grep java   //再次查看
tzdata-java-2016c-1.el6.noarch
```

- 在线下载命令

```c
 wget --no-check-certificate --no-cookies --header "Cookie: oraclelicense=accept-securebackup-cookie" http://download.oracle.com/otn-pub/java/jdk/8u131-b11/d54c1d3a095b4ff2b6607d096fa80163/jdk-8u131-linux-x64.rpm
```

![image-20220928151813112](C:\Users\yilon\Desktop\All\knowledge\linux安装环境（64位）\images\image-20220928151813112.png)

- 查看是否存在安装包

```c
ls
```

- 给安装包添加执行权限，添加后文件名颜色会发生改变

```c
chmod +x jdk-8u131-linux-x64.rpm
```

- 执行rmp安装

```c
rpm -ivh jdk-8u131-linux-x64.rpm
```

![image-20220928152002285](C:\Users\yilon\Desktop\All\knowledge\linux安装环境（64位）\images\image-20220928152002285.png)

- 查看是否安装成功，安装位置在/usr/java目录下

```c
java -version
```

![image-20220928152112530](C:\Users\yilon\Desktop\All\knowledge\linux安装环境（64位）\images\image-20220928152112530.png)

- 配置JDK环境变量

```c
vi /etc/profile
```

在文件的最后添上如下命令

```c
export JAVA_HOME=/usr/java/jdk1.8.0_131	
export JRE_HOME=${JAVA_HOME}/jre
export CLASSPATH=.:${JAVA_HOME}/lib:${JRE_HOME}/lib:$CLASSPATH
export JAVA_PATH=${JAVA_HOME}/bin:${JRE_HOME}/bin
export PATH=$PATH:${JAVA_PATH}
```

![image-20220928152215973](C:\Users\yilon\Desktop\All\knowledge\linux安装环境（64位）\images\image-20220928152215973.png)

- 编辑完成后保存退出，使profile文件更改立即生效

```c
source /etc/profile
```

- 查看命令是否好使

```c
javac
```

![image-20220928152314655](C:\Users\yilon\Desktop\All\knowledge\linux安装环境（64位）\images\image-20220928152314655.png)