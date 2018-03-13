# Linux 下访问samba服务器

>介绍两种访问samba服务器的访问方式：第一种是使用smbclient访问samba服务器;第二种是直接将共享目录挂载到自己的电脑上，强烈推荐第二种。

## 通过smbclient

### 1. smbclient安装

```
    sudo apt-get install smbclient
```

### 2.查看目录的所有共享目录

```shell
    smbclient -L 10.236.254.10 # 10.0.0.11是samba服务器IP
```

### 3. 连接共享目录
```shell
    $ smbclient //10.236.254.10/public                                                                                 
    output: 会让输入密码，因为samba为匿名访问，密码一般为空
WARNING: The "syslog" option is deprecated
Enter WORKGROUP\kevin's password: 
smb: \> 提示符，可以输入相关的命令进行操作
```
### 4.smbclient的常用命令

```
    ?或help [command]       提供关于帮助或某个命令的帮助
    ![shell command]        执行所用的SHELL命令，或让用户进入 SHELL提示符
    cd [目录]               切换到服务器端的指定目录，如未指定，则 smbclient 返回当前本地目录
    lcd [目录]        切换到客户端指定的目录；
    dir 或ls        列出当前目录下的文件；
    exit 或quit        退出smbclient
    get file1  file2     从服务器上下载file1，并以文件名file2存在本地机上；如果不想改名，可以把file2省略
    mget file1 file2 file3  filen        从服务器上下载多个文件；
    md或mkdir 目录        在服务器上创建目录
    rd或rmdir   目录        删除服务器上的目录
    put file1 [file2]        向服务器上传一个文件file1,传到服务器上改名为file2；
    mput file1 file2 filen  向服务器上传多个文件
```

## 直接将samba服务器目录挂载到本地

`mount -t cifs -o username=xxx,password=xxx //10.236.254.10/public /home/kevin/smb`