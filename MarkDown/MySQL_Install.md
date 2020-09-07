1. 下载安装的rpm包
   + `rpm -Uvh mysql80-community-release-el7-3.noarch.rpm`
2. yum仓库默认选择最新版的mysql，低版本需要手动设置
   + 查看yum仓库中所有版本mysql状态
     + `yum repolist all | grep mysql`
   + 如果我们要安装5.7而不是8.0版本可以关闭8.0子存储库，开启5.7子存储库
     + `sudo yum-config-manager --disable mysql80-community`
     + `sudo yum-config-manager --enable mysql57-community`
   + yum-config-manager命令在yum-utils包中，默认没有安装
     + `yum -y install yum-utils`
   + 也可以手动设置关闭8.0开启5.7在`/etc/yum.repos.d/mysql-community.repo`文件下
   + 使用`yum repolist enable | grep mysql`查看开启的子仓库
   + 如果使用EL8系统，它包含一个默认开启的module，它屏蔽了MySQL存储库提供的包，需要手动关闭
     + `sudo yum module disable  mysql`
   + 安装MySQL服务
     + `sudo yum install mysql-community-server`
   + 启动MySQL server
     + systemctl start mysqld.service
   + 查看MySQL server状态
     + systemctl status mysqld.service
3. msyql安装中会初始化server,在data文件夹生成ssl certificate和keys file,创建root用户
   + root用户密码放在err.log日志中
     + `grep 'temporary password' /var/log/mysqld.log`
   + 更改密码
     + `ALTER USER 'root'@'localhost' IDENTIFIED BY 'MyNewPass4!'`
   + 设置MySQL服务开启自启
     + systemctl enable msyqld.service
   + mysql默认安装位置
     + `/var/lib/mysql`