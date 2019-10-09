# ComputerProblems

## qq、微信等可以登录聊天，但是浏览器不能上网  
这种情况一般是VPN被修改，排除是网络驱动之后尝试以下办法  
1. 找到电脑中的**Internet选项**  
2. 点击**连接**选项  
3. 点击**局域网设置**  
4. 将**代理服务器**下**为LAN使用代理服务器**选项去掉

---

## mysql zip安装步骤(Windows10+MySQL8.0.17)
1. 下载mysql zip版本
2. 解压到指定目录
3. 将Mysql的解压目录下的bin文件夹添加到环境变量
4. 打开cmd输入"mysqld -I"初始化命令，很多教程没有这一步所以不能生成data文件夹
5. 打开生成的data目录下的一个XXX.err文件找到类似"root@localhost: er)UPv:j4m#"后面的"er)UPv:j4m#"就是初始密码。
6. 创建my.ini文件并填入搜索到的内容（自行搜索ini格式），执行以下命令。
```
mysqld -install MySQL --defaults-file = "mysql安装路径\my.ini
```
以下是my.ini文件内容
```
[mysqld]
# Remove leading # and set to the amount of RAM for the most important data
# cache in MySQL. Start at 70% of total RAM for dedicated server, else 10%.
# innodb_buffer_pool_size = 128M
# Remove leading # to turn on a very important data integrity option: logging
# changes to the binary log between backups.
# log_bin
# These are commonly set, remove the # and set as required.
basedir = D:/Program Files/mysql-8.0.17-winx64 #MYSQ安装目录
datadir = D:/Program Files/mysql-8.0.17-winx64/data #MYSQ/DATA目录
port = 3306
# server_id = .....
# Remove leading # to set options mainly useful for reporting servers.
# The server defaults are faster for transactions and fast SELECTs.
# Adjust sizes as needed, experiment to find the optimal values.
# join_buffer_size = 128M
# sort_buffer_size = 2M
# read_rnd_buffer_size = 2M
sql_mode=NO_ENGINE_SUBSTITUTION,STRICT_TRANS_TABLES
character-set-server = utf8mb4
performance_schema_max_table_instances = 600
table_definition_cache = 400
table_open_cache = 256
[mysql]
default-character-set = utf8mb4
[client]
default-character-set = utf8mb4
```
7. 启动MySQL服务
```
net start mysql
```
8. 启动MySQL
```
mysql -u root -p
```
9. 修改密码(进入MySQL之后)
```
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY '新密码';
```

---

## Scrapy安装教程(Windows10+python3.7+scrapy1.5.1)
1. 下载并安装python(本例使用python3.7包含了pip安装器)
2. 配置python环境变量到path"python安装路径"和"python安装路径\Scripts"
3. 利用pip -list查看安装了哪些软件，如果没有则安装以下  
  Python Package: pip and setuptools. 现在 pip 依赖 setuptools ，如果未安装，则会自动安装 setuptools 。
  lxml. 大多数Linux发行版自带了lxml。如果缺失，请查看http://lxml.de/installation.html
  OpenSSL. 除了Windows(请查看 平台安装指南)之外的系统都已经提供。  
  以上基本上都会出现各种问题：建议去https://www.lfd.uci.edu/~gohlke/pythonlibs  下载离线文件安装
4. 安装scrapy，命令：pip install Scrapy
5. 一般会遇到运行时语法错误"SyntaxError: invalid syntax",是因为python3.+版本和twished关键词冲突，解决办法是进入twished目录打开文件（python安装目录\Lib\site-packages\twisted\conch\manhole.py），替换掉里面的所有关键字async
6. 完成安装
