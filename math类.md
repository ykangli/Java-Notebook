# Math

大数运算和高精度运算: BigInteger,BIgDecimal

   BigInteger add(BigInteger val)...
   
 ```java
 public class BigIntegerDemo {
    public static void main(String[] args) {
        method1();
        method2();
    }

    public static void method1() {
        BigInteger b1 = new BigInteger("1223445556");   //解决数字超出界限的问题
        BigInteger b2 = new BigInteger("1223445556");
        BigInteger b = b1.add(b2);
        System.out.println(b);
    }

    public static void method2() {
        BigDecimal a1 = new BigDecimal("12.44");
        BigDecimal a2 = new BigDecimal("122.44");
        BigDecimal a = a2.divide(a1,2,RoundingMode.FLOOR);
        System.out.println(a);
    }
}
```

