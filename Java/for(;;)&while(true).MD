for(;;) & while(true)
------------------------------
Test.java
```java
public class Test {
  public static void testFor(){
    for(;;);
  }

  public static void testWhile(){
    while(true);
  }
}
```
```shell
javac Test.java
javap -c Test.class
```
```java
Compiled from "Test.java"
public class Test {
  public Test();
    Code:
       0: aload_0
       1: invokespecial #1                  // Method java/lang/Object."<init>":()V
       4: return

  public static void testFor();
    Code:
       0: goto          0

  public static void testWhile();
    Code:
       0: goto          0
}
```
