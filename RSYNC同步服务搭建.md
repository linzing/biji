     > # 告诉你们我是怎么玩空间的



     ![qinglong](https://mo.lincloud.pro/blog/images/20220123214133.png)



     [七牛云](https://www.qiniu.com/)免费提供10G的空间已经是多年前的事了，虽然空间不大但是作为一个备份空间还是绰绰有余，免费而且稳定。这次来教教大家怎么无脑备份自己的数据到七牛云。全程自动，可以设置定时推送，不怕数据丢失问题，而且还加密，即使是七牛官方也无法知道数据的内容，脚本简单高效，不需要安装任何程序就能胜任工作，确保数据安全无忧，至少我几个服务器的重要数据是这么备份的，这里跳过七牛云注册，准备好你的AK/SK码和空间名，开始吧。


     <!--more-->


     #### 第一步、下载官方的推送工具**qshell**

[rsync文件同步详解](https://www.cnblogs.com/regit/p/8074221.html)
===========================================================

**一.  环境和测试说�?/strong>**

 **rsync(remote sync)是unix及类unix平台下的数据镜像备份软件，它不像FTP那样需要全备份，rsync可以根据数据的变化进行差异备份，从而减少数据流量，提高工作效率

rsync主要分为三个配置文件，分别是rsyncd.conf(主配置文件），rsyncd.secrets(密码文件），rsyncd.motd(服务器信息文件）

本文件以2台机器为列子进行说明

pc1，IP�?92.168.0.230，作为rsync服务器，需要配置rsyncd.conf文件

pc2，IP�?92.168.0.234，作为rsync客户端，不需要配置rsyncd.conf，文件可为空

在服务器端创�?common目录作为共享目录，复制一些测试文件到该目录中，进行测�?/p>

yum -y install rsync   #centos默认安装�?/p>

mkdir /common; cp /etc/init.d/* /common/

**�? 主配置文件说�?/strong>**

 **vim /etc/rsyncd.conf

motd file = /etc/rsyncd.motd    #设置服务器信息提示文件，在该文件中编写提示信�?/p>

transfer logging = yes    #开启rsync数据传输日志功能

log file = /var/log/rsyncd.log    #设置日志文件名，可通过log format参数设置日志格式

pid file = /var/run/rsyncd.log    #设置rsync进程号保存文件名�?/p>

lock file = /var/run/rsync.lock    #设置锁文件名�?/p>

port = 873    #设置服务器监听的端口号，默认�?73

address = 192.168.0.230    #设置本服务器所监听网卡接口的ip地址

uid = nobody    #设置进行数据传输时所使用的帐户名或ID号，默认使用nobody

gid = nobody    #设置进行数据传输时所使用的组名或GID号，默认使用nobody

#若为yes, rsync会首先进行chroot设置，将根映射在下面的path参数路径下，对客户端而言，系统的根就是path参数指定的路径。但这样做需要root权限，并且在同步符号连接资料时只会同步名称，不会同步内容�?/p>

use chroot = no 

read only = yes    #是否允许客户端上传数据，yes表示不允�?/p>

max connections =10    #设置并发连接数，0表示无限�?/p>

[common]    #自定义模块名，rsync通过模块定义同步的目录，可定义多�?/span>

comment = web content    #定义注释说明字串

path = /common    #同步目录的真是路径通过path指定

ignore errors    #忽略一些IO错误

#exclude = test/    #exclude指定common目录下某个目录可以不同步数据

auth users = tom, jerry    #设置允许连接服务器的账户，此账户可以是系统中不存在的用户

secrets file = /etc/rsyncd.secrets    #密码验证文件名，该文件权限要求为只读，建议为600，仅在设置auth users后有�?/p>

hosts allow = 192.168.0.0/255.255.255.0   #设置哪些主机可以同步数据，多ip和网段之间使用空格分�?/p>

hosts deny=*    #除了hosts allow定义的主机外，拒绝其他所�?/p>

list = false    #客户端请求显示模块列表时，本模块名称是否显示，默认为true

**�? 创建密码文件，防火墙设置，客户端和服务器端都要做如下操作**

echo "tom:123" > /etc/rsyncd.secrets

echo "jerry:123" >> /etc/rsyncd.secrets

chmod 600 /etc/rsyncd.secrets

echo "welcome to access" > /etc/rsyncd.motd  #此项客户端不需要做

rsync --daemon    # --daemon表示后台执行，客户端开启rsync不需�?-daemon选项

echo "/usr/bin/rsync --daemon" >> /etc/rc.local    #开机启动rsync服务

firewall-cmd --permanent --add-port=873/tcp    #添加防火墙规则，允许873端口的数据访�?/p>

**�? 客户端同步数�?/strong>**

 **yum -y install rsync

rsync -vzrtopg --progress tom@192.168.0.230::common /test     #通common模块指定�?common目录下的文件拷贝到本客户端的/test目录�?/p>

参数说明

v:显示详细信息

z：传输过程中对数据进行压�?/p>

r：递归

t：保留修改时间属�?/p>

o：保留文件所有者属�?/p>

p：保留文件权限属�?/p>

g：保留文件所属组属�?/p>

a：归档模式，主要保留文件属性，等同�?rlptgoD

--progress：显示数据传输的进度信息

--password-file=FILE：指定密码文件，将密码写入文件，实现非交互式数据同步�?span style="color: rgba(255, 0, 0, 1)">这个文件名也需要修改权限为600

--delete：删除那些仅�?/span>目标路径中存在的文件（源路径中不存在），在脚本中的数据同步经常加上此参数   

--list-only：仅列出服务器模块列表，需要rsync服务器设置list=true

**�?  rsync语法格式，SRC表示源路径，DEST表示目标路径**

1\. 本地复制

rsync [选项] SRC... [DEST]

2\. 通过远程shell复制

下载数据：rsync [选项] [user@a]HOST:SRC...[DEST]     #不加user@表示用root用户进行登陆远程主机下载数据�?本地的DEST路径

上传数据：rsync[选项] SRC...[user@]HOST:DEST   #这里的SRC表示本地数据，DEST表示远端主机目录

3\. 通过rsync进程复制

下载数据

rsync [选项] [user@] HOST::SRC ... [DEST]    #这里双冒号后的SRC表示远端服务端的模块�?/span>

rsync [选项] rsync://[user@]HOST[:port]/SRC...[DEST]   #这里的SRC表示实际的同步目录名，这种方式可以指定端�?/p>

上传数据

rsync [选项] SRC...[user@]HOST::DEST    #上传本地客户端数据到远端服务端的DEST模块名指定的路径

rsync [选项] SRC...rsync://[user@HOST[:port]/DEST

一些例�?/p>

1\. rsync -t *.c 192.168.0.54:src/        #将本机当前目录下的以.c结尾的文件赋值到192.168.0.54的src目录�?/p>

2\. rsync -avz 192.168.0.54:src/bar /data/tmp     #�?92.168.0.54主机上将src/bar目录以递归方式复制到本�?data/tmp目录

3\. rsync -avz 192.168.0.54:src/bar/ /data/tmp   #和例�?的区别是不在/data/tmp目录下创建bar目录

4\. rsync -avz /src/foo /dest    #将本�?src/foo目录复制�?dest目录

5\. rsync -avz tom@192.168.0.230::common /test3    #使用tom账户连接远程192.168.0.230主机的rsync进程，将common模块定义的path路径下载到本地test3目录

6. rsync -avz 192.168.0.230::common /test3     #匿名下载192.168.0.230服务器的common模块至本地的/test3目录

7\. rsync --list-only tom@192.168.0.254::    #显示192.168.0.254服务器所有的模块名称，需要服务器端配置list=true才会显示

8\. 客户端每次连接服务器都需要输入密码很麻烦，可以创建密码文件rsync.pass，在其中包含密码，然后使�?-password-file指定此文�?/span>

echo "123" > rsync.pass   #服务器端用户tom的密�?/span>

rsync -avz --delete --password-file=rsync.pass tom@192.168.0.254::common /dest

**�? 编写简单shell脚本，使客户端定期对rsync服务�?192.168.0.230)的数据进行备�?/strong>**

 **#!/bin/bash

export PATH=/bin:/usr/bin:/usr/local/bin

SRC=common #模块�?/span>

DEST=/data

server=192.168.0.230

user=tom

passfile=/root/rsync.pass

#if the DEST directory not found, then create one

[ ! -d $DEST ] && mkdir $DEST

[ ! -e $passfile ] && exit 2

rsync -az --delete --password-file=$passfile ${user}@${server}::$SRC $DEST/$(data +%Y%m%d)   #加上日期

之后在定时任务中加入执行此脚本即�?/p>********


**
```
rsync --daemon --config=/etc/rsyncd.conf
```
**