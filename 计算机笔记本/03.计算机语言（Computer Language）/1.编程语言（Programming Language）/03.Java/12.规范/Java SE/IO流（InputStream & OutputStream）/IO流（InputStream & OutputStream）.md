# IO流（InputStream & OutputStream）

## 一、IO流类的分类

Java的I/O操作类在java.io包下，大概有将近80个，这些类可以大概分成下面四个类型：

- 基于字节操作的I/O接口: InputStream和 OutputStream。（传输数据的数据格式）
- 基于字符操作的I/O接口: Writer和 Reader。（传输数据的数据格式）
- 基于磁盘操作的1/O接口:File。（传输数据的方式）
- 基于网络操作的I/O接口: Socket。（传输数据的方式）

![IO流](Pictrures\iostream.png)

**前两组主要是传输数据的数据格式，后两组主要是传输数据的方式**，虽然Socket类并不在java.io包下，但是我仍然把它们划分在一起，因为我个人认为IO的核心问题要么是数据格式影响I/O操作，要么是传输方式影响IО操作，也就是将什么样的数据写到什么地方的问题。IO 只是人与机器或者机器与机器交互的手段，除了它们能够完成这个交互功能外，我们关注的就是如何提高它的运行效率了，**而数据格式和传输方式是影响效率最关键的因素**。

## 二、经常使用的16个IO流类

### 文件专属

- java.io.FileInputStream
- java.io.FileOutputStream
- java.io.FileReader
- jvav.io.FileWriter

### 转换流（将字节流转换成字符流）

- java.io.InputStreamReader
- java.io.OutputStreamWriter

### 缓冲流专属

- java.io.BufferedRead
- java.io.BufferedWriter
- java.io.BufferedInputStream
- java.io.BufferesOutputStream

### 数据流专属

- java.io.DataInputStream
- java.io.DataOutputStream

### 标准输出流

- java.io.PrintWriter
- java.io.PrintStream

### 对象专属流

- java.io.ObjectInputStream
  - //序列化一个对象，并将它发送到输出流
    public final void writeObject(Object x) throws IOException
- java.io.ObjectOutputStream
  - //反序列化一个对象的方法
    public final Object readObject() throws IOException, ClassNotFoundException

## 三、字节流

Java中的字节流处理的最基本单位为单个字节，它通常用来处理二进制数据。Java中最基本的两个字节流类是InputStream和OutputStream，它们分别代表了组基本的输入字节流和输出字节流。InputStream类与OutputStream类均为抽象类，我们在实际使用中通常使用Java类库中提供的它们的一系列子类。

## 四、字符流

Java中的字符流处理的最基本的单元是Unicode码元(大小2字节)，它通常用来处理文本数据。所谓Unicode码元，也就是一个Unicode代码单元，范围是Ox0000~OxFFF。在以上范围内的每个数字都与一个字符相对应，Java中的String类型默认就把字符以Unicode规则编码而后存储在内存中。然而与存储在内存中不同，存储在磁盘上的数据通常有着各种各样的编码方式。使用不同的编码方式，相同的字符会有不同的二进制表示。实际上字符流是这样工作的:

- 输出字符流:把要写入文件的字符序列(实际上是Unicode码元序列)转为指定编码方式下的字节序列，然后再写入到文件中;
- 输入字符流:把要读取的字节序列按指定编码方式解码为相应字符序列(实际上是Unicode码元序列从)从而可以存在内存中。

## 五、以流的方式获取绝对路径

```java
//Xxx.java文件代码

//文件必须在src类的路径下

import java.io.InputStream;
import java.io.Reader;
import java.security.Key;
import java.util.Properties;

public class Xxx {
    public static void main(String[] args) throws Exception {
        //以流的形式返回
        InputStream inputStream = Thread.currentThread().getContextClassLoader().getResourceAsStream(Xxx.properties);
        Properties properties = new Properties();
        properties.load(Reader);
        //通过key获取value
        String className = properties.getProperty("key");
        System.out.println(Key);
    }
}

```

## 六、Java读取磁盘文件

![Java读取磁盘文件流程](Pictrues\Java从磁盘读取文件.png)

## 七、Java序列化

Java 序列化就是将一个对象转化成一串二进制表示的字节数组，通过保存或转移这些字节数据来达到持久化的目的。需要持久化，对象必须继承 java.io.Serializable 接口。反序列化则是相反的过程，将这个字节数组再重新构造成对象。我们知道反序列化时，必须有原始类作为模板，才能将这个对象还原，从这个过程我们可以猜测，序列化的数据并不像 class 文件那样保存类的完整的结构信息。

请注意，一个类的对象要想序列化成功，必须满足两个条件：

- 该类必须实现 java.io.Serializable 对象。

- **该类的所有属性必须是可序列化的。如果有一个属性不是可序列化的，则该属性必须注明是短暂的。**

### 序列化对象

ObjectOutputStream 类用来序列化一个对象，如下的SerializeDemo例子实例化了一个Employee对象，并将该对象序列化到一个文件中。该程序执行后，就创建了一个名为employee.ser文件。该程序没有任何输出，但是你可以通过代码研读来理解程序的作用。

**注意：** 当序列化一个对象到文件时， 按照Java的标准约定是给文件一个.ser扩展名。

```java
//SerializeDemo.java文件代码：

//运行时需要修改内容：
//1.【文件地址+文件名.ser】

import java.io.*;

public class SerializeDemo
{
   public static void main(String[] args)
   {
      Employee e = new Employee();
      e.name = "Reyan Ali";
      e.address = "Phokka Kuan, Ambehta Peer";
      e.SSN = 11122333;
      e.number = 101;
      try
      {
         FileOutputStream fileOut = new FileOutputStream("【文件地址+文件名.ser】");
         ObjectOutputStream out = new ObjectOutputStream(fileOut);
         out.writeObject(e);
         out.close();
         fileOut.close();
         System.out.printf("Serialized data is saved in 【文件地址+文件名.ser】");
      }catch(IOException i)
      {
          i.printStackTrace();
      }
   }
}

//Employee.java文件代码：

public class Employee implements java.io.Serializable
{
   public String name;
   public String address;
   public transient int SSN;
   public int number;
   public void mailCheck()
   {
      System.out.println("Mailing a check to " + name
                           + " " + address);
   }
}
```

> 输出结果：
>
> ```
> Serialized data is saved in 【文件地址+文件名.ser】
> ```
>
> 同时产生【文件地址+文件名.ser】文件

### 反序列化对象

**这里要注意以下要点：**

readObject() 方法中的try/catch代码块尝试捕获 ClassNotFoundException异常。对于JVM可以反序列化对象，它必须是能够找到字节码的类。如果JVM在反序列化对象的过程中找不到该类，则抛出一个 ClassNotFoundException异常。

注意，readObject()方法的返回值被转化成Employee引用。

当对象被序列化时，属性SSN的值为111222333，但是因为该属性是短暂的，该值没有被发送到输出流。所以反序列化后Employee对象的SSN属性为0。

```java
//DeserializeDemo.java文件代码

//运行时需要修改内容：
//1.【文件地址+文件名.ser】

import java.io.*;
public class DeserializeDemo
{
   public static void main(String[] args)
   {
      Employee e = null;
      try
      {
         FileInputStream fileIn = new FileInputStream("【文件地址+文件名.ser】");
         ObjectInputStream in = new ObjectInputStream(fileIn);
         e = (Employee) in.readObject();
         in.close();
         fileIn.close();
      }catch(IOException i)
      {
         i.printStackTrace();
         return;
      }catch(ClassNotFoundException c)
      {
         System.out.println("Employee class not found");
         c.printStackTrace();
         return;
      }
      System.out.println("Deserialized Employee...");
      System.out.println("Name: " + e.name);
      System.out.println("Address: " + e.address);
      System.out.println("SSN: " + e.SSN);
      System.out.println("Number: " + e.number);
    }
}
```

> 输出结果：
>
> ```
> Deserialized Employee...
> Name: Reyan Ali
> Address: Phokka Kuan, Ambehta Peer
> SSN: 0
> Number: 101
> 
> ```
>

### 序列化后文件二进制数据分析

第一部分是序列化文件头。

第二部分是要序列化的类的描述，在这里是Serialize类。

第三部分是对象中各个属性项的描述。

第四部分输出该对象的父类信息描述，这里没有父类，如果有，数据格式与第二部分一样。

第五部分输出对象的属性项的实际值，如果属性项是一个对象，那么这里还将序列化这个对象，规则和第二部分一样。

虽然Java 的序列化能够保证对象状态的持久保存，但是遇到一些对象结构复杂的情况还是比较难处理的，下面是一些复杂对象情况的总结。

- 当父类继承Serializable接口，所有子类都可以被序列化。
- 子类实现了Serializable接口，父类没有，父类中的属性不能序列化(不报错，数据会丢失)，但是子类中属性仍能正确序列化。
- 如果序列化的属性是对象，这个对象也必须实现Serializable接口，否则会报错。在反序列化时，如果对象的属性有修改或删减，修改的部分属性会丢失，但不会报错。
- 在反序列化时，如果serialVersionUID被修改，那么反序列化时会失败。

在纯Java环境下，Java序列化能够很好地工作，但是在多语言环境下，用Java序列化存储后，很难用其他语言来还原出结果，在这种情况下，还是要尽量存储通用数据结构，如JSON或者XML结构数据，当前也有比较好的序列化工具，如 Google的 protobuf等。

