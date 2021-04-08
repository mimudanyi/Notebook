# **异常（Exception）**

## 一、异常发生的情况

- 用户输入了非法数据。
- 要打开的文件不存在。
- 网络通信时连接中断，或者JVM内存溢出。

## 二、异常的类型

- 检查性异常：最具代表的检查性异常是用户错误或问题引起的异常，这是程序员无法预见的。例如要打开一个不存在文件时，一个异常就发生了，这些异常在编译时不能被简单地忽略。
- 运行时异常： 运行时异常是可能被程序员避免的异常。与检查性异常相反，运行时异常可以在编译时被忽略。
- 错误： 错误不是异常，而是脱离程序员控制的问题。错误在代码中通常被忽略。例如，当栈溢出时，一个错误就发生了，它们在编译也检查不到的。

## 三、Exception中的方法：

- toString() ：给出异常的类型与性质。
- getMessage()：取得异常描述信息，输出错误的性质。
- printStackTrace()：取得异常的堆栈信息（比较适合于程序的调试阶段），指出异常的类型、性质、栈层次及出现在程序中的位置。

## 四、自定义异常类：

```java
public class MyException extends Exception/RunTimeException{
				public MyException(){
				}

				public MyException(String s){
					super(s);
				}
}
```

## 五、异常的分类

- Exception

  - Error

    - **VirtualMachineError**
    - **IOError**

  - 运行时异常和编译时异常都是发生在运行阶段，编译阶段异常是不会发生的，只有程序运行阶段才会new对象

  - ExcetionSubClass（编译时异常,受检异常Checked Exception，受控异常）

    - 只有java语言提供了Checked异常，Java认为Checked异常都是可以被处理的异常，所以Java程序必须显示处理Checked异常。如果程序没有处理Checked异常，该程序在编译时就会发生错误无法编译。这体现了Java的设计哲学：没有完善错误处理的代码根本没有机会被执行。

    - 对Checked异常处理方法有两种

      1 当前方法知道如何处理该异常，则用try...catch块来处理该异常。

      2 当前方法不知道如何处理，则在定义该方法是声明抛出该异常。

    - **Java.lang.ClassNotFoundException**

    - **Java.lang.NoSuchMetodException**

    - **java.io.IOException**

  - RuntimeException（运行时异常,未受检异常Unchecked Exception，非受控异常）

    - Runtime如除数是0和数组下标越界等，其产生频繁，处理麻烦，若显示申明或者捕获将会对程序的可读性和运行效率影响很大。所以由系统自动检测并将它们交给缺省的异常处理程序。当然如果你有处理要求也可以显示捕获它们。
    - **Java.lang.ArithmeticException**
    - **Java.lang.ArrayStoreExcetpion**
    - **Java.lang.ClassCastException**
    - **Java.lang.IndexOutOfBoundsException**
    - **Java.lang.NullPointerException**

## 注意：

方法重写是只能抛出更少更小的编译型异常。