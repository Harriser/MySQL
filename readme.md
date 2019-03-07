<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents** *generated with [DocToc](http://doctoc.herokuapp.com/)*

- [1、配置系统环境变量](#1配置系统环境变量)
- [2、配置初始化的"my.ini"文件](#2配置初始化的myini文件)
- [3、mysqld 服务配置](#3mysqld服务配置)
  - [Found option 错误处理](#found-option-错误)
- [4、安装"mysqld"服务](#4安装mysqld服务)
  - ["myseql"服务存在错误](#myseql服务存在错误)
- [5、启动"mysqlid"服务](#5启动mysqlid服务)
- [Mysql数据库服务的关闭和重启](#mysql数据库服务的关闭和重启)

## SQL Windows 安装

### 1、配置系统环境变量
![环境变量](https://imgur.com/Hw8nI4f.jpg)


### 2、配置初始化的"my.ini"文件
```
[mysqld]
# 设置3306端口
port=3306
# 设置mysql的安装目录
basedir=C:\Program Files\MySQL
# 设置mysql数据库的数据的存放目录
datadir=C:\Program Files\MySQL\Data
# 允许最大连接数
max_connections=200
# 允许连接失败的次数。
max_connect_errors=10
# 服务端使用的字符集默认为UTF8
character-set-server=utf8
# 创建新表时将使用的默认存储引擎
default-storage-engine=INNODB
# 默认使用“mysql_native_password”插件认证
#mysql_native_password
default_authentication_plugin=mysql_native_password
[mysql]
# 设置mysql客户端默认字符集
default-character-set=utf8
[client]
# 设置mysql客户端连接服务端时默认使用的端口
port=3306
default-character-set=utf8
```


### 3、mysqld服务配置
- `mysqld --initialize --console`

```
[Note] [MY-010454] [Server] A temporary password is generated for root@localhost: a5,MsEgFBj.C
```

- [注意][MY-010454][服务器]生成一个临时密码 root@localhost: a5,MsEgFBj.C
- "a5,MsEgFBj.C"为临时密码

#### Found option 错误
```
mysqld: [ERROR] Found option without preceding group in config file dySQL-8.0.15\my.ini at line 1.
mysqld: [ERROR] Fatal error in defaults handling. Program aborted!
```
##### 错误解决，"my.ini"文件，文件编码选择"ANSII"
![ini](https://imgur.com/SjRwuc3.jpg)


### 4、安装"mysqld"服务
- `mysqld --install mysqld`

#### "myseql"服务存在错误
- The service already exists!
  - 服务已经存在

##### 解决方法A
1. 删除的MySQL
- `sc delete mysql`
2. 重新安装
- `mysqld --install mysqld`

##### 解决方法B
- 直接运行MySQL的服务

### 5、启动"mysqlid"服务
- net start mysql

![start](https://imgur.com/TLVtdYT.jpg)
  - 此图代表启动成功

### Mysql数据库服务的关闭和重启
#### 如果未安装"mysql"服务，也可在命令行模式定位到mysql下的bin目录里，输入命令进行关闭或启动
- 停止
  - net stop mysql
- 启动
  - net start mysql

<!-- END doctoc -->
