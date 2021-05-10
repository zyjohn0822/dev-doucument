# centorOS7 yum 源配置 

## 华为yum源配置 

- [CentOS的镜像地址为](https://repo.huaweicloud.com/centos/) 

1. 备份配置文件：
   ```shell 
   cp -a /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo.bak
   ```
2. 两种方案，请大家自行选取。
- 方案一：
下载新的CentOS-Base.repo文件到/etc/yum.repos.d/目录下，选择CentOS版本：
CentOS 7
执行如下命令：
wget -O /etc/yum.repos.d/CentOS-Base.repo https://repo.huaweicloud.com/repository/conf/CentOS-7-reg.repo
- 方案二：
修改CentOS-Base.repo文件，取消baseurl开头的行的注释，并增加mirrorlist开头的行的注释。将文件中的http://mirror.centos.org替换成https://repo.huaweicloud.com，可以参考如下命令： 

    ```shell
    sed -i "s/#baseurl/baseurl/g" /etc/yum.repos.d/CentOS-Base.repo
    sed -i "s/mirrorlist=http/#mirrorlist=http/g" /etc/yum.repos.d/CentOS-Base.repo
    sed -i "s@http://mirror.centos.org@https://repo.huaweicloud.com@g" /etc/yum.repos.d/CentOS-Base.repo
    ``` 

3. 执行yum clean all清除原有yum缓存。
4. 执行yum makecache（刷新缓存）或者yum repolist all（查看所有配置可以使用的文件，会自动刷新缓存）。 
---- 

<font color="#FF0000">※ 提醒： CentOS 6 及以下版本已被官网源下线, 若需使用, 请参考 CentOS-Vault 进行配置.</font>