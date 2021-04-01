# 日期时间类（DataTime）

## 一、Java中日期和时间的格式化编码

时间模式字符串用来指定时间格式。在此模式中，所有的 ASCII 字母被保留为模式字母，定义如下：

### 1.1 时间日期和时间的格式化编码：

| 以什么为起点 |    起点    | 世纪 |  年  |  月  |        周        |    日     |             时              |  分  |  秒  | 毫秒 |
| :----------: | :--------: | :--: | :--: | :--: | :--------------: | :-------: | :-------------------------: | :--: | :--: | :--: |
|    时间点    |  公元元年  |      |  y   |      |                  |           |                             |      |      |      |
|    时间点    | 计算机元年 |      |      |      |                  |           |                             |      |      |      |
| 时间段中一点 |    世纪    |  -   |  y   |      |                  |           |                             |      |      |      |
| 时间段中一点 |     年     |  -   |  -   |  M   |        w         |     D     |                             |      |      |      |
| 时间段中一点 |     月     |  -   |  -   |  -   |        W         | d(多少日) |                             |      |      |      |
| 时间段中一点 |     月     |  -   |  -   |  -   | F月中第几周的周X |           |                             |      |      |      |
| 时间段中一点 |     周     |  -   |  -   |  -   |        -         | E(星期几) |                             |      |      |      |
| 时间段中一点 |     日     |  -   |  -   |  -   |        -         |     -     |  h(A.M/P.M.(1~12)格式小时)  |      |      |      |
| 时间段中一点 |     日     |  -   |  -   |  -   |        -         |     -     |    H(一天中的小时(0~23))    |      |      |      |
| 时间段中一点 |     日     |  -   |  -   |  -   |        -         |     -     |    k(一天中的小时(1~24))    |      |      |      |
| 时间段中一点 |     日     |  -   |  -   |  -   |        -         |     -     | K(A.M./P.M. (0~11)格式小时) |  m   |      |      |
| 时间段中一点 |     时     |  -   |  -   |  -   |        -         |     -     |              -              |  m   |      |      |
| 时间段中一点 |     分     |  -   |  -   |  -   |        -         |     -     |              -              |  -   |  s   |      |
| 时间段中一点 |     秒     |  -   |  -   |  -   |        -         |     -     |              -              |  -   |  -   |  S   |

### 1.2 其他时间日期和时间的格式化编码：

| 模式字母 |      含义      |
| :------: | :------------: |
|    G     |      公元      |
|    z     |      时区      |
|    a     | A.M./P.M. 标记 |
|    ‘     |   文字界定符   |
|    ''    |     单引号     |
|          |                |

## 二、java.util.Data

- 构造方法

  - ```java
    public Date() {
        this(System.currentTimeMillis());
    }
    ```

  - ```java
    public Date(long date) {
        fastTime = date;
    }
    ```

- 其他方法

## 三、java.util.Calendar



## 四、java.text.SimpleDateFormat

负责日期格式化

```java
//App.java文件代码:

import java.text.ParseException;
import java.text.SimpleDateFormat;
import java.util.Date;

public class App {
    public static void main(String[] args) {
        //将日期以自己想要的格式输出
        Date date = new Date();
        SimpleDateFormat simpleDateFormat = 
            new SimpleDateFormat("z G yyyy-MM-dd F HH:mm:ss SSSS");
        String newTime = simpleDateFormat.format(date);
        System.out.println(newTime);

        //将自己输入的字符串格式日期，变为对象
        String time = "2021.5.16";
        SimpleDateFormat simpleDateFormat1 = new SimpleDateFormat("yyyy.M.dd");
        try {
            Date date1 = simpleDateFormat1.parse(time);
            System.out.println(date1);
        } catch (ParseException e) {	//ParseException 日期对象和输入的日期对不上的异常
            e.printStackTrace();
        }
    }
}
```

> 输出结果
>
> ```
> CST 公元 2021-04-01 1 00:30:04 0646
> Sun May 16 00:00:00 CST 2021
> ```

## 五、java.lang.System.currentTimeMillis()

获取自1970年1月1日00:00:00 000到当前系统时间的总毫秒数。1秒=1000毫秒

```java
//App.java文件代码:

public class App {
    public static void main(String[] args) {
        //获取自1970年1月1日00:00:00 000到当前系统时间的总毫秒数。1秒=1000毫秒
        Long time = System.currentTimeMillis();
        System.out.println(time);
    }
}
```

> 运行结果：
>
> ```
> 1617208839714
> ```
>
> 每次的运行结果不一样