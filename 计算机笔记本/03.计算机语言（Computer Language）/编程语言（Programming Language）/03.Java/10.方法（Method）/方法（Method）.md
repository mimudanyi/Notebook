# 方法（Method）

## 一、定义

方法就是行为，一个类可以有很多方法。逻辑运算、数据修改以及所有动作都是在方法中完成的。

```java
【修饰符】 【返回值类型】 【方法名】(【参数类型】 【参数名】){
	//Code;
	return 【返回值】;
}
```

![方法定义](Pictrues\方法定义.jpg)

![方法定义](Pictrues\方法定义.png)

### 修饰符

修饰符，这是可选的，告诉编译器如何调用该方法。定义了该方法的访问类型。

###返回值类型 

方法可能会返回值。returnValueType 是方法返回值的数据类型。有些方法执行所需的操作，但没有返回值。在这种情况下，returnValueType 是关键字void。

### 方法名

是方法的实际名称。方法名和参数表共同构成方法签名。

### 参数类型

参数像是一个占位符。当方法被调用时，传递值给参数。这个值被称为实参或变量。参数列表是指方法的参数类型、顺序和参数的个数。参数是可选的，方法可以不包含任何参数。

#### 命令行参数

有时候你希望运行一个程序时候再传递给它消息。这要靠传递命令行参数给main()函数实现。命令行参数是在执行程序时候紧跟在程序名字后面的信息。

```java
//CommandLine.java 文件代码：

public class CommandLine {
    public static void main(String args[]){
        for(int i=0; i<args.length; i++){         
            System.out.println("args[" + i + "]: " + args[i]);
        }
    }
}
```

>如下所示，运行这个程序：
>
>```
>$ javac CommandLine.java 
>$ java CommandLine this is a command line 200 -100
>args[0]: this
>args[1]: is
>args[2]: a
>args[3]: command
>args[4]: line
>args[5]: 200
>args[6]: -100
>```
>
>

#### 可变参数

JDK 1.5 开始，Java支持传递同类型的可变参数给一个方法。方法的可变参数的声明如下所示：

```java
typeName... parameterName
```

在方法声明中，在指定参数类型后加一个省略号(...) 。一个方法中只能指定一个可变参数，它必须是方法的最后一个参数。任何普通的参数必须在它之前声明。

```java
//VarargsDemo.java 文件代码：

public class VarargsDemo {
    public static void main(String args[]) {
        // 调用可变参数的方法
        printMax(34, 3, 3, 2, 56.5);
        printMax(new double[]{1, 2, 3});
    }
 
    public static void printMax( double... numbers) {
        if (numbers.length == 0) {
            System.out.println("No argument passed");
            return;
        }
 
        double result = numbers[0];
 
        for (int i = 1; i <  numbers.length; i++){
            if (numbers[i] >  result) {
                result = numbers[i];
            }
        }
        System.out.println("The max value is " + result);
    }
}
```

>以上实例编译运行结果如下：
>
>```
>The max value is 56.5
>The max value is 3.0
>```

### 方法体

方法体包含具体的语句，定义该方法的功能。

## 二、方法种类

### 构造方法

- 创建实例的时候，实际上是通过构造方法来初始化实例的。
- 构造方法的名称就是类名
- 构造方法的参数没有限制，在方法内部，也可以编写任意语句。
- 和普通方法相比，构造方法没有返回值（也没有void）。
- 调用构造方法，必须用new操作符。
- 一个类可以有多个构造方法。
- 一个类没有定义构造方法，编译器会自动为我们生成一个默认构造方法，它没有参数，也没有执行语句，如

```java
class Person{
	public Person(){
	}
}
```

### 实例方法

### 静态方法

### 抽象方法

如果你想设计这样一个类，该类包含一个特别的成员方法，该方法的具体实现由它的子类确定，那么你可以在父类中声明该方法为抽象方法。

Abstract 关键字同样可以用来声明抽象方法，抽象方法只包含一个方法名，而没有方法体。

抽象方法没有定义，方法名后面直接跟一个分号，而不是花括号。

```java
public abstract class Employee
{
   private String name;
   private String address;
   private int number;
   
   public abstract double computePay();
   
   //其余代码
}
```

## 三、方法调用

当程序调用一个方法时，程序的控制权交给了被调用的方法。当被调用方法的返回语句执行或者到达方法体闭括号时候交还控制权给程序。

Java 支持两种调用方法的方式，根据方法是否返回值来选择。

1. 当方法返回一个值的时候，方法调用通常被当做一个值。例如：

```java
int larger = max(30, 40);
```

2. 如果方法返回值是void，方法调用一定是一条语句。例如，方法println返回void。下面的调用是个语句：

```java
System.out.println("欢迎访问菜鸟教程！");
```

## 三、方法重载（Overload）

在同一个类中，这种方法名相同，但各自的参数不同，称为方法重载。方法重载的返回值类型通常都是相同的，也可以不同。

```java
//Xxx.java文件代码：

public class Xxx {
    public void hello() {
        System.out.println("Hello, world!");
    }

    public void hello(String name) {
        System.out.println("Hello, " + name + "!");
    }

    public void hello(String name, int age) {
        if (age < 18) {
            System.out.println("Hi, " + name + "!");
        } else {
            System.out.println("Hello, " + name + "!");
        }
    }
}
```

## 四、方法重写（Override）

返回参数，内置类型不可变，引用类型可以向下转型。

**@Override**：伪代码，表示重新(当然不写也可以)，不过写上有如下好处: 1、可以当注释用,方便阅读； 2、编译器可以给你验证@Override下面的方法名是否是你父类中所有的，如果没有则报错。例如，你如果没写@Override，而你下面的方法名又写错了，这时你的编译器是可以编译通过的，因为编译器以为这个方法是你的子类中自己增加的方法。

## 五、方法递归

方法内调用自己。

## 六、可变参数

可变参数，即可向函数传递 0 个或多个参数，一个函数至多只能有一个可变参数，且可变参数为最后一个参数。对于可变参数，编译器会将其转型为一个数组，故在函数内部，可变参数名即可看作数组名。如

```java
void function(String... args);
void function(String [] args);
```

这两个方法的命名是相等的，不能作为方法的重载。

用类型…表示，如：

```java
class Group {

		private String[] names;

		public void setNames(String... names) {
				this.names = names;
		}
}
```

## 七、注意

- 方法体中的语句一定是自上而下的执行的。