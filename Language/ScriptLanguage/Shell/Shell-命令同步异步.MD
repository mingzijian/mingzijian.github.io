Shell命令同步异步
----------------
async-parent.sh
```shell
#!/bin/bash

#
# 异步执行（wait）使用样例-父脚本
#

echo "父脚本：启动子脚本.."
./async-child.sh &

# 通过将shell参数 $! 赋给pid变量，以记录子进程的进程ID
pid=$!  

echo "父脚本：子脚本(PID=${pid})已启动"

echo "父脚本：继续执行中.."
sleep 2

echo "父脚本：暂停执行，等待子脚本执行完毕.."
wait ${pid}

echo "父脚本：子脚本已结束，父脚本继续.."
echo "父脚本：父脚本执行结束。脚本退出！"
```

async-child.sh
```shell
#!/bin/bash

#
# 异步执行（wait）使用样例-子脚本
#

echo "子脚本：正在运行.."
sleep 5
echo "子脚本：子脚本结束。脚本退出！"
```

#### 参考
 - https://my.oschina.net/u/2000675/blog/1811006