# linux4j

Linux for Java
----------------------------------------------------
用户管理命令
who 查看当前用户(详细)   * 
whoami 查看当前用户  *
su 切换用户 *
passwd 给指定用户修改密码  *
useradd  新增用户 *
usermod  修改用户 *
userdel  删除用户 *
groupadd
groupdel
finger
id

基本命令  *
echo 回显字符
man 帮助
help 命令名

clear 清屏
uname 显示OS名
date 显示系统当前时间
exit

文件系统操作  *
ls

ls -l
第一组 当前用户的权限
第二组 当前组的其他用户的权限
第三组 其他组的用户的权限

rwx rwx rwx 
111 111 111  二进制
7   7   7

rw- rw- rw- 
110 110 110  二进制
6   6   6 

rw- --- --- 
110 000 000
6   0   0



fdisk -l
mount /dev/sdb1 /mnt/usb
mount -t iso9660 /dev/cdrom /mnt/cdrom
umount /mnt/usb

目录操作  *
pwd - 显示完整路径
cd  
  cd /     - 进入根目录
  cd xx    - 从当前目录进入子目录 xx
  cd xx/zz - 从当前目录进入子目录 xx 的子目录 zz
  cd ..    - 从当前目录返回到上一级目录
mkdir - 新建目录(文件夹)
rmdir - 删除目录

文件常用操作
rm  *
cp  *
mv  *
find  *
chmod  *
chgrp
ln
more
less
cat  *
grep
head
tail

vi filename  *
a/i/o
esc
:q/:q!/:wq

/etc/inittab 图形界面 5 - 命令行模式 3
命令行模式下输入“startx”也可以直接进入图形界面

rpm -ivh filename.rpm  *
rpm -e filename  *

压缩及解压缩
gzip
gunzip  *
tar cvf filename.tar /home        -压缩/home所有目录和文件   *
tar czvf filename.tar.gz /home    -还原并解压缩  *
compress
zip
unzip
bzip2
bunzip2

进程管理
ps | ps aux  | ps lax | pstree  *
kill PID  *
pgrep
top
nice

网络配置
ifconfig  *
netconfig  

------------------------------------------------------------
VM - setting
Hardware - Network Adapter -> Host-only
Options - Shared Folders -> Enabled
  add Win7:Shared Folders
  Linux: /mnt/hgfs 

Win7:set IP for VMware Virtual Ethernet Adapter for VMnet1 
close win7 firewall  

Linux:
ifconfig -a 查看网卡设备名
ifconfig eth0 192.168.1.78 netmask 255.255.255.0  

close Linux firewall:
->setup

Linux:ping win7 IP

----------------------------------------------------------
Linux access Win7-Oracle
modify listener.ora/tnsnames.ora->host(Win7 IP)

------------------------------------------------------------
安装JDK

# 给当前用户 JDK 授予 执行权限
# chmod u+x jdk-6u16-linux-i586-rpm.bin
# 运行 JDK 安装文件
./jdk-6u16-linux-i586-rpm.bin

#跳出阅读条款
q

yes
# rpm -ivh jdk-6u16-linux-i586-rpm

#配置JDK环境变量
#用 vi 编辑 /etc/profile 文件
vi /etc/profile

# set Java environment
JAVA_HOME=/usr/java/jdk1.8.0_112
export JAVA_HOME
PATH=$JAVA_HOME/bin:$PATH
CLASSPATH=./
export PATH
export CLASSPATH
# End set Java environment

#保存退出后，使配置环境生效
source /etc/profile

java -classpath xxx.jar:./ com.linux.mysql.LinuxMysql

----------------------------------------------------------
Eclipse
#解压Eclipse
gunzip eclipse-jee-juno-SR1-linux-gtk.tar.gz
tar -xvf eclipse-jee-juno-SR1-linux-gtk.tar

----------------------------------------------------------
sublime text
#解压
tar -xjf sublime_text_3_build_3126_x32.tar.bz2
tar -xvf sublime_text_3_build_3126_x32.tar

----------------------------------------------------------
Tomcat
#解压Tomcat
gunzip apache-tomcat-8.5.6.tar.gz
tar -xvf apache-tomcat-8.5.6.tar

#配置Tomcat环境变量
#用 vi 编辑 /etc/profile 文件
vi /etc/profile

# set Tomcat environment
CATALINA_BASE=/opt/apache-tomcat-8.5.6
export CATALINA_BASE
CATALINA_HOME=/opt/apache-tomcat-8.5.6
export CATALINA_HOME
# End set Tomcat environment

#保存退出后，使配置环境生效
source /etc/profile

#启动Tomcat
1.
cd /opt/apache-tomcat-8.5.6
bin/startup.sh    
2.
cd /opt/apache-tomcat-8.5.6/bin
./startup.sh

#关闭Tomcat
bin/shutdown.sh

# Tomcat Console 查看Tomcat控制台 
cd /opt/apache-tomcat-8.5.6
tail -f logs/catalina.out 



#查看Java或Tomcat的进程 PID
ps -ef | grep java/tomcat

#强制中断进程 PID
kill PID



