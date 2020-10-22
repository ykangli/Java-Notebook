# Java

记录java自学过程，此外将有用及重要的知识点整理记录

`@Override`<br>
1）Override即为`方法重写`，又叫`覆写`，子类与父类的方法返回类型一样、方法名称一样，参数一样，这样我们说`子类与父类`的方法构成了重写关系。<br>
2）方法重写（Override）与方法重载（Overload）之间的关系：重载发生在`同一个类内部`的两个方法或多个方法。重写发生在`父类和子类`之间。<br>

`方法重写的注意事项:`

1.重写的方法必须要和父类一模一样(包括返回值类型,方法名,参数列表)

2.重写的方法可以使用@Override注解来标识

3.子类中重写的方法的访问权限不能低于父类中方法的访问权限

权限修饰符 : private  <   默认(什么都不写)  <   protected  < public

override机制的作用：没有override，子类一旦继承父类的方法就不能进行修改。当子类希望稍微提供一点不一样的功能是只能全部重写。

具体代码实例：<br>
```Java
public class InheritenceTest {
    public static void main(String[] args) {
        Dog dog = new Dog();
        dog.run();
    }
}
 
class Animal {
    public void run() {
        System.out.println("animal is running");
    }
}
 
class Dog extends Animal {
    public void run() {
        System.out.println("Dog is running");
        super.run();//调用父类的run方法
    }
}
输出结果：
Dog is running
animal is running
```

`多态`     包括`操作符的多态`和`类的多态`



在定义一个类的时候，如果没有显式指定该类的父类，那么该类就会继承于java.lang.Object(JDK提供的一个类，Object类是Java中所有类直接或间接父类)。下面举个例子：

``` Java
public class InheritenceTest {
    public static void main(String[] args) {
        Son son = new Son();
    }
}
 
class Grandpa {
    public Grandpa() {
        System.out.println("grandpa");
    }
}
 
class Father extends Grandpa {
    public Father() {
        System.out.println("father");
    }
}
 
class Son extends Father {
    public Son() {
        System.out.println("son");
    }
}
输出结果：
grandpa
father
son
```







