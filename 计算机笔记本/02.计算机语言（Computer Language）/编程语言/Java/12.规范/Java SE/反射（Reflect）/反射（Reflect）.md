# 反射（Reflect）

## 作用

用来反编译

## 相关类

java.lang.reflect

- java.lang.reflect.Method：代表字节码中的方法字节码。
- java.lang.reflect.Constructor：代表字节码中的构造方法字节码。
- java.lang.reflect.Field：代表字节码中的属性字节码。

java.lang

- Class：代表整个字节码，代表一个类型

## 得到Class类型的三种方法

- Class类中有一个forName方法。  

```java
Class c1 = Class.forName("包.类");
```

- Java 中，任何一种类型都有getClass方法。

```java
String s= "abc";  Class x = s.getClass();
```

- Java 中，任何一种类型都有class属性。

```java
Class a = int.class; 
```

## 调用无参构造的两种方法

![](Pictures\Untitled.png)