测试环境用docker部署在服务器,.今天发现服务异常:
1. 首先查看磁盘是否够用
   df -h
   发现磁盘已经满了

2. 到根目录, 查看是哪一部分占用空间比较大
   发现是项目占用的空间并不是很多, 可能是docker的悬空镜像
3. 查看docker 镜像
   docker images
   发现从去年8月份上线后所有的重启镜像都没有删除过,(重启脚本没有删除老镜像,原因是方便回滚)
4. 删除不用的镜像
   docker image prune -a  
   或者可以使用一下命令:
   docker image prune -a -f 　　#-f强制，不需要确认
5. 清除后的磁盘空间:

