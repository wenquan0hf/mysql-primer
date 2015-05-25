# 附录

修改 root 用户密码

按照本文的安装方式, root 用户默认是没有密码的, 重设 root 密码的方式也较多, 这里仅介绍一种较常用的方式。

使用 mysqladmin 方式:

打开命令提示符界面, 执行命令:` mysqladmin -u root -p password 新密码`

执行后提示输入旧密码完成密码修改, 当旧密码为空时直接按回车键确认即可。

可视化管理工具 MySQL Workbench

尽管我们可以在命令提示符下通过一行行的输入或者通过重定向文件来执行 mysql 语句, 但该方式效率较低, 由于没有执行前的语法自动检查, 输入失误造成的一些错误的可能性会大大增加, 这时不妨试试一些可视化的 MySQL 数据库管理工具, MySQL Workbench 就是 MySQL 官方 为 MySQL 提供的一款可视化管理工具, 你可以在里面通过可视化的方式直接管理数据库中的内容, 并且 MySQL Workbench 的 SQL 脚本编辑器支持语法高亮以及输入时的语法检查, 当然, 它的功能强大, 绝不仅限于这两点。

MySQL Workbench官方介绍: [http://www.mysql.com/products/workbench/](http://www.mysql.com/products/workbench/)

MySQL Workbench 下载页: [http://dev.mysql.com/downloads/tools/workbench/](http://dev.mysql.com/downloads/tools/workbench/)