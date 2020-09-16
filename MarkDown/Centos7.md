###### Centos 配置

+ tar解压需要使用参数-C来指定解压目录

1. 查看端口使用情况	`netstat -lnpt`

2. 虚拟机连接时，ssh的服务端在连接时自动检测dns环境，导致链接过慢

   + `/etc/ssh/sshd_config`将UseDNS 修改为no
   + 重启 ssh 服务 `systemctl restart sshd.service`

3. 虚拟机安装修改

   + `hostname : /etc/hostname`

   + `ip : /etc/sysconfig/network-scripts/ifcfg-ens33 ` 

     + ```TYPE=Ethernet
       静态IP配置
       BOOTPROTO=static
       NAME=ens33
       UUID=81b24757-87e8-48c9-afd5-5ec6c037fd78
       DEVICE=ens33
       ONBOOT=yes
       IPADDR=192.168.32.101
       NETMASK=255.255.255.0
       GATEWAY=192.168.32.2
       DNS1=114.114.114.114
       DNS2=8.8.8.8```
       systemctl restart netowrk 重启服务
       ```

4. xargs -n1数字 表示一次输出参数中的一个

###### gcc6.3.0 安装

+ 提前安装bz2`yum -y install bz2`

1. 下载tar包

   + `cd /usr/local`

   + `http://mirrors.concertpass.com/gcc/releases/gcc-6.3.0/`

2. 下载依赖文件

   + `cd gcc-6.3.0`
   + `./contrib/download_prerequisites`

3. 避免脏源文件夹，新建文件夹进行编译

   + `mkdir gcc-build-6.3.0`
   + `../gcc-6.3.0/configure --enable-checking=release --enable-languages=c,c++ --disable-multilib`
   + `make -j4 `

4. 安装

   + `make install`


###### maven 配置

1. 下载 bin 包

2. 配置阿里源

   + ```
     <mirror>
         <id>nexus-aliyun</id>
         <mirrorOf>central</mirrorOf>
         <name>Nexus aliyun</name>
         <url>http://maven.aliyun.com/nexus/content/groups/public</url>
     </mirror>
     ```

3. 配置本地仓库地址

   + ```
     <localRepository>local path</localRepository>
     ```

###### cmake 安装

1. 下载解压
   + `wget https://cmake.org/files/v3.3/cmake-3.3.2.tar.gz `
2. 安装gcc
   + `yum install gcc-c++`
3. 安装依赖
   + `./bootstrap`
   + `gmake`
   + make install