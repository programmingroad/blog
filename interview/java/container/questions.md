### java 容器都有哪些？
List,Map,Set,LinkedList,ArrayList,HashMap,HashSet

### Collection 和 Collections 有什么区别？
- Collection是一个接口,List,Set继承了collection
- Collections是一个包装类，可以看成一个工具类，提供了一些操作集合的方法

### List、Set、Map 之间的区别是什么？
- List: 有序集合，元素可重复
- Set: 不重复集合，LinkedHashSet按照插入排序，SortedSet可排序，HashSet无序
- Map: 键值对集合，存储键、值和之间的映射；Key无序，唯一；value 不要求有序，允许重复

### HashMap 和 Hashtable 有什么区别？
- HashMap: 非线程安全
- Hashtable: 线程安全
 
### 如何决定使用 HashMap 还是 TreeMap？
有顺序的话选择 TreeMap
一般情况下，没有顺序的话选择HashMap，会有更高的性能

### 说一下 HashMap 的实现原理？


### 说一下 HashSet 的实现原理？

### ArrayList 和 LinkedList 的区别是什么？
1、数据结构不同

ArrayList是Array(动态数组)的数据结构，LinkedList是Link(链表)的数据结构。

2、效率不同

当随机访问List（get和set操作）时，ArrayList比LinkedList的效率更高，因为LinkedList是线性的数据存储方式，所以需要移动指针从前往后依次查找。

当对数据进行增加和删除的操作(add和remove操作)时，LinkedList比ArrayList的效率更高，因为ArrayList是数组，所以在其中进行增删操作时，会对操作点之后所有数据的下标索引造成影响，需要进行数据的移动。

### 如何实现数组和 List 之间的转换？
数组转 List ，使用 JDK 中 java.util.Arrays 工具类的 asList 方法

List 转数组，使用 List 的toArray方法

### ArrayList 和 Vector 的区别是什么？

### Array 和 ArrayList 有何区别？

### 在 Queue 中 poll()和 remove()有什么区别？

### 哪些集合类是线程安全的？

### 迭代器 Iterator 是什么？

### Iterator 怎么使用？有什么特点？

### Iterator 和 ListIterator 有什么区别？

### 怎么确保一个集合不能被修改？