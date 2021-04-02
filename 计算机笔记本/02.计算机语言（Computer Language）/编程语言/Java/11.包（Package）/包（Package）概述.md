#  包（Package）

## 一、定义

- 一种命名空间。
- 在Java虚拟机执行的时候，JVM只看完整类名，因此，只要包名不同，类就不同。包可以是多层结构，用.隔开。例如：java.util。要特别注意：包没有父子关系。java.util和java.util.zip是不同的包，两者没有任何继承关系。
- 包作用域： 位于同一个包的类，可以访问包作用域的字段和方法。不用public、protected、private修饰的字段和方法就是包作用域。
- 如果一个源文件中没有使用包声明，那么其中的类，函数，枚举，注释等将被放在一个无名的包（unnamed package）中。
- 通常，一个公司使用它互联网域名的颠倒形式来作为它的包名.例如：互联网域名是 [runoob.com](http://runoob.com)，所有的包名都以 com.runoob 开头。包名中的每一个部分对应一个子目录。

## 二、导入（import）

java.lang.* 这个包的类不用导入，默认自动导入。

导入另一个包中的类时有**三种方法**：

### 第一种

直接写出完整类名

```java
// Person.javapackage ming;
public class Person {
		public void run() {
				mr.jun.Arrays arrays = new mr.jun.Arrays();
		}
}
```

### 第二种

在写import的时候，可以使用*，表示把这个包下面的所有class都导入进来（但不包括子包的class）：我们一般不推荐这种写法，因为在导入了多个包后，很难看出Arrays类属于哪个包。

```java
// Person.java
package ming;
// 导入mr.jun包的所有class:
import mr.jun.*;

public class Person {
		public void run() {
				Arrays arrays = new Arrays();
		}
}
```

### 第三种

import static的语法，它可以导入可以导入一个类的静态字段和静态方法：import static很少使

```java
package main;
// 导入System类的所有静态字段和静态方法:
import static java.lang.System.*;
public class Main {
public static void main(String[] args) {
// 相当于调用System.out.println(…)
out.println("Hello, world!");
}
}
```