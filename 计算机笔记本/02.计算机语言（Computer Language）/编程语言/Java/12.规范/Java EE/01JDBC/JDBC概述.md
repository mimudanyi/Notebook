# Java 数据库连接（Java Database Connectivity ，JDBC）

## 一、定义

是 Java 语言中用来规范客户端程序如何来访问数据库的应用程序接口，提供了诸如查询和更新数据库中数据的方法。

## 二、JDBC编程六步

```java
1、注册驱动
2、获取连接
3、获取数据库操作对象
4、执行SQL语句
5、处理结果
6、释放资源
```

## 三、JDBC代码

```java
//JDBC000文件代码：

import java.sql.*;
import java.util.ResourceBundle;

public class JDBC000 {
    public static void jdbc000(){
        //使用资源管理器绑定属性配置文件
        ResourceBundle resourceBundle = ResourceBundle.getBundle("jdbc");   			//jdbc.properties不用写后缀
        String driver = resourceBundle.getString("driver");
        String url = resourceBundle.getString("url");
        String user = resourceBundle.getString("user");
        String password = resourceBundle.getString("password");

        Connection connection = null;    //通道建立
        Statement statement = null;  //载具建立

        try {
            //第一步：驱动注册（通道注册）
//          方法一：
//          Driver driver = new com.mysql.cj.jdbc.Driver();
//          DriverManager.registerDriver(driver);
//          方法二：将com.mysql.cj.jdbc.Driver这个类装载到JVM中，装载过程中会自动执行静态代码块完成驱动的注册。
//          为什么这种方式常用﹖因为参数是一个字符串，字符串可以写到xxx.properties文件中。
            Class.forName(driver);

            //第二步：获取连接（通道建立）
            connection = DriverManager.getConnection(url,user,password);

            //第三步：获取数据库连接对象（载具建立）
            statement = connection.createStatement();

            //第四步：执行SQL语句,并返回值：专门执行DML语句,返回值是影响数据库中的记录条数。（载具运送货物并返回钱款）
            int count = statement.executeUpdate("INSERT INTO students VALUES (16,3,null,null,99);");
            System.out.println("修改了" + count + "条数据。");
        } catch (SQLException e) {
            e.printStackTrace();
        }catch (ClassNotFoundException e){
            e.printStackTrace();
        }finally {
            //第五步：释放资源:为了保证资源一定释放，在finally语句中释放资源,并且要遵循资源从小到大依次关闭（销毁痕迹）
            if (statement != null){ //载具销毁
                try {
                    statement.close();
                } catch (SQLException e) {
                    e.printStackTrace();
                }
            }
            if (connection != null) {   //通道销毁
                try {
                    connection.close();
                } catch (SQLException e) {
                    e.printStackTrace();
                }
            }
        }
    }
}
```



## JDBC事务机制

JDBC中事务是自动提交的，执行一次DML语句，就会自动提交一次。

