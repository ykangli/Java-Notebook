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

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------
`异常`<br>
下面的例子为利用java打开`d:/LOL.exe`,如果不做任何处理就会报错，Java会强制你考虑两种情况:该文件存在与否<br>

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









