Tomcat
---------

Tomcat是JavaServlet、JSP、JavaEL和JavaWebSocket技术的开源实现。

### 架构

 ![Tomcat_Architecture](https://gitee.com/mingzijian/resources/raw/master/picgo/image-20210426154315543.png)

```
→ Server 
  → Service
    → Container
      → Engine
        → Host
          → Context
            → Wrapper
              → Servlet
```


### 组件

 - Server
 - Service
 - Connector
 - Engine
 - Host
 - Context
 - Wrapper

### 容器
 - Engine
 - Host
 - Context
 - Wrapper

### 配置


#### 参考
 - https://tomcat.apache.org