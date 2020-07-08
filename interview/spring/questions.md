### 为什么要使用 spring？
- Spring可以整合很多各式各样的框架，并能很好的集成
- spring支持aop编程（spring提供面向切面编程，可以很方便的实现对程序进行权限拦截和运行监控等功能）
- 声明式事务的支持（通过配置就完成对事务的支持，不需要手动编程）
- 方便程序的测试，spring 对junit4支持，可以通过注解方便的测试spring 程序
- 降低java EE的使用难度(例如：jdbc，远程调用都提供了封装) 

### 解释一下什么是 aop？
AOP即面向切面编程。使用AOP技术，可以将一些系统性相关的编程工作，独立提取出来，独立实现，然后通过切面切入进系统。从而避免了在业务逻辑的代码中混入很多的系统相关的逻辑——比如权限管理，事务管理，日志记录等等。

### 解释一下什么是 ioc？
控制反转，对于 spring 框架来说，就是由 spring 来负责控制对象的生命周期和对象间的关系

### spring 有哪些主要模块？
- Spring core
    
    Core模块是Spring的核心类库，Spring的所有功能都依赖于该类库，Core主要实现IOC功能，Sprign的所有功能都是借助IOC实现的。
- AOP

    AOP模块是Spring的AOP库，提供了AOP（拦截器）机制，并提供常用的拦截器，供用户自定义和配置。
- ORM

    Spring 的ORM模块提供对常用的ORM框架的管理和辅助支持，Spring支持常用的Hibernate，ibtas，jdao等框架的支持，Spring本身并不对ORM进行实现，仅对常见的ORM框架进行封装，并对其进行管理
- DAO
    
    Spring 提供对JDBC的支持，对JDBC进行封装，允许JDBC使用Spring资源，并能统一管理JDBC事物，并不对JDBC进行实现。（执行sql语句）
- WEB

    WEB模块提供对常见框架如Struts1，WEBWORK（Struts 2），JSF的支持，Spring能够管理这些框架，将Spring的资源注入给框架，也能在这些框架的前后插入拦截器。
- Context

    Context模块提供框架式的Bean访问方式，其他程序可以通过Context访问Spring的Bean资源，相当于资源注入。
- MVC

    WEB MVC模块为Spring提供了一套轻量级的MVC实现，在Spring的开发中，我们既可以用Struts也可以用Spring自己的MVC框架，相对于Struts，Spring自己的MVC框架更加简洁和方便。
### spring 常用的注入方式有哪些？
- 注解 @Autowired，@Resource
- 构造方法注入

### spring 中的 bean 是线程安全的吗？
#### 原型Bean
对于原型Bean,每次创建一个新对象，也就是线程之间并不存在Bean共享，自然是不会有线程安全的问题。
#### 单例Bean
对于单例Bean,所有线程都共享一个单例实例Bean,因此是存在资源的竞争。如果单例Bean,是一个无状态Bean，也就是线程中的操作不会对Bean的成员执行查询以外的操作，那么这个单例Bean是线程安全的。比如Spring mvc 的 Controller、Service、Dao等，这些Bean大多是无状态的，只关注于方法本身

- 有状态就是有数据存储功能
- 无状态就是不会保存数据

### spring 支持几种 bean 的作用域？
- singleton:单例，默认作用域。
- prototype:原型，每次创建一个新对象。
- request:请求，每次Http请求创建一个新对象，适用于WebApplicationContext环境下。
- session:会话，同一个会话共享一个实例，不同会话使用不用的实例。
- global-session:全局会话，所有会话共享一个实例。

### spring 自动装配 bean 有哪些方式？
- no：不进行自动装配，手动设置Bean的依赖关系。
- byName：根据Bean的名字进行自动装配。
- byType：根据Bean的类型进行自动装配。
- constructor：类似于byType，不过是应用于构造器的参数，如果正好有一个Bean与构造器的参数类型相同则可以自动装配，否则会导致错误。
- autodetect：如果有默认的构造器，则通过constructor的方式进行自动装配，否则使用byType的方式进行自动装配。

### spring 事务实现方式有哪些？
- 编程式事务管理对基于 POJO 的应用来说是唯一选择。我们需要在代码中调用beginTransaction()、commit()、rollback()等事务管理相关的方法，这就是编程式事务管理。
- 基于 TransactionProxyFactoryBean的声明式事务管理
- 基于 @Transactional 的声明式事务管理
- 基于Aspectj AOP配置事务

### 说一下 spring 的事务隔离？

### 说一下 spring mvc 运行流程？
- 客户端（浏览器）发送请求，直接请求到 DispatcherServlet；
- DispatcherServlet 根据请求信息调用 HandlerMapping，解析请求对应的 Handler；
- 解析到对应的 Handler（也就是平常说的 Controller 控制器）后，开始由 HandlerAdapter 适配器处理；
- HandlerAdapter 会根据 Handler 来调用真正的处理器开处理请求，并处理相应的业务逻辑；
- 处理器处理完业务后，会返回一个 ModelAndView 对象，Model 是返回的数据对象，View 是个逻辑上的 View；
- ViewResolver 会根据逻辑 View 查找实际的 View；
- DispaterServlet 把返回的 Model 传给 View（视图渲染）；
- 把 View 返回给请求者（浏览器）。

### spring mvc 有哪些组件？
- 前端控制器（DispatcherServlet）：主要负责捕获来自客户端的请求和调度各个组件。
- 处理器映射器（HandlerMapping）：根据url查找后端控制器Handler。
- 处理器适配器（HandlerAdapter）：执行后端控制器（Handler），拿到后端控制器返回的结果ModelAndView后将结果返回给前端控制器DispatcherServlet。
- 后端控制器（处理器）（Handler）：主要负责处理前端请求，完成业务逻辑，生成ModelAndView对象返回给HandlerAdapter。
- 视图解析器（ViewResolver）：主要负责将从DispatcherServlet中拿到的ModelAndView对象进行解析，生成View对象返回给DispatcherServlet。

### @RequestMapping 的作用是什么？
用来标识http请求地址

### @Autowired 的作用是什么？
Bean注入。配合@Qualifier指定按照名称注入bean