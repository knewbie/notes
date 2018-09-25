# mysql


## 安装 

`sudo apt install mysql-client mysql-server`

## 终端工具mycli
`mycli`是一个基于Python开发的mysql终端命令行工具,具有自动补全功能,非常实用.
安装:`sudo apt install mycli`

使用方式跟原生的`mysql`命令一样.

## 问题

初次安装完mysql后,连续被拒问题:
`Q: error: 'Access denied for user 'root'@'localhost''`

解决办法:

1. 通过`sudo`命令来执行`mysql`

```
sudo mysql -u root
```

2. 检查`user`数据库中的账号信息

```

SELECT User,Host FROM mysql.user;
+------------------+-----------+
| User             | Host      |
+------------------+-----------+
| admin            | localhost |
| debian-sys-maint | localhost |
| magento_user     | localhost |
| mysql.sys        | localhost |
| root             | localhost |

```

3. 删除 `root@localhost` 账号

```
mysql> DROP USER 'root'@'localhost';

Query OK, 0 rows affected (0,00 sec)

```

4. 重新创建一个账户

```
mysql> CREATE USER 'root'@'%' IDENTIFIED BY '';

Query OK, 0 rows affected (0,00 sec)
```

5.给新加的账户设置权限(别忘了flush权限)

```
mysql> GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' WITH GRANT OPTION;

Query OK, 0 rows affected (0,00 sec)

### !!!! 一定要执行
mysql> FLUSH PRIVILEGES;

Query OK, 0 rows affected (0,01 sec)
```

退出后,就可以不用`sudo`命令进行连接了.
