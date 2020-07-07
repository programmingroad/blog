### JDK和JRE什么区别？
- JRE：Java Runtime Environment（ java 运行时环境）。即java程序的运行时环境，包含了 java 虚拟机，java基础类库。
- JDK：Java Development Kit（ java 开发工具包）。即java语言编写的程序所需的开发工具包。JDK 包含了 JRE，同时还包括 java 源码的编译器 javac、监控工具 jconsole、分析工具 jvisualvm等。

### == 和 equals 的区别是什么？
- == 是关系运算符，equals() 是方法，结果都返回布尔值
- Object 的 == 和 equals() 比较的都是地址，作用相同

#### ==作用
- 基本类型，比较值是否相等
- 引用类型，比较内存地址值是否相等

#### equals()方法的作用：
- JDK 中的类(String)一般已经重写了 equals()，比较的是内容
- 自定义类如果没有重写 equals()，将调用父类（默认 Object 类）的 equals() 方法，Object 的 equals() 比较使用了 this == obj

### 两个对象的 hashCode()相同，则 equals()也一定为 true，对吗？
如果两个对象equals()方法相等则它们的hashCode返回值一定要相同，如果两个对象的hashCode返回值相同，但它们的equals()方法不一定相等。

### final 在 java 中有什么作用？
在Java中，final关键字可以用来修饰类、方法和变量

#### 修饰类
当用final修饰一个类时，表明这个类不能被继承

#### 修饰方法
当用final修饰一个方法时，表明这个方法不能被重写

#### 修饰变量
当用final修饰一个变量时，表明这个变量只能被赋值一次

### java 中的 Math.round(-1.5) 等于多少？
round函数是取最接近整数，如果遇到一样近，则取最大值。
- Math.round(-1.5) = -1
- Math.round(1.5) = 2

正数的round是四舍五入，负数的round是"五舍六入"

### String 属于基础的数据类型吗？
Java 中 8 种基础的数据类型：byte、short、char、int、long、float、double、boolean
String是常用的引用类型

### java 中操作字符串都有哪些类？它们之间有什么区别？
- String : 字符串是不可变的，对String类型的字符串做修改操作都是相当于重新创建对象
- StringBuffer : StringBuffer中的方法大部分都使用synchronized关键字修饰,所以StringBuffer是线程安全的,适合多线程下面使用
- StringBuilder : 线程不安全，性能高，适合单线程下面使用

### String str="i"与 String str=new String(“i”)一样吗？
因为内存的分配方式不一样。String str="i"的方式，Java 虚拟机会将其分配到常量池中；而 String str=new String(“i”)方式，则会被分到堆内存中。
- Java 虚拟机会将其分配到常量池中：常量池不会重复创建对象。
- 在String str1="i"中，把i值存在常量池，地址赋给str1。假设再写一个String str2="i"，则会把i的地址赋给str2，但是i对象不会重新创建，他们引用的是同一个地址值，共享同一个i内存。
- 分到堆内存中：堆内存会创建新的对象。
- 假设再写一个String str3=new String(“i”)，则会创建一个新的i对象，然后将新对象的地址值赋给str3。虽然str3和str1的值相同但是地址值不同。

### 如何将字符串反转？
使用 StringBuilder 或 StringBuffer 的 reverse 方法。

### String 类的常用方法都有那些？
equals，indexOf，lastIndexOf，charAt，startsWith，endsWith，length，substring，split

### 抽象类必须要有抽象方法吗？
- 抽象类必须有关键字abstract来修饰。
- 抽象类可以不含有抽象方法
- 如果一个类包含抽象方法，则该类必须是抽象类

### 普通类和抽象类有哪些区别？
- 普通类可以去实例化调用；抽象类不能被实例化。
- 普通类和抽象类都可以被继承，但是抽象类被继承后子类必须重写继承的方法，除非自类也是抽象类。

### 抽象类能使用 final 修饰吗？
不能

### 接口和抽象类有什么区别？
- 类实现接口，继承抽象类
- 接口只能做方法声明，抽象类中可以作方法声明，也可以做方法实现。
- 接口里定义的变量只能是公共的静态的常量，抽象类中的变量是普通变量。
- 抽象类和接口都是用来抽象具体对象的，但是接口的抽象级别最高。
- 抽象类可以有具体的方法和属性，接口只能有抽象方法和不可变常量。
- 抽象类主要用来抽象类别，接口主要用来抽象功能。

### java 中 IO 流分为几种？
- 按照流数据的流向：输入流，输出流；
- 按照流数据的格式：字节流，字符流；
- 按照流数据的包装过程：节点流，处理流。

### BIO、NIO、AIO 有什么区别？
- BIO (Blocking I/O): 同步阻塞I/O模式，数据的读取写入必须阻塞在一个线程内等待其完成。
- NIO (New I/O): NIO是一种同步非阻塞的I/O模型，
- AIO (Asynchronous I/O): AIO 也就是 NIO 2。在 Java 7 中引入了 NIO 的改进版 NIO 2,它是异步非阻塞的IO模型。

### Files的常用方法都有哪些？
- Files.exists() 检查文件路径是否存在
- Files.createFile() 创建文件
- Files.createDirectory() 创建文件夹
- Files.delete() 删除一个文件或者目录
- Files.copy()复制文件
- Files.move() 移动文件
- Files.size() 查看文件个数