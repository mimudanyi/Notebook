# Java概述



## Java 介绍

Java 语言介于编译型语言和解释型语言之间。编译型语言如C、C++，代码是直接编译成机器码执行，但是不同的平台（x86、ARM等）CPU的指令集不同，因此，需要编译出每一种平台的对应机器码。解释型语言如Python、Ruby没有这个问题，可以由解释器直接加载源码然后运行，代价是运行效率太低。而Java是将代码编译成一种“字节码”，它类似于抽象的CPU指令，然后，针对不同平台编写虚拟机，不同平台的虚拟机负责加载字节码并执行，这样就实现了“一次编写，到处运行”的效果。当然，这是针对Java开发者而言。对于虚拟机，需要为每个平台分别开发。为了保证不同平台、不同公司开发的虚拟机都能正确执行Java字节码，SUN公司制定了一系列的Java虚拟机规范。从实践的角度看，JVM的兼容性做得非常好，低版本的Java字节码完全可以正常运行在高版本的JVM上。

## Java 版本

![Java 版本](Pictures\Java 版本.png)

- Java EE（Java Enterprise Edition）

- Java SE（Java Standard Edition）

- Java ME（Java Micro Edition）

简单来说，Java SE就是标准版，包含标准的JVM和标准库，而Java EE是企业版，它只是在Java SE的基础上加上了大量的API和库，以便方便开发Web应用、数据库、消息服务等，Java EE的应用使用的虚拟机和Java SE完全相同。Java ME就和Java SE不同，它是一个针对嵌入式设备的“瘦身版”，Java SE的标准库无法在Java ME上使用，Java ME的虚拟机也是“瘦身版”。

## Java Development Kit（JDK）

![JDK](Pictures\JDK.png)

- Java Runtime Emvironment（JRE）
  JRE就是运行Java字节码的虚拟机。但是，如果只有Java源码，要编译成Java字节码，就需要JDK，因为JDK除了包含JRE，还提供了编译器、调试器等开发工具。

可以在JAVA_HOME的bin目录下找到很多可执行文件：

- java：这个可执行程序其实就是JVM，运行Java程序，就是启动JVM，然后让JVM执行指定的编译后的代码；
- javac：这是Java的编译器，它用于把Java源码文件（以.java后缀结尾）编译为Java字节码文件（以.class后缀结尾）；
- jar：用于把一组.class文件打包成一个.jar文件，便于发布；
- javadoc：用于从Java源码中自动提取注释并生成文档；
- jdb：Java调试器，用于开发阶段的运行调试。

## Java 程序的运行过程

![Java程序执行过程](Pictures\Java程序执行过程.png)

![Java 程序执行过程](Pictures\Java程序执行过程2.png)

- 类加载器

  类加载器classloader是专门负责加载类的命令/工具
  JDK中自带了3个类加载器

  - 启动类加载器：rt.jar
    先通过启动类加载器加载 c: \Program Files\Javajdk1.8.0_101\jre\liblrt.rt.jar（java核心类库）
  - 扩展类加载器：ext/.jar
    扩展类加载器专门加载: c: \Program Files\Java\jdk1.8.0_101\jre\lib\ext\.jar
  - 应用类加载器: classpath
    应用类加载器专门加载: classpath中的类。

## Java 源程序与编译型运行区别

![Java 源程序与编译型运行区别](Pictures\Java程序与编译型程序运行的区别.png)

## Java Specification Request（JSR）规范和 Java Community Process（JCP）组织

为了保证Java语言的规范性，SUN公司搞了一个JSR规范，凡是想给Java平台加一个功能，比如说访问数据库的功能，大家要先创建一个JSR规范，定义好接口，这样，各个数据库厂商都按照规范写出Java驱动程序，开发者就不用担心自己写的数据库代码在MySQL上能跑，却不能跑在PostgreSQL上。所以JSR是一系列的规范，从JVM的内存模型到Web程序接口，全部都标准化了。而负责审核JSR的组织就是JCP。一个JSR规范发布时，为了让大家有个参考，还要同时发布一个“参考实现”，以及一个“兼容性测试套件”。