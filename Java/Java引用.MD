Java引用
------------

#### 强引用
```java
public class StrongReferenceTest {
    public static void main(String[] args) throws InterruptedException {
        StrongReferenceTest object = new StrongReferenceTest();

        System.gc();
        TimeUnit.SECONDS.sleep(1);//暂停一秒钟

        System.out.println(object == null);//false
    }
}
```

#### 软引用
```java
/**
 * java -Xms10m -Xmx10m SoftReferenceTest 
 */
public class SoftReferenceTest {

    static class HeapObject {
        byte[] bs = new byte[1024 * 1024];
    }

    public static void main(String[] args) {
        SoftReference<HeapObject> softReference = new SoftReference<>(new HeapObject());

        List<HeapObject> list = new ArrayList<>();

        while (true) {
            if (softReference.get() != null) {
                list.add(new HeapObject());
                System.out.println("list.add");
            } else {
                System.out.println("---------软引用已被回收---------");
                break;
            }
            System.gc();
        }
    }
}
```

#### 弱引用
```java
/**
 * jdk 1.8
 */
public class WeakReferenceTest {
    static class TestObject{

    }

    public static void main(String[] args) throws InterruptedException {
        WeakReference<TestObject> weakReference=new WeakReference<>(new TestObject());

        System.out.println(weakReference.get() == null);//false

        System.gc();
        TimeUnit.SECONDS.sleep(1);//暂停一秒钟

        System.out.println(weakReference.get() == null);//true
    }
}
```

```java
/**
 * java -Xms10m -Xmx10m SoftReferenceTest
 */
public class SoftReferenceQueueTest {

    static class HeapObject {
        byte[] bs = new byte[1024 * 1024];
    }

    public static void main(String[] args) {
        ReferenceQueue<HeapObject> queue=new ReferenceQueue<>();
        SoftReference<HeapObject> softReference = new SoftReference<>(new HeapObject(),queue);

        List<HeapObject> list = new ArrayList<>();

        while (true) {
            if (softReference.get() != null) {
                list.add(new HeapObject());
                System.out.println("list.add");
            } else {
                System.out.println("---------软引用已被回收---------");
                break;
            }
            System.gc();
        }
        Reference<? extends  HeapObject> pollRef = queue.poll();
        while (pollRef != null) {
            System.out.println(pollRef);
            System.out.println(pollRef.get());
            pollRef = queue.poll();
        }

    }
}
```

#### 虚引用
```java
public class PhantomReferenceTest {
    static class TestObject {

    }

    public static void main(String[] args) throws InterruptedException {
        ReferenceQueue<TestObject> queue = new ReferenceQueue<>();
        PhantomReference<TestObject> phantomReference = new PhantomReference<>(new TestObject(), queue);

        System.out.println(phantomReference.get() == null);//true


    }
}
```


#### 参考
 - https://blog.csdn.net/u011179993/article/details/54564380


