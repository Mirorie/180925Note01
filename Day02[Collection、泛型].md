JiuYeDay02[Collection������]
һ��Collection���ù���

public boolean add(E e) �� �Ѹ����Ķ�����ӵ���ǰ������
public void clear() :��ռ��������е�Ԫ��
public boolean remove(E e) : �Ѹ����Ķ����ڵ�ǰ������ɾ��
public boolean contains(E e) : �жϵ�ǰ�������Ƿ���������Ķ���
public boolean isEmpty() : �жϵ�ǰ�����Ƿ�Ϊ��
public int size() : ���ؼ�����Ԫ�صĸ���
public Object[] toArray() : �Ѽ����е�Ԫ�أ��洢�������С�
����Iterator������

1.Iterator�ӿڣ�Iterator �ӿ�Ҳ��Java�����е�һԱ��������Collection Map �ӿ�������ͬ��Collection �ӿ���Map�ӿ���Ҫ���ڴ洢Ԫ�أ���Iterator��Ҫ���ڵ������ʣ���������Collection �е�Ԫ�أ����Iterator����Ҳ����Ϊ�������� 
?public Iterator iterator():��ȡ���϶�Ӧ�ĵ��������������������е�Ԫ��

2.��������Collection����Ԫ�ص�ͨ�û�ȡ��ʽ����ȡԪ��֮ǰ��Ҫ�жϼ�������û��Ԫ�أ�����У��Ͱ����Ԫ��ȡ�������������жϣ�������о���ȡ��������һֱ�Ѽ����е�����Ԫ��ȫ��ȡ��������ȡ����ʽרҵ�����Ϊ������

3.Iterator�ӿڵĳ��÷������£�

Public E next():���ص�������һ��Ԫ��
Public boolean hasNext():�������Ԫ�ؿ��Ե������򷵻�true
4.��ǿfor�� 
For(Ԫ�ص��������� ����:Collection����or����){ 
//д�������� 
}

��������

������ʱ�ڵ�ClassCastException��ת�Ƶ��˱���ʱ�ڱ���˱���ʧ�ܡ�
����������ǿת���鷳
1.�����ʽ�� 
���η�class ����<�����͵ı���>{} 
Class ArrayList{ }

2.���з��͵Ľӿڣ� 
���η� interface�ӿ���<�����͵ı���>{ }

3.����ͨ�������ʹ�÷�������߽ӿ�ʱ�����ݵ������У��������Ͳ�ȷ��������ͨ��ͨ�����ʾ������һ��ʹ�÷��͵�ͨ�����ֻ��ʹ��Object���еĹ��Է�����������Ԫ���������޷�ʹ�á� 
4.ͨ����߼�ʹ��--���޷��� 
��1�����͵����ޣ� 
��ʽ���������� �������� 
���壺ֻ�ܽ��ܸ����ͼ������� 
��2�����͵����ޣ� 
��ʽ���������� �������� 
���壺ֻ�ܽ��ܸ����ͼ��丸���� 
public static void getElement1(Collectioncoll){} 
public static void getElement2(Collectioncoll){}