# 用yum-config-manager生成一个源文件模版
[root@server0 yum.repos.d]# yum-config-manager --add-repo=cdrom
Loaded plugins: langpacks, product-id
adding repo from: cdrom

[cdrom]
name=added from: cdrom
baseurl=cdrom
enabled=1

# 将生成的模版编辑如下
[root@server0 yum.repos.d]# cat cdrom.repo

[cdrom]
name=DVD Media
baseurl=file:///mnt/cdrom
enabled=1

# 挂载CDROM
[root@server0 yum.repos.d]# mount /dev/cdrom /mnt/cdrom/
mount: /dev/sr0 is write-protected, mounting read-only

# 导入RPM-GPG-KEY
[root@server0 yum.repos.d]# rpm --import /etc/pki/rpm-gpg/RPM-GPG-KEY-redhat-xxxx

# 查看
[root@server0 ~]# yum repolist

#libXss.so.1()(64bit) is needed by atom-1.27.0-0.1.x86_64
yum repoquery --nvr --whatprovides libXss.so.1
