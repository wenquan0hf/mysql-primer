# 创建后表的修改

alter table 语句用于创建后对表的修改, 基础用法如下:

## 添加列

基本形式: `alter table 表名 add 列名 列数据类型 [after 插入位置]`;

示例:

在表的最后追加列 `address: alter table students add address char(60)`;

在名为 age 的列后插入列 `birthday: alter table students add birthday date after age`;

## 修改列

基本形式: `alter table 表名 change 列名称 列新名称 新数据类型`;

示例:

将表 tel 列改名为 `telphone: alter table students change tel telphone char(13) default "-"`;

将 name 列的数据类型改为 char(16): `alter table students change name name char(16) not null`;

## 删除列

基本形式: `alter table 表名 drop 列名称`;

示例:

删除 birthday 列: `alter table students drop birthday`;

## 重命名表

基本形式: `alter table 表名 rename 新表名`;

示例:

重命名 students 表为 workmates: `alter table students rename workmates`;

## 删除整张表

基本形式: `drop table 表名`;

示例: 删除 workmates 表: `drop table workmates`;

## 删除整个数据库

基本形式: `drop database 数据库名`;

示例: 删除 samp_db 数据库: `drop database samp_db`;