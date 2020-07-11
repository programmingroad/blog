### throw 和 throws 的区别？
throw用在方法实现中，throws用在方式声明中。前者只能抛出一种异常，后者可以抛出多种异常

### final、finally、finalize 有什么区别？
- final：修饰符，可以修饰类，方法，变量
- finally：异常处理的时候，提供finally来执行清除的操作
- finalize：Object中的一个方法，当垃圾回收器将要回收对象所占内存之前被调用

### try-catch-finally 中哪个部分可以省略？
catch/finally

### try-catch-finally 中，如果 catch 中 return 了，finally 还会执行吗？
会

### 常见的异常类有哪些？
- NullPointerException 当应用程序试图访问空对象时，则抛出该异常。
- SQLException 提供关于数据库访问错误或其他错误信息的异常。
- IndexOutOfBoundsException指示某排序索引（例如对数组、字符串或向量的排序）超出范围时抛出。 
- NumberFormatException当应用程序试图将字符串转换成一种数值类型，但该字符串不能转换为适当格式时，抛出该异常。
- FileNotFoundException当试图打开指定路径名表示的文件失败时，抛出此异常。
- IOException当发生某种I/O异常时，抛出此异常。此类是失败或中断的I/O操作生成的异常的通用类。
- ClassCastException当试图将对象强制转换为不是实例的子类时，抛出该异常。
- ArrayStoreException试图将错误类型的对象存储到一个对象数组时抛出的异常。
- IllegalArgumentException 抛出的异常表明向方法传递了一个不合法或不正确的参数。
- ArithmeticException当出现异常的运算条件时，抛出此异常。例如，一个整数“除以零”时，抛出此类的一个实例。 
- NegativeArraySizeException如果应用程序试图创建大小为负的数组，则抛出该异常。
- NoSuchMethodException无法找到某一特定方法时，抛出该异常。
- SecurityException由安全管理器抛出的异常，指示存在安全侵犯。
- UnsupportedOperationException当不支持请求的操作时，抛出该异常。
- RuntimeExceptionRuntimeException 是那些可能在Java虚拟机正常运行期间抛出的异常的超类。
