Docker 操作  容器迁移
--------------------------------

### 相关概念
#### 镜像
一个特殊的文件系统，只读
#### 容器
镜像的实体，可读可写
### 相关命令
- export
docker export :将文件系统作为一个tar归档文件导出到STDOUT。
`docker export [OPTIONS] CONTAINER`

- import
docker import : 从归档文件中创建镜像。
`docker import [OPTIONS] file|URL|- [REPOSITORY[:TAG]]`

- save
docker save : 将指定镜像保存成 tar 归档文件。
`docker save [OPTIONS] IMAGE [IMAGE...]`

- load
docker load : 导入使用 docker save 命令导出的镜像。
`docker load [OPTIONS]`

### 实操


### 参考
- https://www.cnblogs.com/bethal/p/5945038.html
- https://www.runoob.com/docker/docker-command-manual.html