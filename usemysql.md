# 使用 MySQL 数据库

## 登录到 MySQL

当 MySQL 服务已经运行时, 我们可以通过MySQL自带的客户端工具登录到MySQL数据库中, 首先打开命令提示符, 输入以下格式的命名:

mysql -h 主机名 -u 用户名 -p

- h : 该命令用于指定客户端所要登录的MySQL主机名, 登录当前机器该参数可以省略;
- u : 所要登录的用户名;
- p : 告诉服务器将会使用一个密码来登录, 如果所要登录的用户名密码为空, 可以忽略此选项。
以登录刚刚安装在本机的MySQL数据库为例, 在命令行下输入 mysql -u root -p 按回车确认, 如果安装正确且MySQL正在运行, 会得到以下响应:

Enter password:

若密码存在, 输入密码登录, 不存在则直接按回车登录, 按照本文中的安装方法, 默认 root 账号是无密码的。登录成功后你将会看到 Welecome to the MySQL monitor... 的提示语。

然后命令提示符会一直以 mysql> 加一个闪烁的光标等待命令的输入, 输入 exit 或 quit 退出登录。

## 创建一个数据库

使用 create database 语句可完成对数据库的创建, 创建命令的格式如下:

```
create database 数据库名 [其他选项];
```

例如我们需要创建一个名为 samp_db 的数据库, 在命令行下执行以下命令:

```
create database samp_db character set gbk;
```

为了便于在命令提示符下显示中文, 在创建时通过 character set gbk 将数据库字符编码指定为 gbk。创建成功时会得到 Query OK, 1 row affected(0.02 sec) 的响应。

>注意: MySQL语句以分号(;)作为语句的结束, 若在语句结尾不添加分号时, 命令提示符会以 -> 提示你继续输入(有个别特例, 但加分号是一定不会错的);

提示: 可以使用 show databases; 命令查看已经创建了哪些数据库。

## 选择所要操作的数据库

要对一个数据库进行操作, 必须先选择该数据库, 否则会提示错误:

ERROR 1046(3D000): No database selected

两种方式对数据库进行使用的选择:

一: 在登录数据库时指定, 命令: `mysql -D 所选择的数据库名 -h 主机名 -u 用户名 -p`

例如登录时选择刚刚创建的数据库: mysql -D samp_db -u root -p

二: 在登录后使用 use 语句指定, 命令:`use 数据库名`;

use 语句可以不加分号, 执行 use samp_db 来选择刚刚创建的数据库, 选择成功后会提示: Database changed

## 创建数据库表

使用 create table 语句可完成对表的创建, create table 的常见形式:

create table 表名称(列声明);

以创建 students 表为例, 表中将存放 学号(id)、姓名(name)、性别(sex)、年龄(age)、联系电话(tel) 这些内容:

```
	create table students
	（
		id int unsigned not null auto_increment primary key,
		name char(8) not null,
		sex char(4) not null,
		age tinyint unsigned not null,
		tel char(13) null default "-"
	);
```
				
对于一些较长的语句在命令提示符下可能容易输错, 因此我们可以通过任何文本编辑器将语句输入好后保存为 createtable.sql 的文件中, 通过命令提示符下的文件重定向执行执行该脚本。

打开命令提示符, 输入: `mysql -D samp_db -u root -p < createtable.sql`

(提示: 1.如果连接远程主机请加上 -h 指令; 2. createtable.sql 文件若不在当前工作目录下需指定文件的完整路径。)

语句解说:

create table tablename(columns) 为创建数据库表的命令, 列的名称以及该列的数据类型将在括号内完成;

括号内声明了5列内容, id、name、sex、age、tel为每列的名称, 后面跟的是数据类型描述, 列与列的描述之间用逗号(,)隔开;

以 "id int unsigned not null auto_increment primary key" 行进行介绍:

- "id" 为列的名称;
- "int" 指定该列的类型为 int(取值范围为 -8388608到8388607), 在后面我们又用 "unsigned" 加以修饰, 表示该类型为无符号型, 此时该列的取值范围为 0到16777215;
- "not null" 说明该列的值不能为空, 必须要填, 如果不指定该属性, 默认可为空;
- "auto_increment" 需在整数列中使用, 其作用是在插入数据时若该列为 NULL, MySQL将自动产生一个比现存值更大的唯一标识符值。在每张表中仅能有一个这样的值且所在列必须为索引列。
- "primary key" 表示该列是表的主键, 本列的值必须唯一, MySQL将自动索引该列。
- 
下面的 char(8) 表示存储的字符长度为8, tinyint的取值范围为 -127到128, default 属性指定当该列值为空时的默认值。

更多的数据类型请参阅 《MySQL数据类型》 : [http://www.cnblogs.com/zbseoag/archive/2013/03/19/2970004.html](http://www.cnblogs.com/zbseoag/archive/2013/03/19/2970004.html)

提示: 
1. 使用 show tables; 命令可查看已创建了表的名称; 
2. 使用 describe 表名; 命令可查看已创建的表的详细信息。