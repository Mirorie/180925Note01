JavaNote[Collection、泛型]
一、Collection常用功能

public boolean add(E e) ： 把给定的对象添加到当前集合中
public void clear() :清空集合中所有的元素
public boolean remove(E e) : 把给定的对象在当前集合中删除
public boolean contains(E e) : 判断当前集合中是否包含给定的对象
public boolean isEmpty() : 判断当前集合是否为空
public int size() : 返回集合中元素的个数
public Object[] toArray() : 把集合中的元素，存储到数组中。
二、Iterator迭代器

1.Iterator接口：Iterator 接口也是Java集合中的一员，但它与Collection Map 接口有所不同，Collection 接口与Map接口主要用于存储元素，而Iterator主要用于迭代访问（即遍历）Collection 中的元素，因此Iterator对象也被称为迭代器。 
?public Iterator iterator():获取集合对应的迭代器，用来遍历集合中的元素

2.迭代：即Collection集合元素的通用获取方式。在取元素之前先要判断集合中有没有元素，如果有，就把这个元素取出来，继续在判断，如果还有就再取出出来。一直把集合中的所有元素全部取出。这种取出方式专业术语称为迭代。

3.Iterator接口的常用方法如下：

Public E next():返回迭代的下一个元素
Public boolean hasNext():如果仍有元素可以迭代，则返回true
4.增强for： 
For(元素的数据类型 变量:Collection集合or数组){ 
//写操作代码 
}

三、泛型

将运行时期的ClassCastException，转移到了编译时期变成了编译失败。
避免了类型强转的麻烦
1.定义格式： 
修饰符class 类名<代表泛型的变量>{} 
Class ArrayList{ }

2.含有泛型的接口： 
修饰符 interface接口名<代表泛型的变量>{ }

3.泛型通配符：当使用泛型类或者接口时，传递的数据中，泛型类型不确定，可以通过通配符表示。但是一旦使用泛型的通配符后，只能使用Object类中的共性方法，集合中元素自身方法无法使用。 
4.通配符高级使用--受限泛型 
（1）泛型的上限： 
格式：类型名称 对象名称 
意义：只能接受该类型及其子类 
（2）泛型的下限： 
格式：类型名称 对象名称 
意义：只能接受该类型及其父类型 
public static void getElement1(Collectioncoll){} 
public static void getElement2(Collectioncoll){}
