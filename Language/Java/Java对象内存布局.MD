Java对象内存布局
-------------------------

### 对象头
#### Mark Word

| Mark Word (32 bits) |       State        |
|------------------|--------------------|
| identity_hashcode:25 \| age:4 \| biased_lock:1 \| lock:2 |       Normal       |
| thread:23 \| epoch:2   \| age:4 \| biased_lock:1 \| lock:2 |       Biased       |
| ptr_to_lock_record:30                                          \| lock:2 | Lightweight Locked |
| ptr_to_heavyweight_monitor:30                        \| lock:2 | Heavyweight Locked |
| \| lock:2 |    Marked for GC   |


| Mark Word (64 bits)                                          | State              |
| ------------------ | ------------------ |
| unused:25 \| identity_hashcode:31 \| unused:1 \| age:4 \| biased_lock:1 \| lock:2 | Normal             |
| thread:54  \|       epoch:2                   \| unused:1 \| age:4 \| biased_lock:1 \| lock:2 | Biased             |
| ptr_to_lock_record:62                                                                                      \| lock:2 | Lightweight Locked |
| ptr_to_heavyweight_monitor:62                                                                    \| lock:2 | Heavyweight Locked |
| \| lock:2                                                    | Marked for GC      |

| biased_lock | lock | 状态     |
| ----------- | ---- | -------- |
| 0           | 01   | 无锁     |
| 1           | 01   | 偏向锁   |
| 0           | 00   | 轻量级锁 |
| 0           | 10   | 重量级锁 |
| 0           | 11   | GC标记   |

##### biased_lock：
对象是否启用偏向锁标记，只占1个二进制位。为1时表示对象启用偏向锁，为0时表示对象没有偏向锁。
##### age：
4位的Java对象年龄。在GC中，如果对象在Survivor区复制一次，年龄增加1。当对象达到设定的阈值时，将会晋升到老年代。默认情况下，并行GC的年龄阈值为15，并发GC的年龄阈值为6。由于age只有4位，所以最大值为15，这就是-XX:MaxTenuringThreshold选项最大值为15的原因。

##### identity_hashcode：
25位的对象标识Hash码，采用延迟加载技术。调用方法`System.identityHashCode()`计算，并会将结果写到该对象头中。当对象被锁定时，该值会移动到管程`Monitor`中。
##### thread：
持有偏向锁的线程ID。
##### epoch：
偏向时间戳。
##### ptr_to_lock_record：
指向栈中锁记录的指针。
##### ptr_to_heavyweight_monitor：
指向管程Monitor的指针。


#### Class Pointer
Class Pointer用于存储对象的类型指针，该指针指向它的类元数据，JVM通过这个指针确定对象是哪个类的实例。该指针的位长度为JVM的一个字大小，即32位的JVM为32位，64位的JVM为64位。

##### 压缩指针
为了节约内存可以使用选项`+UseCompressedOops`开启指针压缩

#### Array Length (数组对象特有，普通对象无)
如果对象是一个数组，那么对象头还需要有额外的空间用于存储数组的长度，这部分数据的长度也随着JVM架构的不同而不同：32位的JVM上，长度为32位；64位JVM则为64位。64位JVM如果开启+UseCompressedOops选项，该区域长度也将由64位压缩至32位。
### 对象实例数据
各种类型的字段内容（父类 + 子类）。
### 对齐填充数据
占位符（没有其他作用），虚拟机内存管理系统要求对象起始位置必须是 8 的整数倍。
