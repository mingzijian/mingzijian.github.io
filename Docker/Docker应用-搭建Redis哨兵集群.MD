Docker应用-搭建Redis哨兵集群
----------------------------------
<pre>Redis4.0 一主两从三哨兵</pre>
#### 准备工作
 - 服务器（物理机/云主机/虚拟机）
 - Docker 安装
 - Redis 版本选择
   - 版本查看
   ```shell
    # 在服务器上查看
    $ redis-server -v

    # 在客户端上查看
    > info server
   ```
#### 开始搭建
 - 拉取 Redis 镜像 (注意版本)
    ```shell
    # 拉取
    $ docker pull redis:4.0
    
    # 查看
    $ docker images|grep redis
    ```


#### 参考
 - https://www.cnblogs.com/hutao722/p/9644620.html