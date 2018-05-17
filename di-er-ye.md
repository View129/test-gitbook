Collection接口是集合类的根接口，Java中没有提供这个接口的直接的实现类。但是却让其被继承产生了两个接口，就是Set和List。Set中不能包含重复的元素。List是一个有序的集合，可以包含重复的元素，提供了按索引访问的方式。Map接口是Java.util包中的另一个接口，它和Collection接口没有关系，是相互独立的，但是都属于集合类的一部分。Map包含了key-value对。Map不能包含重复的key，但是可以包含相同的value。

---

# Collecton接口：

```
Collection

├--List

│   ├---LinkedList

│   ├---ArrayList

│   └---Vector

│　       └---Stack

└--Set

├---TreeSet

├---EnumSet

└---HashSet

└---LinkedHashSet
```

---

# Set接口：

 Set里存放的对象是无序，不能重复的，集合中的对象不按特定的方式排序，只是简单地把对象加入集合中。

---

# HashSet类：
 当向其中放入元素时，会调用这个对象的hashCode\\(\\)来计算hashCode值。

·判断元素是否相等是根据equals\\(\\)和hashCode\\(\\)的返回值是否相等来判断的。

·如果重写了equals\\(\\)，那也应该重写hashCode\\(\\)，重写要保证equals返回true时，hashCode\\(\\)返回值的对比结果相同。

特点：

    1、不能保证元素顺序。    

    2、线程非安全。   

    3、集合元素可以是null，但最多只有一个，因为Set不允许有相同的元素。

---

# LinkedHashSet:

HashSet的一个子类使用链表维护元素的次序。

    ·依然不允许重复的元素。

---

# TreeSet类:

SortedSet接口的实现类，集合元素处于有序状态。

```
TreeSet中的有序状态：根据元素的实际大小而不是插入顺序排序

向TreeSet中添加元素时应注意：

        1、加入的元素都应该实现Comparable接口，否则无法调用compareTo\\(\\)方法进行比较，并引起ClassCastException

        2、元素调用compareTo\\(\\)方法时会先将其他元素转换成与与自己一样的类型后进行比较，所以TreeSet中的  元素必须是同                              一个类的实例，否则会引发ClassCastException
```

---

# EnumSet类:

专为枚举类设计，集合中所有元素必须是同一指定枚举类型的枚举值。  
    特点：

```
    1、以枚举值在枚举类中的定义顺序来决定排放顺序。

    2、不允许加入null，强行加入会引发NullPointerException

    3、不暴露任何构造方法来创建实例，只能通过提供的方法来创建EnumSet对象
```

---

# Set接口总结：

性能：EnumSet &gt; HashSet &gt; TreeSet

```
·EnumSet最快，但只能存放枚举类型。

·TreeSet比HashSet慢，因为TreeSet需要维护红黑树来保证元素的顺序。
```

注意：

```
1、三种都是线程不安全的，多线程环境下必须手动保证同步性。

2、必须小心操作可变对象。如果一个Set中的可变元素改变了自身状态导致

    Object1.equals\\(Object2\\)=true将导致一些问题。
```

---

# List接口：

元素有序、可重复的集合，每个集合元素都有自己的顺序索引

---

# LinkedList类：

LinkedList实现了List接口，允许null元素。

注意LinkedList没有同步方法。如果多个线程同时访问一个List，则必须自己实现访问同步。一种解决方法是在创建

List时构造一个同步的List：List list = Collections.synchronizedList\\(new LinkedList\\(...\\)\\);

ArrayList类：   ArrayList实现了可变大小的数组。它允许所有元素，包括null。

和LinkedList一样，ArrayList也是非同步的（unsynchronized）。

---

# MAP接口：

Map集合中存储的是键值对，键不能重复，值可以重复。根据键得到值，对map集合遍历时先得到键的set集合，对set  
集合进行遍历，得到相应的值。

```
Map

├--Hashtable

├--HashMap

└--WeakHashMap
```

---

# Hashtable类：

实现了Map接口，继承了Dictionary类。

·添加数据使用put\\(key,value\\)，获取数据使用get\\(key\\)

特点：

1、key和value不能为null

2、Hashtable类是线程安全的

牢记：要同时重写写equals方法和hashCode方法，而不要只重写其中一个。

---

# HashMap类：

特点：

1、key和value可以为null  

2、HashMap类是线程不安全的

---

# WeakHashMap类：

WeakHashMap是一种改进的HashMap，它对key实行“弱引用”，如果一个key不再被外部所引用，

那么该key可以被GC回收。

---

# 

# 



