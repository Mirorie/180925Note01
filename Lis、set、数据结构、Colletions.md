Day03[Lis��set�����ݽṹ��Colletions]

һ��List�ӿڽ��� 
java.util.List�ӿڼ̳���Collection�ӿڣ��ǵ��м��ϵ�һ����Ҫ��֧��ϰ���ԵػὫʵ����List�ӿڵĶ����ΪList���ϡ���List��������������ظ���Ԫ�أ����е�Ԫ������һ�����Է�ʽ���д洢�ģ��ڳ����п���ͨ�����������ʼ����е�ָ��Ԫ�ء����⣬List���ϻ���һ���ص����Ԫ�����򣬼�Ԫ�صĴ���˳���ȡ��˳��һ�¡�

public void add��int index,E element��:��ָ����Ԫ�أ���ӵ��ü����е�ָ��λ���ϡ�
public E get(int index) :���ؽ����ָ��λ�õ�Ԫ�ء�
public E remove(int index) : �Ƴ��б���ָ��λ�õ�Ԫ�أ����ر��Ƴ���Ԫ�ء�
public E set(int index, E element) :��ָ��Ԫ���滻������ָ��λ�õ�Ԫ�أ����ظ���ǰ��Ԫ�ء� 
�������ݽṹ 
1.ջ�� 
stack,�ֳƶ�ջ�������������޵����Ա��������ǽ������ڱ��һ�˽��в����ɾ���������������������κ�λ�ý�����ӡ����ҡ�ɾ���Ȳ�����
ѹջ�����Ǵ�Ԫ�ء�������Ԫ�ش洢��ջ�Ķ���λ�ã�ջ������Ԫ��������ջ�׷����ƶ�һ��λ�á�
��ջ������ȡԪ�ء�������ջ�Ķ���λ��Ԫ��ȡ����ջ������Ԫ��������ջ�������ƶ�һ��λ�á� 
2.���У� 
queue,��ƶӣ���ͬ��ջһ����Ҳ��һ���������޵����Ա��������ǽ������ڱ��һ�˽��в��룬 
���ڱ����һ�˽���ɾ����
�Ƚ��ȳ����������ȥ��Ԫ�أ�Ҫ�ں���ǰ���Ԫ������ȡ���󣬲���ȡ����Ԫ�أ������磬С�𳵹�ɽ������ͷ�Ƚ�ȥ����β���ȥ����ͷ�ȳ�������β�������
���е���ڡ����ڸ�ռһ�ࡣ 
3.����:
Array,�������Ԫ�����У����������ڴ��п���һ�������Ŀռ䣬���ڴ˿ռ���Ԫ�ء�������һ�ų����ݣ���100�����䣬��001��100ÿ�����䶼�й̶���ţ�ͨ����žͿ��Կ����ҵ��ⷿ�ӵ��ˡ�
����Ԫ�ؿ죺ͨ�����������Կ��ٷ���ָ��λ�õ�Ԫ��
��ɾԪ���� 
4.����
����Ԫ�����������ĳ��Ԫ�أ���Ҫͨ�����ӵĽڵ㣬����������ָ��Ԫ��
��ɾԪ�ؿ� 
5.�������
��������binary tree,��ÿ����㲻����2����������tree���� 
����List�����ࣺ 
1.ArrayList���ϣ� 
java.util.ArrayList�������ݴ洢�Ľṹ������ṹ��Ԫ����ɾ�������ҿ죬�����ճ�������ʹ�����Ĺ���Ϊ��ѯ���ݡ��������ݣ����� ArrayList ����õļ��ϡ�������Ա����ʱ�ǳ������ʹ��ArrayList����κ����󣬲����Ͻ��������÷��ǲ��ᳫ�ġ� 
2.LinkedList���ϣ� 
java.util.LinkedList�������ݴ洢�Ľṹ������ṹ������Ԫ����ӡ�ɾ���ļ���
public void addFirst(E e):��ָ��Ԫ�ز�����б�Ŀ�ͷ��
public void addLast(E e):��ָ��Ԫ����ӵ����б�Ľ�β����
public E getFirst() :���ش��б�ĵ�һ��Ԫ�ء�
public E getLast() :���ش��б�����һ��Ԫ�ء�
public E removeFirst():�Ƴ������ش��б�ĵ�һ��Ԫ�ء�
public E removeLast():�Ƴ������ش��б�����һ��Ԫ�ء�
public E pop() :�Ӵ��б�����ʾ�Ķ�ջ������һ��Ԫ�ء�
public void push(E e) :��Ԫ��������б�����ʾ�Ķ�ջ
public boolean isEmpty()������б�����Ԫ�أ��򷵻�true��

 while (!linkedList.isEmpty()){
         System.out.println(linkedList.pop());
     }
����Set�ӿ� 
1.HashSet���Ͻ��� 
ava.util.HashSet�� Set�ӿڵ�һ��ʵ���࣬�����洢��Ԫ���ǲ����ظ��ģ�����Ԫ�ض��������(����ȡ˳��һ��)�� 
2.HashSet�洢�Զ�������Ԫ�� 
��HashSet�д���Զ�������Ԫ��ʱ����Ҫ��д�����е�hashCode��equals�����������Լ��ıȽϷ�ʽ�����ܱ�֤HashSet�����еĶ���Ψһ�� 
3.LinkedHashSet 
����֪��HashSet��֤Ԫ��Ψһ������Ԫ�ش�Ž�ȥ��û��˳��ģ���ô����Ҫ��֤������ô���أ���HashSet������һ������ java.util.LinkedHashSet����������͹�ϣ����ϵ�һ�����ݴ洢�ṹ��

public static int getSum(int... arr) {
    int sum = 0;
    for (int a : arr) {
        sum += a;
    }
    return sum;
}
�ġ�Collections 
1.���ù��ܣ� 
- java.utils.Collections�Ǽ��Ϲ����࣬�����Լ��Ͻ��в��������ַ������£� 
- public static boolean addAll(Collection c, T... elements) :�����������һЩԪ�� 
- public static void shuffle(List list):���Ҽ���˳�� 
- public static void sort(List list):��������Ԫ�ذ���Ĭ�Ϲ������� 
- public static void sort(List list��Comparator ):��������Ԫ�ذ���ָ���������� 
2.Comparator�Ƚ���

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
3.Comparable��Comparator�����ӿڵ�����

Comparable��ǿ�ж�ʵ������ÿ����Ķ���������������������򱻳�Ϊ�����Ȼ�������compareTo��������Ϊ������Ȼ�ȽϷ�����ֻ��������ʵ��compareTo()һ�Σ����ܾ����޸���Ĵ���ʵ���Լ���Ҫ������ʵ�ִ˽ӿڵĶ����б������飩����ͨ��Collections.sort����Arrays.sort�������Զ����򣬶��������������ӳ���еļ������򼯺��е�Ԫ�أ�����ָ���Ƚ�����

Comparatorǿ�ж�ĳ����������������򡣿��Խ�Comparator ���ݸ�sort��������Collections.sort�� Arrays.sort�����Ӷ�����������˳����ʵ�־�ȷ���ơ�������ʹ��Comparator������ĳЩ���ݽṹ��������set������ӳ�䣩��˳�򣬻���Ϊ��Щû����Ȼ˳��Ķ���collection�ṩ����