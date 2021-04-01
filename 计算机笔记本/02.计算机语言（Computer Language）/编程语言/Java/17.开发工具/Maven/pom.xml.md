# pom.xml

文件解释：

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <!--Project Object Model(POM)版本号-->
    <modelVersion>4.0.0</modelVersion>

    <!--以下三个是Maven的坐标-->
    <!--Maven项目的组织名-->
    <groupId>org.example</groupId>
    <!--Maven项目的构建名-->
    <artifactId>module-test001</artifactId>
    <!--Maven项目的版本号-->
    <version>1.0-SNAPSHOT</version>
    <!--项目的打包方式，默认为jar-->
    <packaging>jar</packaging>

    <properties>
        <!--Maven项目构建时使用的编码-->
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
        <!--编译代码使用的JDK-->
        <maven.compiler.source>11</maven.compiler.source>
        <!--运行代码使用的JDK-->
        <maven.compiler.target>11</maven.compiler.target>
        <!--自定义的全局变量-->
        <!--使用自变量用：${变量名}-->
        <【变量名】>变量值</【变量名】>
    </properties>

    <!--该项目的名称，意义不大，可以省略-->
    <name>【project-name】</name>
    <!--该项目的地址，意义不大，可以省略-->
    <url>【http://.....】</url>

    <!--项目的依赖关系-->
    <dependencies>
        <!--每一个dependency对应一个Maven项目-->
        <dependency>
            <groupId>【${变量名1}】</groupId>
            <artifactId>【${变量名2}】</artifactId>
            <version>【${变量名3}】</version>
            <!--配置此包是在运行时用还是编译时用，只需参与编译，无需参与打包设置为scope，只是运行时用，无须参与编译设置为runtime-->
            <!--<scope></scope>-->
        </dependency>
        <dependency>
            <groupId>mysql</groupId>
            <artifactId>mysql-connector-java</artifactId>
            <version>5.1.6</version>
        </dependency>
        <dependency>
            <groupId></groupId>
            <artifactId></artifactId>
        </dependency>
    </dependencies>

    <!--资源插件-->
    <build>
        <plugins>
            <plugin></plugin>
        </plugins>
    </build>
</project>
```

