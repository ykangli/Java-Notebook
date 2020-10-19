# System类

System类不能创建对象，因为构造函数是用private修饰 
```java
public final class System {
    private static native void registerNatives();
    static {
        registerNatives();
    }

    /** Don't let anyone instantiate this class */
    private System() {
    }
    
    ...
```

System方法：
  
  static void exit(int status) // 终止当前正在运行的 Java 虚拟机。
  
  static long currentTimeMillis() //返回以毫秒为单位的当前时间。 
  
```java
        for (int i = 0; i < desk.length; i++) {
            System.out.println(desk[i]);
        }

        long start = System.currentTimeMillis();
        for (int i = 0; i < 100000; i++) {
            System.out.println(i);
        }
        long end = System.currentTimeMillis();

        System.out.println(end - start);
```
  
  static void gc()  //运行垃圾回收器
  
  static void arraycopy(Object src, int srcPos, Object dest, int destPos, int length)  //从指定源数组中复制一个数组，复制从指定的位置开始，到目标数组的指定位置结束 
  
```java
  public class SystemDemo {
    public static void main(String[] args) {
        int[] src = {1, 2, 3, 4, 5};
        int[] desk = {6, 7, 8, 9, 0};

        System.arraycopy(src,2,desk,0,2);

        for (int i = 0; i < desk.length; i++) {
            System.out.println(desk[i]);
        }
    }
}
```
         
           
