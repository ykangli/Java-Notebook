# -
记录java自学过程，此外将有用及重要的知识点整理记录

`@Override`<br>
1）Override即为方法重写，又叫覆写，子类与父类的方法返回类型一样、方法名称一样，参数一样，这样我们说子类与父类的方法构成了重写关系。
2）方法重写（Override）与方法重载（Overload）之间的关系：重载发生在同一个类内部的两个方法或多个方法。重写发生在父类和子类之间。

具体代码实例：<br>
```
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
3) 在定义一个类的时候，如果没有显式指定该类的父类，那么该类就会继承于java.lang.Object(JDK提供的一个类，Object类是Java中所有类直接或间接父类)。下面举个例子：

``` 
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
