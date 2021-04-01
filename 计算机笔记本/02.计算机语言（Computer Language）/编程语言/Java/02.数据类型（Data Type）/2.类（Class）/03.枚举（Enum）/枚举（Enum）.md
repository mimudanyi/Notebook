# 枚举

## 一、定义

Java 枚举是一个类，一般表示一组常量，比如一年的 4 个季节，一个年的 12 个月份，一个星期的 7 天，方向有东南西北等。Java 枚举类使用 enum 关键字来定义，各个常量使用逗号 , 来分割。

例如定义一个颜色的枚举类。

```java
enum Color
{
RED, GREEN, BLUE;
}
```

枚举类也可以声明在内部类中：

```java
public class Test
{
enum Color
{
RED, GREEN, BLUE;
}
// 执行输出结果
public static void main(String[] args)
{
Color c1 = Color.RED;
System.out.println(c1);
}
}
```

每个枚举都是通过 Class 在内部实现的，且所有的枚举值都是 public static final 的。

values(), ordinal() 和 valueOf() 方法

enum 定义的枚举类默认继承了 java.lang.Enum 类，并实现了 java.lang.Seriablizable 和 java.lang.Comparable 两个接口。

values(), ordinal() 和 valueOf() 方法位于 java.lang.Enum 类中：

values() 返回枚举类中所有的值。

ordinal()方法可以找到每个枚举常量的索引，就像数组索引一样。

valueOf()方法返回指定字符串值的枚举常量。