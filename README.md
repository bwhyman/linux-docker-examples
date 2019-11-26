# Linux-Docker Examples
### 2019.11.16 - 1.Virtual Machine
下载最新版VirtualBox  
创建一个1GB内存+动态15GB磁盘，名为CentOS的虚拟机。注意，放在合适的位置  
https://opsx.alibaba.com/mirror  
下载CentOS7.7.1908，DVD iso版，4.66GB(4.34GB)  
在虚拟机的光驱，引入下载的CentOS镜像  
鉴于需登录的校园网络特点，网络模式使用默认的NAT模式  
桥接，默认的网络地址转换(NAT)的区别？  
从虚拟机切出鼠标/键盘的控制的快捷键？

### 2019.11.16 - 2.CentOS
运行虚拟机，进入centos安装模式  
打开网络功能，默认的自动分配IP  
安装位置，无需分区  
安装minimal版，后续软件包可以再添加  
安装过程中，设置root账号密码，创建一个普通操作权限的用户/密码  
安装时，查找资料了解root/普通用户，Linux系统操作权限管理  
安装完毕，光驱卸载iso，重启  

初学者可以直接以root账号登录  
查看网络是否正常，ping通百度  
停止操作快捷键？自动补全快捷键？

### 2019.11.16 - 3.SSH
win10可安装win10自带的OpenSSH客户端。什么是SSH？  
Win7安装Bitvise SSH Client或其他SSH客户端  
在VB网络设置中，创建一个宿主机到虚拟机的ssh端口映射  
通过控制台，以root登入虚拟机，注意需显式声明端口参数  
为什么通过ssh连接服务器，而不直接在虚拟机中操作？  

如果能够正确进入服务器，则可以在VB中为虚拟机创建一个系统快照作为基础镜像，
后续操作出问题，可以回滚到当前版本。当然，直接删了虚拟机重来也很方便  

### 2019.11.16 - 4.Don’t Be Scared of the Terminal
基本命令  
清屏，快速删除命令，列出，进入/退出目录，根目录，home目录，
创建/删除/重命名目录，查看系统版本，系统内核，cpu/内存占用，磁盘占用。要使用自动补全  
在/home/用户下，练习创建/删除/重命名目录

### 2019.11.23 - 5.vi
vi，Linux经典编辑器  
在/home/用户下，基于vi创建文件test，编写C语言主函数打印输出hello world  
掌握最基本的操作指令，编辑模式/删除整行/保存退出/不保存退出  
在/home/用户下，创建名为code的目录，将文件重命名为hello.c；移动到code目录。即，学习掌握基本的重命名/移动命令

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

### 2019.11.26 - 8.bash & chmod
Shell？bash？cat？了解脚本的：基本结构，支持的语句，执行linux命令，运行即可  
在/home/用户名/test下，基于vi编写一个由bash执行的，打印出/home/用户名/test/下所有文件的脚本  
需要添加脚本文件的执行权限，运行  
基于cat读取显式脚本代码  

带权限的列出文件
chmod命令，r/w/x？3组权限？u/g/o？增加/修改/删除指定角色的指定权限。使用语义参数比数字好记  
为以上脚本文件，添加创建者具有读写执行权限命令？取消其他用户的读权限？  
权限角色，u，所有者；g，组；o，其他人  

### 2019.11.26 - 9.Docker
可以把安装的gcc/openjdk等等都卸载了  
https://docs.docker.com/engine/docker-overview/  
https://geekflare.com/docker-vs-virtual-machine/  
https://yeasy.gitbooks.io/docker_practice/  
了解早先服务器基于虚拟化技术的部署，为什么使用虚拟化技术？当前Docker的虚拟化与之前的区别？优点？了解docker images docker containers？  
Servers？VPS？Cloud Servers？为什么VPS创建了就开始计时付费？而云可以按流量/CPU内存等的实际使用量弹性付费？  

https://docs.docker.com/  
官网查找适合centos系统的docker-ce社区稳定版的安装方法。Community版？  
安装基本工具；添加docker官方仓库，下载docker-ce本身的仓库使用官方地址即可，速度很快。无需指定版本，安装最新版docker-ce  
启动docker。开机自动启动docker服务

### 2019.11.26 - 10.Docker Images
docker官方镜像仓库国内速度慢，基于vi修改配置文件，
使用微软Azure仓库https://dockerhub.azk8s.cn，我这拉取500MB镜像1分钟。基本满速。服务器在国外的不要配。其他仓库要么需要密钥，要么已作废  
重新加载配置，重启docker  

Docker基本命令：拉取镜像；列出本地镜像；删除镜像；不建议在本地查询，去官方网站查询更方便  
不用拉取hello-world测试，直接拉取最新的openjdk  
如果出现Error response from daemon，说明centos DNS域名解析错误，修改系统DNS解析地址为Google的域名服务器  
Docker仓库？docker镜像仓库？

### 2019.11.26 - 11.Docker Container
#### Docker run
Docker命令：基于指定镜像创建容器；列出全部已创建的容器；停止运行容器；删除容器。容器ID使用hash值的前2位即可  
run基本参数：-p；-v；-d；-i；-t；--rm    
创建容器时，追加在容器启动后，容器内执行操作指令  
在/home/用户名/test下，创建HelloWorld.java  
基于openjdk创建一个容器：挂载home/用户名/test/目录到容器内的/home/code/目录，
即可以在容器中访问挂载目录中的文件；测试用，创建运行完就删除容器；
在前台运行，即显示容器中的输出，后台运行看不到输出；添加容器内java直接运行挂载目录下的HelloWorld的命令  

当容器中没有运行的进程时，容器将关闭。tomcat/MySQL/Nginx等带服务进程的容器会一直运行，
而普通openjdk的容器运行即关闭，除非运行像带web容器的springboot  
如何创建一个不关闭的openjdk容器？  
创建一个openjdk容器：依然挂载以上目录；启动标准输入，
启动终端控制台；在后台运行；在容器内运行/bin/bash。即，创建一个一直运行的进程，使容器不会关闭；  
查看容器是否为运行状态  

#### Docker exec
exec基本参数：-i；-t。结合/bin/bash使用  
以可互交的带终端的模式，进入之上创建的后台运行的，未停止的openjdk容器   
在容器内进入挂载目录，运行HelloWorld，查看输出  
查看容器内系统版本？查看镜像/容器信息？查看镜像/容器占用？

### 2019.11.26 - 12.FirewallD & Services
CentOS集成的firewall工具。ports？firewall zone？使用默认的zone-public无需声明  
列出firewall所有打开服务与端口等信息，这一个命令就够所有查询了  
防火墙重载；永久开启http服务；永久打开80端口；永久关闭服务；永久关闭端口  
firewall规则为动态添加，改变规则后需重载，无需重启    

查看一个服务的状态。一个服务的启动/停止/启动/禁用。基于firewalld操作

### 2019.11.26 - 12.Docker Web Container
在宿主机，通过scp命令将本地文件上传到服务器。注意，虚拟机网络为NAT模式，需显式声明ssh映射的端口，但参数与ssh命令不同  
创建目录，/home/用户名/services/。services下按应用创建目录  
将/github/resources/docker-examples.war文件下载到本地，再上传到/home/用户名/services/docker-tomcat/。目录需先创建  

拉取最新tomcat镜像。默认暴露的端口？部署路径？集成的openjdk版本？查看镜像信息？  
基于命令行创建一个容器：映射服务器80端口到容器的8080端口；挂载docker-examples.war所在目录到容器中的部署目录；后台运行  
查看容器是否创建/启动成功。容器中的tomcat自动在挂载目录解压war包部署  
在虚拟机添加端口，例如8888，映射虚拟机的80端口  
在宿主浏览器，本地+端口+部署在tomcat应用的名称，访问应用  

https://github.com/firewalld/firewalld/issues/461  
创建容器时在服务器映射的端口，即使服务器firewall没有开启服务或端口，外部依然可以直接访问？  
停止，并删除此容器。命令写在一行执行  
注意，服务器的一个端口只能被一个应用/容器监听，反复创建容器会端口冲突  

### 2019.11.26 - 12.Dockerfile
Orchestration System？为什么需要Docker Compose？优点？k8s(Kubernetes)？k8s与官方docker compose的适用场景？编写docker-compose文件的最大最大特点？  
https://docs.docker.com/compose/  
按官网教程安装最新版，添加执行权限  
基于vi在/home/用户名/services/docker-tomcat/下，编写一个docker-compose文件，基于第3版，服务名称自定义。
将14Docker Web Container，基于命令行创建容器的命令，转为在文件中描述，包括tomcat基础镜像，挂载目录，映射端口  
基于文件创建在后台运行的容器；停止/停止删除基于文件创建的容器  
查看容器日志，错误时可查看  
注意，严格的缩进与空格