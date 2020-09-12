数组可以存储任何数据类型，包括但不限于整形，字符串...

其中存储对象比较特殊，即对象数组。利用数组存储对象，其实在数组中存储的是对象的地址值。

```java
package demo02;

import java.util.Random;

public class DemoMethod {

    public static void main(String[] args) {
//        int[] array = new int[5];//一般整型数组的定义

        Person2[] array = new Person2[3];//定义对象数组

        Person2 one = new Person2("Allen",22);
        Person2 two = new Person2("Kobe",32);
        Person2 three = new Person2("Jordon",42);

        array[0] = one;//数组中存储对象
        array[1] = two;
        array[2] = three;

        System.out.println(array[0]);
        System.out.println(array[1]);
        System.out.println(array[2]);

        System.out.println(array[2].getName());
        System.out.println(array[2].getAge());

    }
}
```
  
`数组缺点：一旦创建，数组的长度固定。`  由此引出ArrayList集合这样的数据类型

`基本概念：引用类型和基本类型`

基本类型：int，long，short，float，double等

引用类型：类、接口类型、数组类型、枚举类型、注解类型

二者区别：

    基本数据类型在被创建时，在栈上给其划分一块内存，将数值直接存储在栈上。
    
    引用数据类型在被创建时，首先要在 栈 上给其引用（句柄）分配一块内存，而对象的具体信息都存储在 堆内存 上，然后由栈上面的引用指向堆中对象的地址。

`ArrayList`   

对于ArrayList来说，< >代表泛型。泛型即装在集合中的所有元素都是统一的类型。左边< >不可省略，对于JDK 1.8以上右侧< >内容可以省略不写。

泛型都是引用类型，而不能是基本类型。原因：基本类型的内容都是直接存储在栈当中，而引用类型是在栈中存储对象地址，再由这地址指向堆中具体的内容。

要在ArrayList存储基本类型时，必须使用`包装类`。

当直接打印ArrayList时，打印的是集合里面的内容，与数组有所不同，数组打印出的是地址。
```java
package demo02;

import java.util.ArrayList;
import java.util.Scanner;

public class DemoMethod3 {

    public static void main(String[] args) {
        int[] array = new int[3];
        ArrayList<String> list = new ArrayList<>();

        System.out.println(array);
        System.out.println(list);
    }

}

结果为： 
[I@723279cf
[]
```

常用的list方法：
    list.add(E);  // E代表泛型
    list.get(index i);  // 获得index位置的内容
    list.remove(index i); // 删除index位置的内容
    
包装类：可利用来在ArrayList中存储基本数据类型

例：
```java
package demo02;

import java.util.ArrayList;
import java.util.Random;

public class DemoMethod4 {
    public static void main(String[] args) {
    
        ArrayList<Integer> list = new ArrayList<>();
        Random r = new Random();
        
        //产生6个随机数，并存储在集合
        for (int i = 0; i < 6; i++) {
            int random = r.nextInt(33) + 1;
            list.add(random);
        }
        
        //遍历集合
        for (int i = 0; i < list.size(); i++) {
            System.out.println(list.get(i));
        }
    }
}
```
`集合也可以当作方法的返回值：`

例：筛选集合中的随机数（将随机产生的数字存储在大集合中，筛选出偶数将其放置在小集合中）

```java
package demo02;

import java.util.ArrayList;
import java.util.Random;

public class SelectNumber {

    //将大集合中的偶数添加到小集合中
    public static ArrayList<Integer> getSmaliList(ArrayList<Integer> bigList) {
        ArrayList<Integer> smallList = new ArrayList<>();
        for (int i = 0; i < bigList.size(); i++) {
            int num = bigList.get(i);
            if(num % 2 == 0) {
                smallList.add(num);
            }
        }
        return smallList;
    }

    public static void main(String[] args) {
        ArrayList<Integer> bigList = new ArrayList<>();
        Random random = new Random();

        //随机产生0-30范围内的20个数字
        for (int i = 0; i < 20; i++) {
            int r = random.nextInt(30) + 1;
            bigList.add(r);
        }

        ArrayList<Integer> smallList = getSmaliList(bigList);
        
        for (int i = 0; i < smallList.size(); i++) {
            System.out.println(smallList.get(i));
        }
    }
}
```













