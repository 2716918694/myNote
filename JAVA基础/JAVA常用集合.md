## JAVA 集合框架

集合框架设计必须满足以下几个目标

- 该框架必须是高性能的
- 该框架允许不同类型的集合，以类的方式工作，具有高度的互操作性
- 对一个集合的拓展和适应必须是简单的

为此，整个集合框架就围绕一组标准接口设计。

>![](./java集合.gif "Java集合框架图")
>从上面的集合框架可以看到，Java集合框架主要包括两种类型的容器，一种是Collection，存储一个元素集合，另一种是Map,存储键/值对映射。Collection接口有三个子类型：List、Set和Queue。再下面是一些抽象类，最后是具体的实现类，常用的有ArrayList、LinkedList、HashSet、LinkedHashSet、HashMap、LinkedHashMap等等。

你也可以通过以上接口实现自己的集合。

集合框架是一个用来代表和操纵集合的统一架构。所有集合框架都会包含如下内容：

- **接口：** 是代表集合的抽象数据类型。比如Collection、List、Set、Map等。之所以定义多个接口，是为了以不同的方式操纵集合对象
- **实现(类)：** 是集合接口的具体实现。从本质上讲，它们是可重复使用的数据结构，例如：ArrayList、LinkedList、HashSet、HashMap等
- **算法** 是实现集合接口的对象里的方法执行的一些有用的计算，例如：搜索和排序。这些算法被称为多态，那是因为相同的方法可以在相似的接口上有着不同的实现

除了集合，该框架也定义了几个Map接口和类。Map里存储的是键/值对,尽管Map不是集合，但是它们完全整合在集合中。

>![](./java-coll.png "")
>Java集合框架提供了一套性能优良，使用方便的接口和类，java集合框架位于java.util包中，所有使用集合框架时需要引入对应的包/类

***

## 集合接口

集合框架定义了一些接口，本节提供了每个接口的概述：

序号|接口描述
:-:|:-
&nbsp;&nbsp;&nbsp;1&nbsp;&nbsp;&nbsp;|Collection接口<br>Collection 是最基本的集合接口，一个Collection代表一组Object，即Collection的元素，java不提供直接继承自Collection的类，只提供继承于它的子接口List/Set<br>Collection 接口存储一组不唯一，无序的对象。
2|List接口<br>List 接口是一个有序的Collection，使用此接口能精确的控制每个接口插入的位置，能够通过索引（元素在List中的位置，类似于数组下标）来访问List的元素，第一个元素的索引为0，而且允许有相同元素。<br>List 接口存储一组不唯一，有序（顺序插入）的对象。
3|Set接口<br>Set 具有和Collection完全一样的接口，只是行为上不同，Set不保存重复的元素。<br>Set 接口存储一组唯一，无序的对象。
4|SortedSet接口<br>继承于Set，保存有序集合。
5|Map接口<br>Map 接口存储一组键/值对象,提供key(键)到value(值)的映射。
6|Map Entry<br>描述在一个Map中的元素（键/值对），是Map的一个内部类。
7|SortedMap<br>继承于Map，使Key保持在升序排列。
8|Enumeration<br>这是一个传统的接口和定义的方法，通过它可以枚举（一次获得一个）对象集合中的元素。这个传统接口已被迭代器取代

**Set和List的区别**

1. Set接口实例存储的是无序的，不重复的数据。List接口实例存储的是有序的，可以重复的元素。
2. Set检索效率低下，增删效率高，插入和删除不会引起元素位置的改变<实现类有HashSet、TreeSet>。
3. List和数组类似，可以动态增长，根据实际存储的数据的长度自动增长List的长度。查找元素效率高，插入删除效率低，因为会引起其他元素位置改变<实现类有ArrayList、LinkedList、Vector>。

***

## 集合实现类（集合类）

Java 提供了一套实现了Collection接口的标准集合类。其中一些是具体类，这些类可以直接拿来使用，而另外一些是抽象类，提供了接口的部分实现。

标准集合类汇总于下表：

序号|类描述
:-:|:-
&nbsp;&nbsp;&nbsp;1&nbsp;&nbsp;&nbsp;|AbstractCollection<br>实现了大部分的接口。
2|AbstractList<br>继承于AbstractCollection并且实现了大部分List接口。
3|AbstractSequentialList<br>继承于AbstractList，提供了对数据元素的链式访问而不是随机访问。
4|LinkedList<br>该类实现了List接口，允许有空元素（Null），主要用于创建链表数据结构，该类没有同步方法，如果多个线程同时访问一个List则必须自己实现访问同步，解决方法就是创建List时候构造一个同步List。例如:<br>&nbsp;&nbsp;`List list = Collection.synchronizedList(new LinkedList(...));`<br>LinkedList 查找效率低。
5|**ArrayList**<br>该类也是实现了List接口，实现了可变大小的数组。
6|AbstractSet<br>继承于AbstractCollection并且实现了大部分Set接口。
7|**HashSet**<br>该类也是实现了Set接口，不允许出现重复元素，不保证集合中元素的顺序，允许包含值为null的元素，但最多只能一个。
8|LinkedHashSet<br>具有可预知迭代顺序的哈希表和链接列表实现。
9|TreeSet<br>该类实现了Set接口，可以实现排序等功能。
10|AbstractMap<br>实现了大部分的Map接口
11|**HashMap**<br>HashMap是一个散列表，它存储的内容是键值对（key-value）映射。<br>该类实现了Map接口，根据键的HashCode值存储数据，具有很快的访问速度，最多允许一条记录的键为null,不支持线程同步。
12|TreeMap<br>继承了AbstractMap，并且是红黑树算法的实现。

***
## 常用集合API

### ArrayList
