Docker应用-搭建MySQL主从
-----------------------------

## 准备工作
- 服务器（物理机/云主机/虚拟机）
- Docker 安装
- MySQL
  - 查看版本 (当前为：5.7.21)
   ```sql # 客户端查看
   mysql> select version();
    +------------+
    | version()  |
    +------------+
    | 5.7.29-log |
    +------------+
    1 row in set (0.03 sec)

   ```
   ```shell # 服务器查看
   $ mysql --help | grep Distrib
   mysql  Ver 14.14 Distrib 5.7.21, for Linux (x86_64) using  EditLine wrapper
   ```

## 开始搭建
 - 拉取 MySQL 镜像 (注意版本)
   ```shell 
   # 拉取
   $ docker pull mysql:5.7
   # 查看
   $ docker images|grep mysql
     mysql               5.7                 f965319e89de        10 days ago         448MB
   ```
 - 使用 MySQL 镜像分别启动‘主’‘从’两个容器 
   - 主(Master) 对外映射端口：33061 密码：123456
     `docker run -p 33061:3306 --name mysql-master -e MYSQL_ROOT_PASSWORD=123456 -d mysql:5.7`
   - 从(Slave)  对外映射端口：33062 密码：123456
     `docker run -p 33062:3306 --name mysql-slave -e MYSQL_ROOT_PASSWORD=123456 -d mysql:5.7`

 - 容器查看/停止/删除
   - 查看所有正在运行容器 `docker ps`
   - 停止容器 `docker stop xxx` xxx为容器name
   - 删除容器 `docker rm xxx` xxx为容器name ，删除之前需先停止容器运行

