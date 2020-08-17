# Java

记录java自学过程，此外将有用及重要的知识点整理记录

`@Override`<br>
1）Override即为`方法重写`，又叫`覆写`，子类与父类的方法返回类型一样、方法名称一样，参数一样，这样我们说`子类与父类`的方法构成了重写关系。<br>
2）方法重写（Override）与方法重载（Overload）之间的关系：重载发生在`同一个类内部`的两个方法或多个方法。重写发生在`父类和子类`之间。<br>

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
在定义一个类的时候，如果没有显式指定该类的父类，那么该类就会继承于java.lang.Object(JDK提供的一个类，Object类是Java中所有类直接或间接父类)。下面举个例子：

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

`对象转型：`
类型转换：指的是引用类型和对象类型不一致的情况下的转换问题。通常情况下，引用类型和对象类型是一样的

1.所有的子类转换为父类，都是说得通的。
2.没有继承关系的两个类，互相转换，一定会失败

```
package charactor;
 
public class Hero {
    public String name;
    protected float hp;
     
    public static void main(String[] args) {
         
        Hero h = new Hero();
         
        ADHero ad = new ADHero();
         
        //类型转换指的是把一个引用所指向的对象的类型，转换为另一个引用的类型
         
        //把ad引用所指向的对象的类型是ADHero
        //h引用的类型是Hero
        //把ADHero当做Hero使用，一定可以
         
        h = ad;
         
    }
}
```
`接口:` 用来描述类应该做什么。一个类可以有多个接口。
例如：以下例子就是表明ADHero这个类的功能

```
package charactor;
 
public class ADHero extends Hero implements AD{
 
    @Override
    public void physicAttack() {
        System.out.println("进行物理攻击");
    }
 
}
```






-----------------------------------------------------------------------------------------------------------------------------------------------------------------------
`异常` 导致程序的正常流程被中断的事件，叫做异常<br>

异常分为检查型异常(CheckedException，也叫可查异常)，非检查型异常(Error和RuntimeException，也叫不可查异常)以及错误(Errror)。RuntimeException包括数组越界，访问null指针，错误的强制转换；<br>

出现该类异常，一定是自己的问题。<br>

检查型异常(CheckedException): 如果不处理，编译器，就不让你通过

非检查型异常(Error和RuntimeException): 不是必须进行try catch的异常

编译器将检查你是否为所有的检查型异常提供了异常处理器<br>

下面的例子为利用java打开`d:/LOL.exe`,如果不做任何处理就会报错，Java编译器会强制你考虑两种情况:该文件存在与否<br>

`设计的面试问题：`<br>
运行时异常与非运行时异常的区别：
运行时异常是不可查异常，不需要进行显式的捕捉，但也可捕捉。
非运行时异常是可查异常，必须进行显式的捕捉，或者抛出

可查异常

`Java规定：` 对于可查异常必须捕捉、或者声明抛出。允许忽略不可查的RuntimeException和Error。Error也是可以catch的
```
package practice;

import java.io.File;
import java.io.FileInputStream;

public class Exception {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		File f= new File("d:/LOL.exe");
        
        //试图打开文件LOL.exe，会抛出FileNotFoundException，如果不处理该异常，就会有编译错误
        new FileInputStream(f);
	}
}
```

因此强制考虑处理异常：<br>
1）利用try-catch<br>
```
package practice;

import java.io.File;
import java.io.FileInputStream;
import java.io.FileNotFoundException;

public class Exception {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		File f= new File("d:/LOL.exe");
        
        //试图打开文件LOL.exe，会抛出FileNotFoundException，如果不处理该异常，就会有编译错误
        
        try{
            System.out.println("试图打开 d:/LOL.exe");
            new FileInputStream(f);
            System.out.println("成功打开");
        }
        catch(FileNotFoundException e){
            System.out.println("d:/LOL.exe不存在");
            e.printStackTrace();
        }
	}
}

编译结果：
试图打开 d:/LOL.exe
d:/LOL.exe不存在
java.io.FileNotFoundException: d:\LOL.exe (系统找不到指定的文件。)
	at java.base/java.io.FileInputStream.open0(Native Method)
	at java.base/java.io.FileInputStream.open(FileInputStream.java:213)
	at java.base/java.io.FileInputStream.<init>(FileInputStream.java:155)
	at practice.Exception.main(Exception.java:17)
```
<br>
2)使用异常的父类进行catch<br>
FileNotFoundException是`Exception`的子类，使用Exception也可以catch住FileNotFoundException

```
package exception;
  
import java.io.File;
import java.io.FileInputStream;
import java.io.FileNotFoundException;
  
public class TestException {
  
    public static void main(String[] args) {
          
        File f= new File("d:/LOL.exe");
          
        try{
            System.out.println("试图打开 d:/LOL.exe");
            new FileInputStream(f);
            System.out.println("成功打开");
        }
         
        catch(Exception e){
            System.out.println("d:/LOL.exe不存在");
            e.printStackTrace();
        }
          
    }
}
```
3)多异常捕捉<br>
可能存在多个异常，如文件异常和解析异常，因此可使用多个catch
```
public class TestException {

	public static void main(String[] args) throws FileNotFoundException {
		// TODO Auto-generated method stub
        File f = new File("d:/LOL.exe");
        
        try {
            System.out.println("试图打开 d:/LOL2.exe");
            new FileInputStream(f);
            System.out.println("成功打开");
            SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd");
            Date d = sdf.parse("2016-06-03");
        } catch (FileNotFoundException e) {
            System.out.println("d:/LOL.exe不存在");
            e.printStackTrace();
        } catch (ParseException e) {
            System.out.println("日期格式解析错误");
            e.printStackTrace();
        }
	}
}
```
此外还可将多个异常放在同一个catch里面，可用 `ininstanceof` 进行判断具体的异常类型
```
public class TestException {
 
    public static void main(String[] args) {
 
        File f = new File("d:/LOL.exe");
 
        try {
            System.out.println("试图打开 d:/LOL.exe");
            new FileInputStream(f);
            System.out.println("成功打开");
            SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd");
            Date d = sdf.parse("2016-06-03");
        } catch (FileNotFoundException | ParseException e) {
            if (e instanceof FileNotFoundException)
                System.out.println("d:/LOL.exe不存在");
            if (e instanceof ParseException)
                System.out.println("日期格式解析错误");
 
            e.printStackTrace();
        }
 
    }
}
```
`finally` 无论异常与否，finally都会被调用

`throws` 抛出异常，一般利用函数调用
```
public class TestException {
 
    public static void main(String[] args) {
        method1();
 
    }
 
    private static void method1() {
        try {
            method2();
        } catch (FileNotFoundException e) {
            // TODO Auto-generated catch block
            e.printStackTrace();
        }
 
    }
 
    private static void method2() throws FileNotFoundException {
 
        File f = new File("d:/LOL.exe");
 
        System.out.println("试图打开 d:/LOL.exe");
        new FileInputStream(f);
        System.out.println("成功打开");
 
    }
}
```
此例中，method2()抛出异常给method1()，由method1()的try和catch来处理异常

抛出异常：
`throws与throw的区别`
1. throws 出现在方法声明上，而throw通常都出现在方法体内。
2. throws 表示出现异常的一种可能性，并不一定会发生这些异常；throw则是抛出了异常，执行throw则一定抛出了某个异常对象。

`Throwable` Exception和Error都继承了该类

![Throwable类](https://github.com/ykangli/-/blob/master/742.png)

创建异常：







