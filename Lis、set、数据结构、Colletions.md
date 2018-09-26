Day03[Lis、set、数据结构、Colletions]

一、List接口介绍 
java.util.List接口继承自Collection接口，是单列集合的一个重要分支，习惯性地会将实现了List接口的对象称为List集合。在List集合中允许出现重复的元素，所有的元素是以一种线性方式进行存储的，在程序中可以通过索引来访问集合中的指定元素。另外，List集合还有一个特点就是元素有序，即元素的存入顺序和取出顺序一致。

public void add（int index,E element）:将指定的元素，添加到该集合中的指定位置上。
public E get(int index) :返回结合中指定位置的元素。
public E remove(int index) : 移除列表中指定位置的元素，返回被移除的元素。
public E set(int index, E element) :用指定元素替换集合中指定位置的元素，返回更新前的元素。 
二、数据结构 
1.栈： 
stack,又称堆栈，它是运算受限的线性表，其限制是仅允许在标的一端进行插入和删除操作，不允许在其他任何位置进行添加、查找、删除等操作。
压栈：就是存元素。即，把元素存储到栈的顶端位置，栈中已有元素依次向栈底方向移动一个位置。
弹栈：就是取元素。即，把栈的顶端位置元素取出，栈中已有元素依次向栈顶方向移动一个位置。 
2.队列： 
queue,简称队，它同堆栈一样，也是一种运算受限的线性表，其限制是仅允许在表的一端进行插入， 
而在表的另一端进行删除。
先进先出（即，存进去的元素，要在后它前面的元素依次取出后，才能取出该元素）。例如，小火车过山洞，车头先进去，车尾后进去；车头先出来，车尾后出来。
队列的入口、出口各占一侧。 
3.数组:
Array,是有序的元素序列，数组是在内存中开辟一段连续的空间，并在此空间存放元素。就像是一排出租屋，有100个房间，从001到100每个房间都有固定编号，通过编号就可以快速找到租房子的人。
查找元素快：通过索引，可以快速访问指定位置的元素
增删元素慢 
4.链表：
查找元素慢：想查找某个元素，需要通过连接的节点，依次向后查找指定元素
增删元素快 
5.红黑树：
二叉树：binary tree,是每个结点不超过2的有序树（tree）。 
三、List的子类： 
1.ArrayList集合： 
java.util.ArrayList集合数据存储的结构是数组结构。元素增删慢，查找快，由于日常开发中使用最多的功能为查询数据、遍历数据，所以 ArrayList 是最常用的集合。许多程序员开发时非常随意地使用ArrayList完成任何需求，并不严谨，这种用法是不提倡的。 
2.LinkedList集合： 
java.util.LinkedList集合数据存储的结构是链表结构。方便元素添加、删除的集合
public void addFirst(E e):将指定元素插入此列表的开头。
public void addLast(E e):将指定元素添加到此列表的结尾。、
public E getFirst() :返回此列表的第一个元素。
public E getLast() :返回此列表的最后一个元素。
public E removeFirst():移除并返回此列表的第一个元素。
public E removeLast():移除并返回此列表的最后一个元素。
public E pop() :从此列表所表示的堆栈处弹出一个元素。
public void push(E e) :将元素推入此列表所表示的堆栈
public boolean isEmpty()：如果列表不包含元素，则返回true。

 while (!linkedList.isEmpty()){
         System.out.println(linkedList.pop());
     }
三、Set接口 
1.HashSet集合介绍 
ava.util.HashSet是 Set接口的一个实现类，它所存储的元素是不可重复的，并且元素都是无序的(即存取顺序不一致)。 
2.HashSet存储自定义类型元素 
给HashSet中存放自定义类型元素时，需要重写对象中的hashCode和equals方法，建立自己的比较方式，才能保证HashSet集合中的对象唯一。 
3.LinkedHashSet 
我们知道HashSet保证元素唯一，可是元素存放进去是没有顺序的，那么我们要保证有序，怎么办呢？在HashSet下面有一个子类 java.util.LinkedHashSet，它是链表和哈希表组合的一个数据存储结构。

public static int getSum(int... arr) {
    int sum = 0;
    for (int a : arr) {
        sum += a;
    }
    return sum;
}
四、Collections 
1.常用功能： 
- java.utils.Collections是集合工具类，用来对集合进行操作。部分方法如下： 
- public static boolean addAll(Collection c, T... elements) :往集合中添加一些元素 
- public static void shuffle(List list):打乱集合顺序。 
- public static void sort(List list):将集合中元素按照默认规则排序。 
- public static void sort(List list，Comparator ):将集合中元素按照指定规则排序。 
2.Comparator比较器

ArrayList<String> list = new ArrayList<>();
    //Collections.addAll(list,"qwqeasd","asfsdasd","dffda","jksdfuhgij");
    list.add("asd");
    list.add("gasd");
    list.add("hasd");
    list.add("qwasd");
    Collections.sort(list, new Comparator<String>() {
        @Override
        public int compare(String o1, String o2) {
            return 0;
        }
    });
    System.out.println(list);
3.Comparable和Comparator两个接口的区别

Comparable：强行对实现它的每个类的对象进行整体排序。这种排序被称为类的自然排序，类的compareTo方法被称为它的自然比较方法。只能在类中实现compareTo()一次，不能经常修改类的代码实现自己想要的排序。实现此接口的对象列表（和数组）可以通过Collections.sort（和Arrays.sort）进行自动排序，对象可以用作有序映射中的键或有序集合中的元素，无需指定比较器。

Comparator强行对某个对象进行整体排序。可以将Comparator 传递给sort方法（如Collections.sort或 Arrays.sort），从而允许在排序顺序上实现精确控制。还可以使用Comparator来控制某些数据结构（如有序set或有序映射）的顺序，或者为那些没有自然顺序的对象collection提供排序。