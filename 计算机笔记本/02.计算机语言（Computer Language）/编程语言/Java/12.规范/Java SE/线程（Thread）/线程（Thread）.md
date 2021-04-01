# 线程（Thread）

# 一、实现多线程的方法

## 第一种：通过继承Thread Class来创建线程

写一个类继承Thread class，重新run method，即你要运行的另一个线程的内容，在main method中new一个你写的继承Thread class的class，然后调用这个class的run method

```java
public class ThreadTest {
    public static void main(){
        MyThread mythread = new MyThread();
        mythread.start();
        
        for(int i = 0; i < 1000; i++){
            System.out.println(主线程--->" + i);
        }
    }
}

class MyThread extends Thread{
    @Override
    public void run(){
        for(int i = 0; i < 1000; i++){
            System.out.println("分支线程--->" + i);
        }
    }
}
```

## 第二种：通过实现Runnable接口来创建线程

```java
public class Threadtest {
    public static void main(String[] args) {
        MyThread myThread = new MyThread();
        Thread thread = new Thread(myThread);
    }
}

//这并不是一个线程类，是一个可运行的类，它不是一个线程。
class MyThread implements Runnable{
    @Override
    public void run() {

    }
}
```

## 第三种：通过Callable和Futrue创建线程

- 1. 创建 Callable 接口的实现类，并实现 call() 方法，该 call() 方法将作为线程执行体，并且有返回值。
- 1. 创建 Callable 实现类的实例，使用 FutureTask 类来包装 Callable 对象，该 FutureTask 对象封装了该 Callable 对象的 call() 方法的返回值。
- 1. 使用 FutureTask 对象作为 Thread 对象的 target 创建并启动新线程。
- 1. 调用 FutureTask 对象的 get() 方法来获得子线程执行结束后的返回值。

```java
public class CallableThreadTest implements Callable<Integer> {
    public static void main(String[] args)  
    {  
        CallableThreadTest ctt = new CallableThreadTest();  
        FutureTask<Integer> ft = new FutureTask<>(ctt);  
        for(int i = 0;i < 100;i++)  
        {  
            System.out.println(Thread.currentThread().getName()+" 的循环变量i的值"+i);  
            if(i==20)  
            {  
                new Thread(ft,"有返回值的线程").start();  
            }  
        }  
        try  
        {  
            System.out.println("子线程的返回值："+ft.get());  
        } catch (InterruptedException e)  
        {  
            e.printStackTrace();  
        } catch (ExecutionException e)  
        {  
            e.printStackTrace();  
        }  
  
    }
    @Override  
    public Integer call() throws Exception  
    {  
        int i = 0;  
        for(;i<100;i++)  
        {  
            System.out.println(Thread.currentThread().getName()+" "+i);  
        }  
        return i;  
    }  
}
```

## 三种创建线程方式的对比

- 1. 采用实现 Runnable、Callable 接口的方式创建多线程时，线程类只是实现了 Runnable 接口或 Callable 接口，还可以继承其他类。
- 1. 使用继承 Thread 类的方式创建多线程时，编写简单，如果需要访问当前线程，则无需使用 Thread.currentThread() 方法，直接使用 this 即可获得当前线程。

# 二、线程生命周期

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/68108ff7-75cc-41e0-89e1-369193df0152/java-thread.jpg](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/68108ff7-75cc-41e0-89e1-369193df0152/java-thread.jpg)

- **新建状态:**

  使用 **new** 关键字和 **Thread** 类或其子类建立一个线程对象后，该线程对象就处于新建状态。它保持这个状态直到程序 **start()** 这个线程。

- **就绪状态:**

  当线程对象调用了start()方法之后，该线程就进入就绪状态。就绪状态的线程处于就绪队列中，要等待JVM里线程调度器的调度。

- **运行状态:**

  如果就绪状态的线程获取 CPU 资源，就可以执行 **run()**，此时线程便处于运行状态。处于运行状态的线程最为复杂，它可以变为阻塞状态、就绪状态和死亡状态。

- **阻塞状态:**

  如果一个线程执行了sleep（睡眠）、suspend（挂起）等方法，失去所占用资源之后，该线程就从运行状态进入阻塞状态。在睡眠时间已到或获得设备资源后可以重新进入就绪状态。可以分为三种：

  - 等待阻塞：运行状态中的线程执行 wait() 方法，使线程进入到等待阻塞状态。
  - 同步阻塞：线程在获取 synchronized 同步锁失败(因为同步锁被其他线程占用)。
  - 其他阻塞：通过调用线程的 sleep() 或 join() 发出了 I/O 请求时，线程就会进入到阻塞状态。当sleep() 状态超时，join() 等待线程终止或超时，或者 I/O 处理完毕，线程重新转入就绪状态。

- **死亡状态:**

  一个运行状态的线程完成任务或者其他终止条件发生时，该线程就切换到终止状态。

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/46187df2-50ba-43b4-9f76-ab37c4d8c1b5/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/46187df2-50ba-43b4-9f76-ab37c4d8c1b5/Untitled.png)

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f88f3836-737a-485e-b79c-829b1ffae761/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f88f3836-737a-485e-b79c-829b1ffae761/Untitled.png)

[守护线程](https://www.notion.so/8741a93411d94500ad105d75984097ec)

[定时器](https://www.notion.so/c884d15e23fe4ac0896ecf9b7a5495a0)

# 三、线程的优先级

每一个 Java 线程都有一个优先级，这样有助于操作系统确定线程的调度顺序。

Java 线程的优先级是一个整数，其取值范围是 1 （Thread.MIN_PRIORITY ） - 10 （Thread.MAX_PRIORITY ）。

默认情况下，每一个线程都会分配一个优先级 NORM_PRIORITY（5）。

具有较高优先级的线程对程序更重要，并且应该在低优先级的线程之前分配处理器资源。但是，线程优先级不能保证线程执行的顺序，而且非常依赖于平台。