# 操作 MySQL 数据库

## 向表中插入数据

insert 语句可以用来将一行或多行数据插到数据库表中, 使用的一般形式如下:

```
insert [into] 表名 [(列名1, 列名2, 列名3, ...)] values (值1, 值2, 值3, ...);
```

其中 [] 内的内容是可选的, 例如, 要给 samp_db 数据库中的 students 表插入一条记录, 执行语句:

insert into students values(NULL, "王刚", "男", 20, "13811371377");

按回车键确认后若提示 Query Ok, 1 row affected (0.05 sec) 表示数据插入成功。 若插入失败请检查是否已选择需要操作的数据库。


有时我们只需要插入部分数据, 或者不按照列的顺序进行插入, 可以使用这样的形式进行插入:

```
insert into students (name, sex, age) values("孙丽华", "女", 21);
```

## 查询表中的数据

select 语句常用来根据一定的查询规则到数据库中获取数据, 其基本的用法为:

```
select 列名称 from 表名称 [查询条件];
```

例如要查询 students 表中所有学生的名字和年龄, 输入语句 select name, age from students; 执行结果如下:

```
	mysql> select name, age from students;
	+--------+-----+
	| name   | age |
	+--------+-----+
	| 王刚   |  20 |
	| 孙丽华 |  21 |
	| 王永恒 |  23 |
	| 郑俊杰 |  19 |
	| 陈芳   |  22 |
	| 张伟朋 |  21 |
	+--------+-----+
	6 rows in set (0.00 sec)

	mysql>
```

也可以使用通配符 * 查询表中所有的内容, 语句: select * from students;

## 按特定条件查询

where 关键词用于指定查询条件, 用法形式为: `select 列名称 from 表名称 where 条件`;

以查询所有性别为女的信息为例, 输入查询语句: `select * from students where sex="女"`;

where 子句不仅仅支持 "where 列名 = 值" 这种名等于值的查询形式, 对一般的比较运算的运算符都是支持的, 例如 =、>、<、>=、<、!= 以及一些扩展运算符 is [not] null、in、like 等等。 还可以对查询条件使用 or 和 and 进行组合查询, 以后还会学到更加高级的条件查询方式, 这里不再多做介绍。

示例:

查询年龄在 21 岁以上的所有人信息: `select * from students where age > 21`;

查询名字中带有 "王" 字的所有人信息: `select * from students where name like "%王%"`;

查询 id 小于 5 且年龄大于 20 的所有人信息: `select * from students where id<5 and age>20`;

## 更新表中的数据

update 语句可用来修改表中的数据, 基本的使用形式为:

update 表名称 set 列名称=新值 where 更新条件;

使用示例:

将 id 为 5 的手机号改为默认的"-":` update students set tel=default where id=5`;

将所有人的年龄增加 1: update students set age=age+1;

将手机号为 13288097888 的姓名改为 "张伟鹏", 年龄改为 19: `update students set name="张伟鹏", age=19 where tel="13288097888"`;

## 删除表中的数据

delete 语句用于删除表中的数据, 基本用法为:

delete from 表名称 where 删除条件;

使用示例:

删除 id 为 2 的行: `delete from students where id=2`;

删除所有年龄小于 21 岁的数据: `delete from students where age<20`;

删除表中的所有数据: `delete from students`;