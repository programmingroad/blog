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

### 如何实现数组和 List 之间的转换？

### ArrayList 和 Vector 的区别是什么？

### Array 和 ArrayList 有何区别？

### 在 Queue 中 poll()和 remove()有什么区别？

### 哪些集合类是线程安全的？

### 迭代器 Iterator 是什么？

### Iterator 怎么使用？有什么特点？

### Iterator 和 ListIterator 有什么区别？

### 怎么确保一个集合不能被修改？