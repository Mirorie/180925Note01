
day06[线程、同步]
一、Thread类 
1.构造方法：

public Thread():分配一个新的线程对象
public Thread(String name):分配一个指定名字的新的线程对象
public Thread(Runnnable target):分配一个带有指定目标的新的线程对象
public Thread(Runnable target,String name):分配一个带有指定目标新的线程对象并指定名字
2.常用方法

public String getName():获取当前线程名称
public void start():导致此线程开始执行；Java虚拟机调用此线程的run方法
public void run():此线程要执行的任务在此处定义代码
public static void sleep(long millis):市当前正在执行的线程以指定的毫秒数暂停
public static Thread currentThread():放回对当前正在执行的线程对象的引用
翻阅API后得知创建线程的方式总共有两种，一种是继承Thread类方式，一种是实现Runnable接口方式。

3.创建线程方式二

采用java.lang.Runnable也是非常常见的一种，我们只需要重写run方法即可，步骤如下： 
(1)定义Runnable接口的实现类，并重写该接口的run()方法，该run()方法的方法提同样是该线程的线程执行体 
(2)创建Runnable实现类的实例，并以此实例作为Thread的target来创建Thread对象，该Thread对象才是真正的线程对象 
(3)吊用线程对象的start()方法来启动线程

代码如下：

public class MyRunnable implements Runnable {
    @Override
    public void run() {
        for (int i = 0; i < 20; i++) {
            System.out.println(Thread.currentThread().getName()+" "+i);
        }
    }
}
public static void main(String[] args) {
        MyRunnable mr = new MyRunnable();//创建自定义类对象，线程任务对象
        Thread t = new Thread(mr,"小强");
        t.start();
        for (int i = 0; i < 20; i++) {
            System.out.println("旺财"+i);
        }
    }
通过实现Runnable接口，使得该类有了多线程类的特征。run()方法是多线程程序的一个执行目标。所有的多线程代码都在run方法里面。Thread类实际上也是实现了Runnable接口的类。 
再启用多线程的时候，需要先通过Thread类的构造方法Thread(Runnable target)构造出对象，然后调用Thread对象的start()方法来运行多线程代码。

4.Thread和Runnable的区别 
如果一个类继承Thread则不适合资源共享，但是如果实现了Runnable接口的话则很容易的实现资源共享

实现Runnable接口比继承Thread类所具有的的优势： 
(1)适合多个相同的程序代码的线程去共享同一个资源 
(2)可以避免java中的单继承的局限性 
(3)增加程序的健壮性，实现解耦操作，代码可以被多个线程共享，代码和线程独立 
(4)线程池只能放入实现Runnable或Callable类线程，不能直接放入继承Thraad的类

5.匿名内部类方式实现线程的创建

public class NoNameInnerClassThread {
    public static void main(String[] args){
       //new Runnable(){
       //    public void run(){
       //        for (int i = 0; i < 20; i++) {
       //            System.out.println("enen"+i);
       //        }
       //    }
       //}; //----这个整体 相当于new MyRunnable()
        Runnable r = new Runnable() {
            @Override
            public void run() {
                for (int i = 0; i < 20; i++) {
                    System.out.println("ruarua"+i);
                }
            }
        };
        new Thread(r).start();
        for (int i = 0; i < 20; i++) {
            System.out.println("bubu"+i);
        }
    }
}
二、线程安全

如果有多个线程在同时运行，而这些线程可能会同时运行这段代码。程序每次运行结果和单线程运行的结果是一样的，而且其他的变量的值也和预期的是一样的，就是线程安全的。

1.电影院发票示范：

public class Ticket implements Runnable {
    private int ticket = 100;
    @Override
    public void run() {
        while (true){//每个窗口买票的操作，窗口要永远开启
            if(ticket > 0){//有票可以卖
                try{//出票操作 使用sleep模拟一下出票时间
                    Thread.sleep(100);
                }catch (Exception e){
                    e.printStackTrace();
                }
                String name = Thread.currentThread().getName();//获取当前线程对象的名字
                System.out.println(name+" "+ticket--);
            }
        }
    }
}
public static void main(String[] args) {
        Ticket ticket = new Ticket();//创建线程任务对象
        Thread t1 = new Thread(ticket,"窗口1");
        Thread t2 = new Thread(ticket,"窗口2");
        Thread t3 = new Thread(ticket,"窗口3");
        t1.start();
        t2.start();
        t3.start();
    }
2.线程同步

要解决多线程并发访问一个资源的安全性问题：也就是解决重复票与不存在票问题，Java中提供了同步机制(synchronized)来解决。 
由三种方式完成同步操作： 
同步代码块 
同步方法 
锁机制

(1)同步代码块

同步代码块：synchronized关键字可以用于方法中的某个区块中，表示只对这个区块的资源实行互斥访问 
格式：
    synchronized(同步锁){
        需要同步操作的代码
    }
锁对象可以是任意类型
多个线程对象 要使用同一把锁
在任何时候，最多允许一个线程拥有同步锁，谁拿到锁谁就进入代码块，其他的线程只能在外等着(BLOCKED)
public class Ticket implements Runnable {
    private int ticket = 100;
    Object lock = new Object();
    @Override
    public void run() {
        while (true){
            synchronized (lock){
                if(ticket>0){
                    try{
                        Thread.sleep(100);
                    }catch (Exception e){
                        e.printStackTrace();
                    }
                    String name = Thread.currentThread().getName();
                    System.out.println(name+" 正在卖"+ticket--);
                }
            }
        }
    }
}
public static void main(String[] args) {
        Ticket ticket = new Ticket();
        Thread t1 = new Thread(ticket,"窗口1");
        Thread t2 = new Thread(ticket,"窗口2");
        Thread t3 = new Thread(ticket,"窗口3");
        t1.start();
        t2.start();
        t3.start();
    }
(2)同步方法

同步方法使用synchronized修饰的方法，就叫同步方法，保证A线程执行该方法的时候，其他线程只能在方法外等着。
    public synchronized void method(){
        可能会产生线程安全问题的代码
    }
同步锁是谁？对于非static方法，同步锁就是this,对于static方法，我们使用当前方法所在的累的字节码对象（类名.class）

public class Ticket implements Runnable{
    private int ticket = 100;
    @Override
    public void run() {
        while (true){
            sellTicket();
        }
    }
    public synchronized void sellTicket() {
        if(ticket>0){
            try{
                Thread.sleep(100);
            }catch (Exception e){
                e.printStackTrace();
            }
            String name = Thread.currentThread().getName();
            System.out.println(name+"正在卖"+ticket--);
        }
    }
}
(3)Lock锁

java.util.concurrenr.locks.Lock机制提供了比synchronized代码块和synchronized方法更广泛的锁定操作，同步代码块/同步方法具有的功能Lock都有，除此之外更强大，更体现面向对象。

Lock锁也成同步锁，加锁与释放锁方法化了，如下：

public void lock()加同步锁
public void unlock():释放同步锁
import java.util.concurrent.locks.Lock;
import java.util.concurrent.locks.ReentrantLock;
public class Ticked implements Runnable{
    private int ticket = 100;
    Lock lock = new ReentrantLock();
    @Override
    public void run() {
        while (true){
            lock.lock();
            if(ticket>0){
                try{
                    Thread.sleep(50);
                }catch (Exception e){
                    e.printStackTrace();
                }
            }
            String name = Thread.currentThread().getName();
            System.out.println(name+"正在卖"+ticket--);
            lock.unlock();
        }
    }
}
三、线程状态

1.TimedWaiting一个正在限时等待另一个线程执行一个（唤醒）动作的线程处于这一状态。

public class MyThread extends Thread {
    public void run(){
        for (int i = 0; i < 100; i++) {
            if((i)%10 == 0){
                System.out.println("---------"+i);
            }
            System.out.println(i);
            try{
                Thread.sleep(1000);
                System.out.println("线程睡眠1秒！\\n");
            }catch (Exception e){
                e.printStackTrace();
            }
        }
    }
    public static void main(String[] args) {
        new MyThread().start();
    }
}
2.BLOCKED(锁阻塞)一个正在阻塞等待一个监视器锁（锁对象）的线程处于这一状态。
我们已经学完同步机制，那么这个状态是非常好理解的了。比如，线程A与线程B代码中使用同一锁，
如果线程A获取到锁，线程A进入到Runnable状态，那么线程B就进入到Blocked锁阻塞状态。