### Java SE 和 Java EE 的区别
- JavaSE通常是指Java Standard Edition，Java标准版，就是一般Java程序的开发就可以(如桌面程序)，可以看作是JavaEE的子集。
- JavaEE是指Java Enterprise Edition，Java企业版，多用于企业级开发，包括web开发等等。也叫J2EE。

### 负载均衡的算法有哪些
- 轮询法：很好理解,将请求按照顺序轮流的分配到服务器上,他均衡的对待每一台后端的服务器,不关心服务器的的连接数和负载情况.
- 随机法：通过系统的随机函数,根据后端服务器列表的大小来随机获取其中的一台来访问,随着调用量的增大,实际效果越来越近似于平均分配到没一台服务器.和轮询的效果类似,
- 源地址hash法：源地址hash法的思想是获取客户端访问的ip地址,通过hash函数计算出一个hash值,用该hash值对服务器列表的大小进行取模运算,得到的值就是要访问的服务器的序号
- 加权轮询法：刚刚有说道过,不同的服务器性能不同,所以不能一概而论,需要给性能低的服务器给比较低的权重,性能高的给跟高的权重
- 加权随机法：与加权轮询法类似，加权随机法也是根据后端服务器不同的配置和负载情况来配置不同的权重。不同的是，它是按照权重来随机选择服务器的，而不是顺序。

### linux命令： 查看文件夹大小
du -sh directory

### Java EE 的核心技术有哪些
1、EJB(Enterprise JavaBean)

JAVAEE技术之所以赢得媒体广泛重视的原因之一就是EJB。它们提供了一个框架来开发和实施分布式商务逻辑，由此很显著地简化了具有可伸缩性和高度复杂的企业级应用的开发。

EJB规范定义了EJB组件在何时如何与它们的容器进行交互作用。容器负责提供公用的服务，例如目录服务、事务管理、安全性、资源缓冲池以及容错性。但这里值得注意的是，EJB并不是实现JAVAEE的唯一途径。

正是由于JAVAEE的开放性，使得有的厂商能够以一种和EJB平行的方式来达到同样的目的。

2、JNDI(Java Name and Directory Interface)

JNDI API被用于执行名字和目录服务。它提供了一致的模型来存取和操作企业级的资源如DNS和LDAP，本地文件系统，或应用服务器中的对象。

3、JDBC(Java Database Connectivity)

JDBC API为访问不同的数据库提供了一种统一的途径，象ODBC一样，JDBC对开发者屏蔽了一些细节问题，另外，JDCB对数据库的访问也具有平台无关性。

4、RMI(Remote Method Invoke)

正如其名字所表示的那样，RMI协议调用远程对象上方法。它使用了序列化方式在客户端和服务器端传递数据。RMI是一种被EJB使用的更底层的协议。

5、Java IDL/CORBA

在Java IDL的支持下，开发人员可以将Java和CORBA集成在一起。他们可以创建Java对象并使之可在CORBA ORB中展开, 或者他们还可以创建Java类并作为和其它ORB一起展开的CORBA对象的客户。后一种方法提供了另外一种途径，通过它Java可以被用于将你的新的应用和旧的系统相集成。

6、JSP(Java Server Pages)

JSP页面由html代码和嵌入其中的java代码所组成。服务器在页面被客户端所请求以后对这些Java代码进行处理，然后将生成的HTML页面返回给客户端的浏览器。

7、Java Servlet

Servlet是一种小型的java程序，它扩展了Web服务器的功能。作为一种服务器端的应用，当被请求时开始执行，这和CGI Perl脚本很相似。

Servlet提供的功能大多与JSP类似，不过实现的方式不同。JSP通常是大多数HTML代码中嵌入少量的Java代码，而servlets全部由Java写成并且生成HTML。

8、XML(Extensible Markup Language)

XML是一种可以用来定义其它标记语言的语言。它被用来在不同的商务过程中共享数据。 XML的发展和Java是相互独立的，但是，它和Java具有的相同目标正是平台独立性。通过将Java和XML的组合，您可以得到一个完美的具有平台独立性的解决方案。

9、JMS(Java Message Service)

JMS是用于和面向消息的中间件相互通信的应用程序接口(API)。它既支持点对点的域，有支持发布/订阅(publish/subscribe)类型的域，并且提供对下列类型的支持：经认可的消息传递,事务型消息的传递，一致性消息和具有持久性的订阅者支持。JMS还提供了另 一种方式来对您的应用与旧的后台系统相集成。

10、JTA(Java Transaction Architecture)

JTA定义了一种标准的API，应用系统由此可以访问各种事务监控。

11、JTS(Java Transaction Service)

JTS是CORBA OTS事务监控的基本的实现。JTS规定了事务管理器的实现方式。该事务管理器是在高层支持Java Transaction API (JTA)规范，并且在较底层实现OMG OTS specification的Java映像。JTS事务管理器为应用服务器、资源管理器、独立的应用以及通信资源管理器提供了事务服务。

12、JavaMail

JavaMail是用于存取邮件服务器的API，它提供了一套邮件服务器的抽象类。不仅支持SMTP服务器，也支持IMAP服务器。

13、JAF(JavaBeans Activation Framework)

JavaMail利用JAF来处理MIME编码的邮件附件。MIME的字节流可以被转换成Java对象，或者转换自Java对象。大多数应用都可以不需要直接使用JAF。

### 边检项目架构

### ConcurrentHashMap 和 HashMap有什么区别

### 序列化和反序列化的实现
若一个类仅仅实现了Serializable接口，则可以按照以下方式进行序列化和反序列化。
- ObjectOutputStream采用默认的序列化方式，对该类对象的非transient的实例变量进行序列化。 
- ObjectInputStream采用默认的反序列化方式，对该类对象的非transient的实例变量进行反序列化。