
day06[�̡߳�ͬ��]
һ��Thread�� 
1.���췽����

public Thread():����һ���µ��̶߳���
public Thread(String name):����һ��ָ�����ֵ��µ��̶߳���
public Thread(Runnnable target):����һ������ָ��Ŀ����µ��̶߳���
public Thread(Runnable target,String name):����һ������ָ��Ŀ���µ��̶߳���ָ������
2.���÷���

public String getName():��ȡ��ǰ�߳�����
public void start():���´��߳̿�ʼִ�У�Java��������ô��̵߳�run����
public void run():���߳�Ҫִ�е������ڴ˴��������
public static void sleep(long millis):�е�ǰ����ִ�е��߳���ָ���ĺ�������ͣ
public static Thread currentThread():�ŻضԵ�ǰ����ִ�е��̶߳��������
����API���֪�����̵߳ķ�ʽ�ܹ������֣�һ���Ǽ̳�Thread�෽ʽ��һ����ʵ��Runnable�ӿڷ�ʽ��

3.�����̷߳�ʽ��

����java.lang.RunnableҲ�Ƿǳ�������һ�֣�����ֻ��Ҫ��дrun�������ɣ��������£� 
(1)����Runnable�ӿڵ�ʵ���࣬����д�ýӿڵ�run()��������run()�����ķ�����ͬ���Ǹ��̵߳��߳�ִ���� 
(2)����Runnableʵ�����ʵ�������Դ�ʵ����ΪThread��target������Thread���󣬸�Thread��������������̶߳��� 
(3)�����̶߳����start()�����������߳�

�������£�

public class MyRunnable implements Runnable {
    @Override
    public void run() {
        for (int i = 0; i < 20; i++) {
            System.out.println(Thread.currentThread().getName()+" "+i);
        }
    }
}
public static void main(String[] args) {
        MyRunnable mr = new MyRunnable();//�����Զ���������߳��������
        Thread t = new Thread(mr,"Сǿ");
        t.start();
        for (int i = 0; i < 20; i++) {
            System.out.println("����"+i);
        }
    }
ͨ��ʵ��Runnable�ӿڣ�ʹ�ø������˶��߳����������run()�����Ƕ��̳߳����һ��ִ��Ŀ�ꡣ���еĶ��̴߳��붼��run�������档Thread��ʵ����Ҳ��ʵ����Runnable�ӿڵ��ࡣ 
�����ö��̵߳�ʱ����Ҫ��ͨ��Thread��Ĺ��췽��Thread(Runnable target)���������Ȼ�����Thread�����start()���������ж��̴߳��롣

4.Thread��Runnable������ 
���һ����̳�Thread���ʺ���Դ�����������ʵ����Runnable�ӿڵĻ�������׵�ʵ����Դ����

ʵ��Runnable�ӿڱȼ̳�Thread�������еĵ����ƣ� 
(1)�ʺ϶����ͬ�ĳ��������߳�ȥ����ͬһ����Դ 
(2)���Ա���java�еĵ��̳еľ����� 
(3)���ӳ���Ľ�׳�ԣ�ʵ�ֽ��������������Ա�����̹߳���������̶߳��� 
(4)�̳߳�ֻ�ܷ���ʵ��Runnable��Callable���̣߳�����ֱ�ӷ���̳�Thraad����

5.�����ڲ��෽ʽʵ���̵߳Ĵ���

public class NoNameInnerClassThread {
    public static void main(String[] args){
       //new Runnable(){
       //    public void run(){
       //        for (int i = 0; i < 20; i++) {
       //            System.out.println("enen"+i);
       //        }
       //    }
       //}; //----������� �൱��new MyRunnable()
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
�����̰߳�ȫ

����ж���߳���ͬʱ���У�����Щ�߳̿��ܻ�ͬʱ������δ��롣����ÿ�����н���͵��߳����еĽ����һ���ģ����������ı�����ֵҲ��Ԥ�ڵ���һ���ģ������̰߳�ȫ�ġ�

1.��ӰԺ��Ʊʾ����

public class Ticket implements Runnable {
    private int ticket = 100;
    @Override
    public void run() {
        while (true){//ÿ��������Ʊ�Ĳ���������Ҫ��Զ����
            if(ticket > 0){//��Ʊ������
                try{//��Ʊ���� ʹ��sleepģ��һ�³�Ʊʱ��
                    Thread.sleep(100);
                }catch (Exception e){
                    e.printStackTrace();
                }
                String name = Thread.currentThread().getName();//��ȡ��ǰ�̶߳��������
                System.out.println(name+" "+ticket--);
            }
        }
    }
}
public static void main(String[] args) {
        Ticket ticket = new Ticket();//�����߳��������
        Thread t1 = new Thread(ticket,"����1");
        Thread t2 = new Thread(ticket,"����2");
        Thread t3 = new Thread(ticket,"����3");
        t1.start();
        t2.start();
        t3.start();
    }
2.�߳�ͬ��

Ҫ������̲߳�������һ����Դ�İ�ȫ�����⣺Ҳ���ǽ���ظ�Ʊ�벻����Ʊ���⣬Java���ṩ��ͬ������(synchronized)������� 
�����ַ�ʽ���ͬ�������� 
ͬ������� 
ͬ������ 
������

(1)ͬ�������

ͬ������飺synchronized�ؼ��ֿ������ڷ����е�ĳ�������У���ʾֻ������������Դʵ�л������ 
��ʽ��
    synchronized(ͬ����){
        ��Ҫͬ�������Ĵ���
    }
�������������������
����̶߳��� Ҫʹ��ͬһ����
���κ�ʱ���������һ���߳�ӵ��ͬ������˭�õ���˭�ͽ������飬�������߳�ֻ���������(BLOCKED)
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
                    System.out.println(name+" ������"+ticket--);
                }
            }
        }
    }
}
public static void main(String[] args) {
        Ticket ticket = new Ticket();
        Thread t1 = new Thread(ticket,"����1");
        Thread t2 = new Thread(ticket,"����2");
        Thread t3 = new Thread(ticket,"����3");
        t1.start();
        t2.start();
        t3.start();
    }
(2)ͬ������

ͬ������ʹ��synchronized���εķ������ͽ�ͬ����������֤A�߳�ִ�и÷�����ʱ�������߳�ֻ���ڷ�������š�
    public synchronized void method(){
        ���ܻ�����̰߳�ȫ����Ĵ���
    }
ͬ������˭�����ڷ�static������ͬ��������this,����static����������ʹ�õ�ǰ�������ڵ��۵��ֽ����������.class��

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
            System.out.println(name+"������"+ticket--);
        }
    }
}
(3)Lock��

java.util.concurrenr.locks.Lock�����ṩ�˱�synchronized������synchronized�������㷺������������ͬ�������/ͬ���������еĹ���Lock���У�����֮���ǿ�󣬸������������

Lock��Ҳ��ͬ�������������ͷ����������ˣ����£�

public void lock()��ͬ����
public void unlock():�ͷ�ͬ����
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
            System.out.println(name+"������"+ticket--);
            lock.unlock();
        }
    }
}
�����߳�״̬

1.TimedWaitingһ��������ʱ�ȴ���һ���߳�ִ��һ�������ѣ��������̴߳�����һ״̬��

public class MyThread extends Thread {
    public void run(){
        for (int i = 0; i < 100; i++) {
            if((i)%10 == 0){
                System.out.println("---------"+i);
            }
            System.out.println(i);
            try{
                Thread.sleep(1000);
                System.out.println("�߳�˯��1�룡\\n");
            }catch (Exception e){
                e.printStackTrace();
            }
        }
    }
    public static void main(String[] args) {
        new MyThread().start();
    }
}
2.BLOCKED(������)һ�����������ȴ�һ�����������������󣩵��̴߳�����һ״̬��
�����Ѿ�ѧ��ͬ�����ƣ���ô���״̬�Ƿǳ��������ˡ����磬�߳�A���߳�B������ʹ��ͬһ����
����߳�A��ȡ�������߳�A���뵽Runnable״̬����ô�߳�B�ͽ��뵽Blocked������״̬��