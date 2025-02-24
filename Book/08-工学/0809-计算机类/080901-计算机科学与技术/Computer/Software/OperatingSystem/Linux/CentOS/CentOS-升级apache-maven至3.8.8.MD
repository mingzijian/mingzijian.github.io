# CentOS升级apache-maven-3.8.8

### 查看当前版本
$ mvn -version
```shell
Apache Maven 3.0.5 (Red Hat 3.0.5-17)
Maven home: /usr/share/maven
...
```

cd /usr/local
### 下载新版本
$ wget https://dlcdn.apache.org/maven/maven-3/3.8.8/binaries/apache-maven-3.8.8-bin.tar.gz

[更多版本](http://maven.apache.org/download.cgi)



### 解压
$ tar -zxvf apache-maven-3.8.8-bin.tar.gz

### 移出老版本
$ mv /usr/share/maven/*
### 移入新版本
$ cp -r /usr/local/apache-maven-3.8.8/* /usr/share/maven/

### 查看当前版本

$ mvn -version
```shell
Apache Maven 3.8.8 (4c87b05d9aedce574290d1acc98575ed5eb6cd39)
Maven home: /usr/share/maven
...
```

### 配置MAVEN_HOME (新安装需要配置)
```shell
vim /etc/profile

export MAVEN_HOME=/usr/share/maven
export PATH=${PATH}:${MAVEN_HOME}/bin

source /etc/profile

mvn -version

```