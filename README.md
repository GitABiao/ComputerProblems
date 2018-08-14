# ComputerProblems
## qq、微信等可以登录聊天，但是浏览器不能上网  
这种情况一般是VPN被修改，排除是网络驱动之后尝试以下办法  
1、找到电脑中的“Internet选项”  
2、点击“连接”选项  
3、点击“局域网设置  
4、 将“代理服务器”下“为LAN使用代理服务器”选项去掉
## mysql zip安装步骤
1.  下载mysql zip版本
2.  解压到指定目录
3. 将Mysql的解压目录下的bin文件夹添加到环境变量
4. 打开cmd输入"mysqld -I"初始化命令，很多教程没有这一步所以不能生成data文件夹
5. 打开生成的data目录下的一个XXX.err文件找到类似"root@localhost: *er)UPv:j4m#"后面的"*er)UPv:j4m#"就是初始密码。
6. 创建my.ini文件并填入搜索到的内容（自行搜索ini格式），执行以下命令"mysqld -install MySQL --defaults-file = "mysql安装路径\my.ini"。
7. 启动mysql服务
8. mysql -u root -p 测试
