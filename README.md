# Linux-Docker Examples
### 2019.11.16 - 1.Virtual Machine
下载最新版VirtualBox  
创建一个1GB内存+动态15GB磁盘，名为CentOS的虚拟机。注意，放在合适的位置  
https://opsx.alibaba.com/mirror  
下载CentOS7.7.1908，DVD iso版，4.66GB(4.34GB)  
在虚拟机的光驱，引入下载的CentOS镜像  
鉴于需登录的校园网络特点，网络模式使用默认的NAT模式  
桥接，默认的网络地址转换(NAT)的区别？  
```angular2
桥接模式下宿主机和虚拟机本质上是两台电脑,ip,网络不共享
而在NAT模式下宿主机和虚拟机在网络上是共享的,也就是虚拟机没有
独立的网络层
所以在桥接模式下虚拟机需要连接手机热点才能上网
```
从虚拟机切出鼠标/键盘的控制的快捷键？
```angular2
Right Control(键盘右边的control键)
```

### 2019.11.16 - 2.CentOS
运行虚拟机，进入centos安装模式  
打开网络功能，默认的自动分配IP  
安装位置，无需分区  
安装minimal版，后续软件包可以再添加  
安装过程中，设置root账号密码，创建一个普通操作权限的用户/密码
```angular2
1.创建用户
    `adduser username`
2.设置密码
    `passwd username`
3.对user进行sudo授权
    1.查找sudoers文件
        `whereis sudoers`
    2.改变权限
        `chmod -v u+w /etc/sudoers
    3.将user添加到sudoers
        `vi /etc/sudoers`
        添加内容
            `admin ALL = (ALL) ALL
    4.将sudoers文件权限该回去
        `chmod -v u-w /etc/sudoers
4.测试user
    `su admin` 
```  
安装时，查找资料了解root/普通用户，Linux系统操作权限管理  
安装完毕，光驱卸载iso，重启  

初学者可以直接以root账号登录  
查看网络是否正常，ping通百度  
停止操作快捷键？自动补全快捷键？
```angular2
停止快捷键
    `ctrl + c`
自动补全快捷键
    `Tab`
```

````### 2019.11.16 - 3.SSH
win10可安装win10自带的OpenSSH客户端。什么是SSH？ 
```angular2
ssh是一种安全协议
``` 
Win7安装Bitvise SSH Client或其他SSH客户端  
在VB网络设置中，创建一个宿主机到虚拟机的ssh端口映射  
通过控制台，以root登入虚拟机，注意需显式声明端口参数  
为什么通过ssh连接服务器，而不直接在虚拟机中操作？  
```angular2
方便快捷高效
```

如果能够正确进入服务器，则可以在VB中为虚拟机创建一个系统快照作为基础镜像，
后续操作出问题，可以回滚到当前版本。当然，直接删了虚拟机重来也很方便  

### 2019.11.16 - 4.Don’t Be Scared of the Terminal
基本命令  
清屏，列出，进入/退出目录，根目录，home目录，
创建/删除/重命名目录，查看系统版本，系统内核，cpu/内存占用，磁盘占用。要使用自动补全  
在/home/用户下，练习创建/删除/重命名目录

```
清屏命令: `clear` 或者是 `ctrl + l`
创建
```
### 2019.11.23 - 5.vi
vi，Linux经典编辑器  
在/home/用户下，基于vi创建文件test，编写主函数打印输出hello world  
掌握最基本的操作指令，编辑模式/删除整行/保存退出/不保存退  
在/home/用户下，创建名为code的目录，将文件重命名为hello.c；移动到test目录。即，学习掌握基本的重命名/移动命令

### 2019.11.23 - 6.yum
了解linux的软件管理方式  
yum？repo？rpm？为什么使用yum？基于yum下载的是程序源码还是编译完的二进制文件？  
为什么有时需要下载源码在本地编译，而不是直接下载编译好的二进制文件？   
学习yum基本命令：列出所有已安装，基于通配符查询已安装，所有可更新，更新全部可更新，基于通配符列出远程仓库匹配的软件包，安装所需软件包  
无需添加国内仓库镜像网址，centos自动在延迟最小的仓库下载(我这是上海交大/163镜像)。还是要理解yum repo  
基于yum安装gcc，查看是否已安装    
基于gcc将code目录下的hello.c，编译生成可运行的名为hello的文件，运行查看输出结果    
也可安装openjdk11，编写Java版hello world。java11起可直接通过java命令运行，自动先编译    
gcc安装到哪了？列出安装gcc的位置，各位置的作用，为什么可以在任意位置直接运行gcc命令？  
基于yum history卸载(回滚)gcc及全部依赖  
直接删除非空的test目录。命令参数？ 

### 2019.11.23 - 7.Directory Structure
了解根目录下的，主要目录的功能  
bin/; dev/; mnt/; etc/; opt/; usr/; lib/; home/; /usr/bin/; /usr/lib/; /usr/libexec/;
