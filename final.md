#final关键字

final，即为最后的意思，具体使用方法：

1.修饰类，该修饰类不能被继承

2.修饰方法，该方法不能被覆盖重写

3.final和abstract关键字必然不能同时使用，因为abstract方法所在的类一定是抽象类，abstract方法一定要被子类覆盖重写，而final方法是最后的方法，不能被重写覆盖

4.修饰局部变量

注意final的不可变含义：
  
  对于基本变量类型来说，不可变指的是变量中的数值不可变
  
  对于引用类型来说，不可变指的是变量中的地址不可变，因为引用类型变量中存储的是地址值，可利用setter改变其变量内容
  ```java
  package demo03;

public class Student {
    final int num = 10;
    String name;

    public Student(String name) {
        this.name = name;
    }

    public void getNum() {
        System.out.println(num);
    }

    public void getName() {
        System.out.println(name);
    }

    public void setName(String name) {
        this.name = name;
    }

    public static void main(String[] args) {
        final Student student = new Student("Allen");
//        student = new Student("aaa");// 错误写法，final不能变改变
        student.getName();
        student.setName("Allennnnnnnn");
        student.getName();
    }
}
```
  
