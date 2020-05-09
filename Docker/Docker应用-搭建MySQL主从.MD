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
 - 启动‘主’‘从’两个容器  (每个容器有其独立的ip，容器内部尽量使用mysql默认的3306端口)
   - 主(Master) 对外映射端口：3306 密码：123456
     ```shell
     docker run -p 3306:3306 --name mysql-master -e MYSQL_ROOT_PASSWORD=123456 -d mysql:5.7
     ```
   - 从(Slave)  对外映射端口：33062 密码：123456
     ```shell
     docker run -p 33062:3306 --name mysql-slave -e MYSQL_ROOT_PASSWORD=123456 -d mysql:5.7
     ```

 - 容器查看/停止/删除/启动/重启/进入
   - 查看所有正在运行容器 `docker ps`
   - 查看所有容器(包括未运行的) `docker ps -a`
   - 停止容器 `docker stop xxx` xxx为容器id或name
   - 删除容器 `docker rm xxx` xxx为容器id或name ，删除之前需先停止容器运行
   - 启动容器 `docker start xxx` 
   - 重启容器 `docker restart xxx` 
   - 进入容器 
      - `docker attach ...`
      - `docker exec ...`  退出容器终端，不会导致容器的停止

 - 配置‘主’‘从’两个容器
   - 主容器(Master)配置
      - 通过 `docker exec -it mysql-master /bin/bash` 命令进入到 Master 容器内部
      - 更换容器内软件源
        ```shell
        # 备份（习惯）
        $ cp /etc/apt/sources.list /etc/apt/sources.list_bak
        # 替换
        $ sed -i 's/deb.debian.org/mirrors.ustc.edu.cn/g' /etc/apt/sources.list
        ```
      - 容器内安装 vim `apt update` `apt install vim`
      - 编辑配置文件 `vim /etc/mysql/my.cnf`

   - 从容器(Slave)配置
      - 通过`docker exec -it mysql-slave /bin/bash`命令进入到Slave容器内部
