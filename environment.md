# Windows 下 MySQL 的配置

以 MySQL 5.1 免安装版为例, 下载 [mysql-noinstall-5.1.69-win32.zip](http://dev.mysql.com/downloads/mysql/5.1.html#downloads )

配置步骤:

1. 将下载的 mysql-noinstall-5.1.69-win32.zip 解压至需要安装的位置, 如: C:\Program Files;

2. 在安装文件夹下找到 my-small.ini 配置文件, 将其重命名为 my.ini , 打开进行编辑, 在 [client] 与 [mysqld] 下均添加一行: default-character-set = gbk

3. 打开 Windows 环境变量设置, 新建变量名 MYSQL_HOME , 变量值为 MySQL 安装目录路径, 这里为 C:\Program Files\mysql-5.1.69-win32

4. 在 环境变量 的 Path 变量中添加 ;%MYSQL_HOME%\bin;

5. 安装 MySQL 服务, 打开 Windows 命令提示符, 执行命令: mysqld --install MySQL --defaults-file="my.ini" 提示"Service successfully installed."表示成功;

 

MySQL 服务的启动、停止与卸载

在 Windows 命令提示符下运行:

启动: net start MySQL

停止: net stop MySQL

卸载: sc delete MySQL