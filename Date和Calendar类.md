# Date类

Date表示日期对象:

  Date类主要的作用是提供了日期对象和毫秒值之间的转换，日期不能进行数学计算，但是毫秒值可以 
  
日期转换为毫秒值：

  Date对象方法getTime()   new Date.getTime()
  
毫秒值转换为日期：

  Date对象方法setTime(long num)   new Date.setTime(long num)
  
日期格式化：java.text.Format 是一个abstract修饰的抽象类，创建它的子类SimpleDateFormat

将日期对象转换为字符串:
  
 ```java
SimpleDateFormat sdf = new SimpleDateFormat("yyyy年MM月dd日"); //构造方法，构造给定的类型

String format = sdf.format(new Date());

System.out.println(format);
```

将字符串转化为日期对象：

```java
String str = "2020-10-1";

SimpleDateFormat sdf1 = new SimpleDateFormat("yyyy-MM-dd"); //构造方法，构造给定的类型，必须与给定的字符串形式一致

Date parse = sdf1.parse(str);

System.out.println(parse);
```

Calendar类：是抽象类，但是抽象类中定义静态方法，直接调用了 static getInstance(),方法返回值是日历类的子类对象，注意

若要用变量必须用父类 Calendar接收   

```java
package demo03;

import java.util.Calendar;

public class CalendarDemo {
    public static void main(String[] args) {
        Calendar calendar1 = Calendar.getInstance(); //使用默认时区和语言环境获得一个日历
        int year = calendar1.get(Calendar.YEAR); //get()返回给定日历字段的值
        System.out.println(year);

        System.out.println("----------------");

        Calendar calendar2 = Calendar.getInstance(); //使用默认时区和语言环境获得一个日历
        calendar2.set(Calendar.MONDAY, 3);
        int month = calendar2.get(Calendar.MONTH);  //修改日历（这里为修改月份）
        System.out.println(month);

        System.out.println("----------------");

        Calendar calendar3 = Calendar.getInstance(); //使用默认时区和语言环境获得一个日历
        calendar3.add(Calendar.DAY_OF_MONTH, 300);  //  向后偏移300天
        System.out.println(calendar3.get(Calendar.YEAR) + "年" +
                calendar3.get(Calendar.MONTH) + "月" + calendar3.get(Calendar.DAY_OF_MONTH) + "日");
    }
}
```



  














  
