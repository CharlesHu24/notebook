### 1. 安装ftp

```
yum install -y vsftpd
```



### 2. 启动服务

```
systemctl start vsftpd.service
```



### 3. 查看端口

```
netstat -antup | grep ftp
```



### 4. 关于配置文件

> vsftpd.ftpusers：位于/etc/vsftpd目录下。它指定了哪些用户账户不能访问FTP服务器，例如root等。
> vsftpd.user_list：位于/etc/vsftpd目录下。该文件里的用户账户在默认情况下也不能访问FTP服务器，仅当vsftpd .conf配置文件里启用userlist_enable=NO选项时才允许访问。
> vsftpd.conf：位于/etc/vsftpd目录下。来自定义用户登录控制、用户权限控制、超时设置、服务器功能选项、服务器性能选项、服务器响应消息等FTP服务器的配置。

#### 4.1 修改vsftpd.conf文件

```
vi /etc/vsftpd/vsftpd.conf

# 修改以下内容

# 禁用匿名用户
anonymous_enable=NO

# 禁止切换根目录　
local_enable=YES

# 解开以下两条注释（若要使用chroot_list则启用这两条），这里不做处理
# chroot_local_user=YES
# chroot_list_file=/etc/vsftpd/chroot_list

# 若要启用 user_list 文件，则改为NO（这里选用这种）
userlist_enable=NO
```



#### 4.2 user_list文件

```
# 将创建的用户添加进来
ftpuser
```



### 5. 创建FTP用户

```
# 创建用户，不能使用root作为用户名 
useradd ftpuser

# 设置密码
passwd ftpuser

# 更改用户主目录权限 权限改为dr-x------
chmod a-w /home/ftpuser

# 设置权限
chmod -s /sbin/nologin ftpuser
```





### 6.关于selinux（以下二选一）- 修改后必须重启

#### 6.1 关闭

```
vi /etc/selinux/config

# 修改以下内容

# 默认是enforcing  把他修改为disabled
SELINUX=disabled
```



#### 6.2 修改（关闭了就不能修改）

```
# 暂时让SELinux进入Permissive模式
setenforce 0 

# 列出与ftp相关的设置
getsebool -a | grep ftp

# 将包含有 ftp_home_dir 和 ftpd_full_access 相关的都设置为 1
setsebool -P ftp_home_dir 1
setsebool -P allow_ftpd_full_access 1
```

### 7. 配置防火墙

```
vi /etc/sysconfig/iptables

# 添加
-A RH-Firewall-1-INPUT -m state --state NEW -m tcp -p tcp --dport 21 -j ACCEPT
```

> [解决CentOS7关闭/开启防火墙出现Unit iptables.service failed to load: No such file or directory.](https://blog.csdn.net/c233728461/article/details/52679558/)



**或者直接关闭防火墙**

```
systemctl stop firewalld
```





### 8. 重启服务

```
systemctl restart vsftpd
```





### 查看ip地址

```
ip addr
```



### 访问

```
ftp://ip:port
```



### 相关命令

```
systemctl enable vsftpd			//开机启动ftp
```



