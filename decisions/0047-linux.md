# 42.  linux


1.获取源代码：git pull master分支最新代码
2.拷贝到部署目录：scp 要更新服务部署目录
3.安装依赖模块：cd 部署目录执行npm install
4.启动服务：pm2 ./bin/启动文件-i  max

--linux查看某个文件内关键字：cat  文件  |grep 关键字 
--linux查看某个文件路径：find / -name 文件名
--linux查看某个端口占用情况，已经所有端口：netstat -tunlp |grep 8080        netstat -tunlp
--linux查看某个端口是否通 ：telnet 102.106.228.173 8601
--linux主机间文件传输：
scp -r /data/file root@ip:/data/
scp -C /data/sda.img root@ip:/data/img/

--linux 查看当前磁盘情况: df –hl
--linux查看当前文件夹目录磁盘使用情况：du -h --max-depth=1
--linux某一个文件（文件夹）的大小：du   -sh
--linux查看运行的进程启动路径:
--linux创建文件夹：mkdir

--linux HA-PROXY启动命令  service haproxy restart 
--linux zookeeper启动命令 ./bin/zkServer.sh start
--linux 给某个文件或者文件夹权限： chmod 777 –R  /data/run/java_package
一、查看哪些端口被打开 netstat -anp
二、关闭端口号:iptables -A INPUT -p tcp --drop 端口号-j DROP
　　iptables -A OUTPUT -p tcp --dport 端口号-j DROP
三、打开端口号：iptables -A INPUT -ptcp --dport 端口号-j ACCEPT
四、以下是linux打开端口命令的使用方法。
　　nc -lp 23 &(打开23端口，即telnet)
　　netstat -an | grep 23 (查看是否打开23端口)
五、linux打开端口命令每一个打开的端口，都需要有相应的监听程序才可以
 
  --linux查看内存使用情况：free –h

  --linux查看进程占用内存使用情况：pmap -d pid 

--Linux查看服务器访问IP地址: 
netstat -nat|grep ":80"|awk '{print $5}' |awk -F: '{print $1}' | sort| uniq -c|sort –n


--linux限制访问IP:
iptables -I INPUT -s 124.42.103.132 -j DROP--限制访问
iptables -D INPUT -s  -j DROP--解除限制
iptables --list --查看限制列表
iptables --flush--清空限制
iptables -A INPUT -s 124.42.103.132 -p tcp --dport 22 -j ACCEPT--只有某IP能访问22端口

查看进程，按内存从大到小：ps -e -o "%C : %p : %z : %a"|sort -k5 -nr
查看进程，按cpu从大到小：ps -e -o "%C : %p : %z : %a"|sort -nr
查看内存剩余情况：free -m |grep "Mem" | awk "{print $2}"

查看关键字行号:cat -n test.log |grep "地形"


查看日志根据行号:cat -n test.log |tail -n +92|head -n 20
tail -n +92表示查询92行之后的日志
head -n 20 则表示在前面的查询结果里再查前20条记录

需要查找指定时间端的日志:sed -n '/2014-12-17 16:17:20/,/2014-12-17 16:17:36/p'  test.log

Unzip在linux下安装：sudo apt-get install unzip
修改某文件用户权限  sudo chown -R devops:devops config/
NGINX重启命令 /usr/local/nginx/sbin/nginx -s reload

