### 并行和并发有什么区别？
- 并行：多个cpu同一时刻处理多个任务
- 并发：一个cpu在同一个时间段内处理多个任务

### 线程和进程的区别？
- 进程是资源分配最小单位，线程是程序执行的最小单位
- 一个进程可以有多个线程，线程需要在进程下运行
- 不同进程间数据很难共享，同一进程下不同线程数据易共享
- 进程执行开销大，线程执行开销小。

### 守护线程是什么？
守护线程是个服务线程。比如：垃圾回收线程。

当 JVM 中不存在任何一个正在运行的非守护线程时，则 JVM 进程即会退出

守护线程拥有自动结束自己生命周期的特性，而非守护线程不具备这个特点

### 创建线程有哪几种方式？
- 继承Thread
- 实现Runnable接口
- 实现Callable接口

### 说一下 runnable 和 callable 有什么区别？
- 实现Callable接口的任务线程能返回执行结果；而实现Runnable接口的任务线程不能返回结果；
- Callable接口的call()方法允许抛出异常；而Runnable接口的run()方法的异常只能在内部消化，不能继续上抛

### 线程有哪些状态？
- 新建(NEW)：新创建了一个线程对象。
- 可运行(RUNNABLE)：线程对象创建后，其他线程(比如main线程）调用了该对象的start()方法。该状态的线程位于可运行线程池中，等待被线程调度选中，获取cpu 的使用权 。
- 运行(RUNNING)：可运行状态(runnable)的线程获得了cpu 时间片（timeslice） ，执行程序代码。
- 阻塞(BLOCKED)：阻塞状态是指线程因为某种原因放弃了cpu 使用权，也即让出了cpu timeslice，暂时停止运行。直到线程进入可运行(runnable)状态，才有机会再次获得cpu timeslice 转到运行(running)状态。阻塞的情况分三种： 
    - 等待阻塞：运行(running)的线程执行o.wait()方法，JVM会把该线程放入等待队列(waitting queue)中。
    - 同步阻塞：运行(running)的线程在获取对象的同步锁时，若该同步锁被别的线程占用，则JVM会把该线程放入锁池(lock pool)中。
    - 其他阻塞：运行(running)的线程执行Thread.sleep(long ms)或t.join()方法，或者发出了I/O请求时，JVM会把该线程置为阻塞状态。当sleep()状态超时、join()等待线程终止或者超时、或者I/O处理完毕时，线程重新转入可运行(runnable)状态。
- 死亡(DEAD)：线程run()、main() 方法执行结束，或者因异常退出了run()方法，则该线程结束生命周期。死亡的线程不可再次复生。

### sleep() 和 wait() 有什么区别？
sleep() 和 wait() 的区别就是 调用sleep方法的线程不会释放对象锁，而调用wait() 方法会释放对象锁

### notify()和 notifyAll()有什么区别？
当有线程调用了对象的 notifyAll()方法（唤醒所有 wait 线程）或 notify()方法（只随机唤醒一个 wait 线程），被唤醒的的线程便会进入该对象的锁池中，锁池中的线程会去竞争该对象锁。也就是说，调用了notify后只要一个线程会由等待池进入锁池，而notifyAll会将该对象等待池内的所有线程移动到锁池中，等待锁竞争

### 线程的 run()和 start()有什么区别？
调用start方法方可启动线程，而run方法只是thread的一个普通方法调用，并没有启动线程

### 创建线程池有哪几种方式？
- newCachedThreadPool（），它是用来处理大量短时间工作任务的线程池，具有几个鲜明特点：它会试图缓存线程并重用，当无缓存线程可用时，就会创建新的工作线程；如果线程闲置时间超过60秒，则被终止并移除缓存；长时间闲置时，这种线程池，不会消耗什么资源。其内部使用SynchronousQueue作为工作队列。
- newFixedThreadPool（int nThreads），重用指定数目（nThreads）的线程，其背后使用的是无界的工作队列，任何时候最多有nThreads个工作线程是活动的。这意味着，如果任务数量超过了活动线程数目，将在工作队列中等待空闲线程出现；如果工作线程退出，将会有新的工作线程被创建，以补足指定数目nThreads。
- newSingleThreadExecutor()，它的特点在于工作线程数目限制为1，操作一个无界的工作队列，所以它保证了所有的任务都是被顺序执行，最多会有一个任务处于活动状态，并且不予许使用者改动线程池实例，因此可以避免改变线程数目。
- newSingleThreadScheduledExecutor()和newScheduledThreadPool(int corePoolSize)，创建的是个ScheduledExecutorService，可以进行定时或周期性的工作调度，区别在于单一工作线程还是多个工作线程。
- newWorkStealingPool(int parallelism)，这是一个经常被人忽略的线程池，Java 8 才加入这个创建方法，其内部会构建ForkJoinPool，利用Work-Stealing算法，并行地处理任务，不保证处理顺序。

### 线程池都有哪些状态？
- RUNNING：这是最正常的状态，接受新的任务，处理等待队列中的任务。线程池的初始化状态是RUNNING。线程池被一旦被创建，就处于RUNNING状态，并且线程池中的任务数为0。
- SHUTDOWN：不接受新的任务提交，但是会继续处理等待队列中的任务。调用线程池的shutdown()方法时，线程池由RUNNING -> SHUTDOWN。
- STOP：不接受新的任务提交，不再处理等待队列中的任务，中断正在执行任务的线程。调用线程池的shutdownNow()方法时，线程池由(RUNNING or SHUTDOWN ) -> STOP。
- TIDYING：所有的任务都销毁了，workCount 为 0，线程池的状态在转换为 TIDYING 状态时，会执行钩子方法 terminated()。因为terminated()在ThreadPoolExecutor类中是空的，所以用户想在线程池变为TIDYING时进行相应的处理；可以通过重载terminated()函数来实现。 

当线程池在SHUTDOWN状态下，阻塞队列为空并且线程池中执行的任务也为空时，就会由 SHUTDOWN -> TIDYING。

当线程池在STOP状态下，线程池中执行的任务为空时，就会由STOP -> TIDYING。
- TERMINATED：线程池处在TIDYING状态时，执行完terminated()之后，就会由 TIDYING -> TERMINATED。

### 线程池中 submit()和 execute()方法有什么区别？
- submit()有返回值。
- execute没有返回值。
- submit() 的返回值 Future 调用get方法时，可以捕获处理异常

### 在 java 程序中怎么保证多线程的运行安全？
分布式锁，synchronied关键字

### 多线程锁的升级原理是什么？

### 什么是死锁？
线程死锁是指由于两个或者多个线程互相持有对方所需要的资源，导致这些线程处于等待状态，无法前往执行。

### 怎么防止死锁？


### ThreadLocal 是什么？有哪些使用场景？

### 说一下 synchronized 底层实现原理？

### synchronized 和 volatile 的区别是什么？

### synchronized 和 Lock 有什么区别？

### synchronized 和 ReentrantLock 区别是什么？

### 说一下 atomic 的原理？