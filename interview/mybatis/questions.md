### mybatis 中 #{}和 ${}的区别是什么？
传入的参数在SQL中显示为字符串，#方式能够很大程度防止sql注入；$传入的参数在SqL中直接显示为传入的值，$方式无法防止Sql注入.

### mybatis 有几种分页方式？
- 数组分页
- sql分页
- 拦截器分页
- RowBounds分页

### RowBounds 是一次性查询全部结果吗？为什么？
RowBounds 表面是在“所有”数据中检索数据，其实并非是一次性查询出所有数据，因为 MyBatis 是对 jdbc 的封装，在 jdbc 驱动中有一个 Fetch Size 的配置，它规定了每次最多从数据库查询多少条数据，假如你要查询更多数据，它会在你执行 next()的时候，去查询更多的数据。就好比你去自动取款机取 10000 元，但取款机每次最多能取 2500 元，所以你要取 4 次才能把钱取完。只是对于 jdbc 来说，当你调用 next()的时候会自动帮你完成查询工作。这样做的好处可以有效的防止内存溢出。

### mybatis 逻辑分页和物理分页的区别是什么？
- 逻辑分页是一次性查询很多数据，然后再在结果中检索分页的数据。这样做弊端是需要消耗大量的内存、有内存溢出的风险、对数据库压力较大。
- 物理分页是从数据库查询指定条数的数据，弥补了一次性全部查出的所有数据的种种缺点，比如需要大量的内存，对数据库查询压力较大等问题。

### mybatis 是否支持延迟加载？延迟加载的原理是什么？
MyBatis 支持延迟加载，设置 lazyLoadingEnabled=true 即可。

延迟加载的原理的是调用的时候触发加载，而不是在初始化的时候就加载信息。比如调用 a. getB(). getName()，这个时候发现 a. getB() 的值为 null，此时会单独触发事先保存好的关联 B 对象的 SQL，先查询出来 B，然后再调用 a. setB(b)，而这时候再调用 a. getB(). getName() 就有值了，这就是延迟加载的基本原理。

### 说一下 mybatis 的一级缓存和二级缓存？
缓存目的是为了减少对数据库的访问次数，提升数据库的执行效率。

- 一级缓存(默认开启)也叫sqlSession级别的缓存 ，也就是在同一个sqlSession内执行两次多次相同结果的查询语句，只会在第一次时发出sql查询数据库的数据，然后之后每次从一级缓存中查询数据返回。
- 是mapper级别的缓存，也就是多个sqlSession之间可以实现数据的共享。

开启二级缓存数据查询流程：二级缓存 -> 一级缓存 -> 数据库。

缓存更新机制：当某一个作用域(一级缓存 Session/二级缓存 Mapper)进行了C/U/D 操作后，默认该作用域下所有 select 中的缓存将被 clear。

### mybatis 和 hibernate 的区别有哪些？
- 灵活性：MyBatis 更加灵活，自己可以写 SQL 语句，使用起来比较方便。
- 可移植性：MyBatis 有很多自己写的 SQL，因为每个数据库的 SQL 可以不相同，所以可移植性比较差。
- 学习和使用门槛：MyBatis 入门比较简单，使用门槛也更低。
- 二级缓存：hibernate 拥有更好的二级缓存，它的二级缓存可以自行更换为第三方的二级缓存

### mybatis 有哪些执行器（Executor）？
- SimpleExecutor：每执行一次update或select，就开启一个Statement对象，用完立刻关闭Statement对象。
- ReuseExecutor：执行update或select，以sql作为key查找Statement对象，存在就使用，不存在就创建，用完后，不关闭Statement对象，而是放置于Map内，供下一次使用。简言之，就是重复使用Statement对象。
- BatchExecutor：执行update（没有select，JDBC批处理不支持select），将所有sql都添加到批处理中（addBatch()），等待统一执行（executeBatch()），它缓存了多个Statement对象，每个Statement对象都是addBatch()完毕后，等待逐一执行executeBatch()批处理。与JDBC批处理相同。

### mybatis 分页插件的实现原理是什么？
基于拦截器，在sql执行前，拦截sql，设置分页参数，然后执行重写后的sql，从而实现分页

