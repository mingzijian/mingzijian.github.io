java.lang.StrictMath
-----------------------
StrictMath类包含执行基本数值运算的方法，如初等指数、对数、平方根和三角函数。
其中许多方法(native)被Math类同名方法直接调用。
也有许多方法的实现是直接调用Math类同名方法。
StrictMath可以保障在不同的平台上运行都得到相同的结果（一个完全可预测的结果）。


### 简要代码
```java
package java.lang;
import ...
/**
 * StrictMath类包含执行基本数值运算的方法，如初等指数、对数、平方根和三角函数。
 */
public final class StrictMath {
    /** 禁止实例化该类 */
    private StrictMath() {}
    
    public static final double E = 2.7182818284590452354;
    public static final double PI = 3.14159265358979323846;
    
    public static native double sin(double a);
    public static native double cos(double a);
    public static native double tan(double a);
    public static native double asin(double a);
    public static native double acos(double a);
    public static native double atan(double a);
    public static strictfp double toRadians(double angdeg) {...}
    public static strictfp double toDegrees(double angrad) {...}
    
    public static native double exp(double a);
    public static native double log(double a);
    public static native double log10(double a);
    public static native double sqrt(double a);
    public static native double cbrt(double a);
    
    public static native double IEEEremainder(double f1, double f2);
    
    public static double ceil(double a) {...}
    public static double floor(double a) {...}
    private static double floorOrCeil(double a,
                                      double negativeBoundary,
                                      double positiveBoundary,
                                      double sign) {...}
    
    public static double rint(double a) {...}
    
    public static native double atan2(double y, double x);
    public static native double pow(double a, double b);
    
    public static int round(float a) {
        return Math.round(a);
    }
    public static long round(double a) {
        return Math.round(a);
    }
    private static final class RandomNumberGeneratorHolder {
        static final Random randomNumberGenerator = new Random();
    }
    public static double random() {
        return RandomNumberGeneratorHolder.randomNumberGenerator.nextDouble();
    }
    
    public static int addExact(int x, int y) {
        return Math.addExact(x, y);
    }
    public static long addExact(long x, long y) {
        return Math.addExact(x, y);
    }
    public static int subtractExact(int x, int y) {
        return Math.subtractExact(x, y);
    }
    public static long subtractExact(long x, long y) {
        return Math.subtractExact(x, y);
    }
    public static int multiplyExact(int x, int y) {
        return Math.multiplyExact(x, y);
    }
    public static long multiplyExact(long x, long y) {
        return Math.multiplyExact(x, y);
    }
    public static int toIntExact(long value) {
        return Math.toIntExact(value);
    }
    public static int floorDiv(int x, int y) {
        return Math.floorDiv(x, y);
    }
    public static long floorDiv(long x, long y) {
        return Math.floorDiv(x, y);
    }
    public static int floorMod(int x, int y) {
        return Math.floorMod(x , y);
    }
    public static long floorMod(long x, long y) {
        return Math.floorMod(x, y);
    }
    public static int abs(int a) {
        return Math.abs(a);
    }
    public static float abs(float a) {
        return Math.abs(a);
    }
    public static double abs(double a) {
        return Math.abs(a);
    }
    public static int max(int a, int b) {
        return Math.max(a, b);
    }
    public static long max(long a, long b) {
        return Math.max(a, b);
    }
    public static float max(float a, float b) {
        return Math.max(a, b);
    }
    public static double max(double a, double b) {
        return Math.max(a, b);
    }
    public static int min(int a, int b) {
        return Math.min(a, b);
    }
    public static long min(long a, long b) {
        return Math.min(a, b);
    }
    public static float min(float a, float b) {
        return Math.min(a, b);
    }
    public static double min(double a, double b) {
        return Math.min(a, b);
    }
    public static double ulp(double d) {
        return Math.ulp(d);
    }
    public static float ulp(float f) {
        return Math.ulp(f);
    }
    public static double signum(double d) {
        return Math.signum(d);
    }
    public static float signum(float f) {
        return Math.signum(f);
    }
    
    public static native double sinh(double x);
    public static native double cosh(double x);
    public static native double tanh(double x);
    public static native double hypot(double x, double y);
    public static native double expm1(double x);
    public static native double log1p(double x);
    
    public static double copySign(double magnitude, double sign) {
        return Math.copySign(magnitude, (Double.isNaN(sign)?1.0d:sign));
    }
    public static float copySign(float magnitude, float sign) {
        return Math.copySign(magnitude, (Float.isNaN(sign)?1.0f:sign));
    }
    public static int getExponent(float f) {
        return Math.getExponent(f);
    }
    public static int getExponent(double d) {
        return Math.getExponent(d);
    }
    public static double nextAfter(double start, double direction) {
        return Math.nextAfter(start, direction);
    }
    public static float nextAfter(float start, double direction) {
        return Math.nextAfter(start, direction);
    }
    public static double nextUp(double d) {
        return Math.nextUp(d);
    }
    public static float nextUp(float f) {
        return Math.nextUp(f);
    }
    public static double nextDown(double d) {
        return Math.nextDown(d);
    }
    public static float nextDown(float f) {
        return Math.nextDown(f);
    }
    public static double scalb(double d, int scaleFactor) {
        return Math.scalb(d, scaleFactor);
    }
    public static float scalb(float f, int scaleFactor) {
        return Math.scalb(f, scaleFactor);
    }
    
}
```