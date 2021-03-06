# 目录
* [面试题](#面试题)
* [面试技巧](#面试技巧)

### 面试题
* [SpringMVC 说说过滤器、监听器、拦截器有啥区别]()
* [SpringBoot系列](https://github. com/zhonghuasheng/Tutorial/issues?q=label%3ASpringBoot+)
    * [SpringBoot 的启动原理](https://github. com/zhonghuasheng/Tutorial/issues/185)
#### Java 基础
> 什么是面向对象?

先讲一下面向过程与面向对象编程
1. 对比说明面向对象的优点
2. 说说面向对象的三个特征：封装、继承、多态
先讲一下面向过程:
面向过程就是分析出解决问题所需要的步骤，然后用函数把这些步骤一步一步实现，使用的时候一个一个依次调用就可以了；面向对象是把构成问题事物分解成各个对象，建立对象的目的不是为了完成一个步骤，而是为了描叙某个事物在整个解决问题的步骤中的行为。

可以拿生活中的实例来理解面向过程与面向对象，例如五子棋，面向过程的设计思路就是首先分析问题的步骤：1、开始游戏，2、黑子先走，3、绘制画面，4、判断输赢，5、轮到白子，6、绘制画面，7、判断输赢，8、返回步骤2，9、输出最后结果。把上面每个步骤用不同的方法来实现。

如果是面向对象的设计思想来解决问题。面向对象的设计则是从另外的思路来解决问题。整个五子棋可以分为1、黑白双方，这两方的行为是一模一样的，2、棋盘系统，负责绘制画面，3、规则系统，负责判定诸如犯规、输赢等。第一类对象（玩家对象）负责接受用户输入，并告知第二类对象（棋盘对象）棋子布局的变化，棋盘对象接收到了棋子的变化就要负责在屏幕上面显示出这种变化，同时利用第三类对象（规则系统）来对棋局进行判定。

可以明显地看出，面向对象是以功能来划分问题，而不是步骤。同样是绘制棋局，这样的行为在面向过程的设计中分散在了多个步骤中，很可能出现不同的绘制版本，因为通常设计人员会考虑到实际情况进行各种各样的简化。而面向对象的设计中，绘图只可能在棋盘对象中出现，从而保证了绘图的统一。

我们再来说一说面向对象都有哪些优点：
1. 代码开发模块化，更容易维护和修改
2. 代码复用性强
3. 增加了代码的可读性
4. 相对来说代码的可靠性和灵活性也得到了增强

面向对象的三个特征
封装
封装给对象提供了隐藏内部特性和行为的能力。对象提供一些能被其他对象访问的方法来改变它内部的数据。首先Java中提供了4种修饰符来修饰方法default, public, protected, private，对对象赋予了不同的访问权限；另外，对于对象内部的属性，通常写成私有的，然后通过setter方法来赋值，getter方法来取值，避免了直接与对象内部属性的操作。
继承
继承给对象提供了从基类获取字段和方法的能力，继承提供了代码的重用性，也可以在不修改类的情况下给现存类添加新特性。
多态
多态提供了同一个行为具有多个不同表现形式或形态的能力（say()）。是指一个类实例（对象）的相同方法在不同情形有不同表现形式。多态机制使具有不同内部结构的对象可以共享相同的外部接口。这意味着，虽然针对不同对象的具体操作不同，但通过一个公共的类，它们（那些操作）可以通过相同的方式予以调用。
多态的优点：
消除类型之间的耦合关系
可替换性
可扩充性
接口性
灵活性
简化性

> JDK 和 JRE 有什么区别？

JVM ：英文名称（Java Virtual Machine），就是我们耳熟能详的 Java 虚拟机。它只认识 xxx.class 这种类型的文件，它能够将 class 文件中的字节码指令进行识别并调用操作系统向上的 API 完成动作。所以说，jvm 是 Java 能够跨平台的核心，具体的下文会详细说明。
JRE ：英文名称（Java Runtime Environment），我们叫它：Java 运行时环境。它主要包含两个部分，jvm 的标准实现和 Java 的一些基本类库。它相对于 jvm 来说，多出来的是一部分的 Java 类库。
JDK ：英文名称（Java Development Kit），Java 开发工具包。jdk 是整个 Java 开发的核心，它集成了 jre 和一些好用的小工具。例如：javac.exe，java.exe，jar.exe 等。
显然，这三者的关系是：一层层的嵌套关系。JDK>JRE>JVM。

> == 和 equals 的区别是什么？

1. 基础数据类型没有equals方法，只能使用==来判断，判断的时候是判断值是否相等
2. 引用类型可以使用==和equalls。如果对象不重写Object中的equals方法，那么==和equals没有区别，因为Object中的equals也是使用==来判断；如果重写了equals方法，那就使用对象重写的equals方法来判断。==比较的是两个对象在堆中存放数据的内存地址是否相等。
3. String需要拿来特殊说明，String是Java中不需要new就可以产生对象的特例。使用String来申明一个变量的时候，JVM会在字符串池中查找是否已经存在这个值，如果存在就把内存地址返回给变量；如果不存在，会新开辟一个空间来存储这个值，然后把内存地址返回。那么我们再来看String中==和equals的区别，String中使用==比较的是内存地址是否相等，String重写了Object中的equals方法，使用equals时先比较对象是否相等，如果相等就返回true；否则比较值是否相等（进行字符遍历比较）。
```
    public boolean equals(Object anObject) {
        if (this == anObject) {
            return true;
        }
        if (anObject instanceof String) {
            String anotherString = (String)anObject;
            int n = value.length;
            if (n == anotherString.value.length) {
                char v1[] = value;
                char v2[] = anotherString.value;
                int i = 0;
                while (n-- != 0) {
                    if (v1[i] != v2[i])
                        return false;
                    i++;
                }
                return true;
            }
        }
        return false;
    }
```
> 两个对象的 hashCode()相同，则 equals()也一定为 true，对吗？

这个问题需要分两种情况来思考：对象有没有重写equals方法。如果没有，那默认使用Object中的equals做判断，Object中的equals使用的==来判断，比较的是对象在堆中的内存地址。如果对象为String类型，那么equals为true；否则不一定相等。Java中的HashCode是通过一定的规则将与对象相关的信息（内存地址，对象的字段等）映射成一个数值，这个数值称为散列值。我们知道这个hashCode的生成规则之后就不难理解为什么JDK要求（没有强制）当重写了hashCode之后要重写equals方法，来保证当两个对象的hashCode相同时，equals也为true。

> final 在 Java 中有什么作用？

final在Java中可以用来修饰类，方法，变量。被final修饰的类表示该类不能被继承；被final修饰的方法表示该方法不能被重写；被final修饰的变量只能被赋值一次不能被修改。

> Java 中的 Math. round(-1. 5) 等于多少？
-1

> String 属于基础的数据类型吗？
String是属于final修饰的Java类，不属于基础数据类型，基础数据类型bbcsdlif。

> Java中操作字符串都有哪些类？它们之间有什么区别？
主要有三种：String, StringBuffer, StringBuilder
String是不可变的对象，每次对String类型的改变都可能会生成一个新的对象
StringBuffer和StringBuilder是可以改变的对象。
对于操作效率：StringBuilder > StringBuffer > String
对于线程安全：StringBuffer是线程安全的，可用于多线程（关键方法基本都使用synchronized关键字修饰）；StringBuilder是非线程安全的，用于单线程
不频繁的字符串操作使用String

> String str="i"与 String str=new String(“i”)一样吗？
String str = "i";JVM会在堆内存中开辟一个空间存i这个值，然后返回地址给str; new String("i")如果字符串池中没有i的话会创建两个对象，"i"创建一个对象，new String()创建一个对象。

> 如何将字符串反转？
最直接的是使用StringBuffer的reverse方法，实现方式是使用倒序遍历；另外可以将字符串转换为char[]数组（toCharArray），倒序遍历数组

> 抽象类必须要有抽象方法吗？
不一定。抽象类必须要有abstract来修饰。

> 普通类，抽象类，接口有哪些区别？
1. 普通类可以去实例化调用，抽象类不能被实例化
2. 普通类和抽象类都可以被继承，但是抽象类被继承后子类必须重写抽象类中的抽象方法，除非自己也是抽象类
3. 抽象类可以有具体的方法和属性，接口只能有抽象方法和不可变的常量
4. 抽象类和接口性质不同，抽象类是对对象的抽象，接口是一种行为规范
5. 什么时候使用抽象类，什么时候使用接口
  使用接口：
- 需要让不相关的类都实现一个方法，例如不相关的类都可以实现 Compareable 接口中的 compareTo() 方法；
- 需要使用多重继承。
  使用抽象类：
- 需要在几个相关的类中共享代码。
- 需要能控制继承来的成员的访问权限，而不是都为 public。
- 需要继承非静态和非常量字段。
在很多情况下，接口优先于抽象类。因为接口没有抽象类严格的类层次结构要求，可以灵活地为一个类添加行为。并且从 Java 8 开始，接口也可以有默认的方法实现，使得修改接口的成本也变的很低。
另外有一点是接口中有一个叫做标记接口，例如RandomAccess

> 抽象类能使用 final 修饰吗？
不能,抽象类是被用于继承的,final修饰代表不可修改、不可继承的

> 重载和重写的区别
* 重载：同名不同参（参数类型，个数，顺序至少有一个不同）
* 重写：同名同参，子类方法不能缩小父类方法的访问权限；子类方法不能抛出比父类方法更多的异常；


15. Java 中 IO 流分为几种？
16. BIO、NIO、AIO 有什么区别？
17. Files的常用方法都有哪些？
#### 多线程
18. 并行和并发有什么区别？
19. 线程和进程的区别？
20. 守护线程是什么？
21. 创建线程有哪几种方式？
22. 说一下 runnable 和 callable 有什么区别？
23. 线程有哪些状态？
24. sleep() 和 wait() 有什么区别？
25. notify()和 notifyAll()有什么区别？
26. 线程的 run()和 start()有什么区别？
27. 创建线程池有哪几种方式？
28. 线程池都有哪些状态？
29. 线程池中 submit()和 execute()方法有什么区别？
30. 在 Java 程序中怎么保证多线程的运行安全？
31. 多线程锁的升级原理是什么？
32. 什么是死锁？
33. 怎么防止死锁？
34. ThreadLocal 是什么？有哪些使用场景？
35. 说一下 synchronized 底层实现原理？
36. synchronized 和 volatile 的区别是什么？
37. synchronized 和 Lock 有什么区别？
38. synchronized 和 ReentrantLock 区别是什么？
39. 说一下 atomic 的原理？
三、spring/spring MVC
40. 为什么要使用 spring？
41. 解释一下什么是 aop？
42. 解释一下什么是 ioc？
43. spring 有哪些主要模块？
44. spring 常用的注入方式有哪些？
45. spring 中的 bean 是线程安全的吗？
46. spring 支持几种 bean 的作用域？
47. spring 自动装配 bean 有哪些方式？
48. spring 事务实现方式有哪些？
49. 说一下 spring 的事务隔离？
50. 说一下 spring mvc 运行流程？
51. spring mvc 有哪些组件？
52. @RequestMapping 的作用是什么？
53. @Autowired 的作用是什么？
四、spring/spring Cloud
54. 什么是 spring boot？
55. 为什么要用 spring boot？
56. spring boot 核心配置文件是什么？
57. spring boot 配置文件有哪几种类型？它们有什么区别？
58. spring boot 有哪些方式可以实现热部署？
59. jpa 和 hibernate 有什么区别？
60. 什么是 spring cloud？
61. spring cloud 断路器的作用是什么？
62. spring cloud 的核心组件有哪些？
五、Mybatis
63. mybatis 中 #{}和 ${}的区别是什么？
64. mybatis 有几种分页方式？
65. RowBounds 是一次性查询全部结果吗？为什么？
66. mybatis 逻辑分页和物理分页的区别是什么？
67. mybatis 是否支持延迟加载？延迟加载的原理是什么？
68. 说一下 mybatis 的一级缓存和二级缓存？
69. mybatis 和 hibernate 的区别有哪些？
70. mybatis 有哪些执行器（Executor）？
71. mybatis 分页插件的实现原理是什么？
72. mybatis 如何编写一个自定义插件？
六、kafk、Zookeeper
73. kafka 可以脱离 zookeeper 单独使用吗？为什么？
74. kafka 有几种数据保留的策略？
75. kafka 同时设置了 7 天和 10G 清除数据，到第五天的时候消息达到了 10G，这个时候 kafka 将如何处理？
76. 什么情况会导致 kafka 运行变慢？
77. 使用 kafka 集群需要注意什么？
78. zookeeper 是什么？
79. zookeeper 都有哪些功能？
80. zookeeper 有几种部署模式？
81. zookeeper 怎么保证主从节点的状态同步？
82. 集群中为什么要有主节点？
83. 集群中有 3 台服务器，其中一个节点宕机，这个时候 zookeeper 还可以使用吗？
84. 说一下 zookeeper 的通知机制？
七、Redis、JVM
85. Redis是什么？都有哪些使用场景？
86. redis 有哪些功能？
87. redis 和 memecache 有什么区别？
88. redis 为什么是单线程的？
89. 什么是缓存穿透？怎么解决？
90. redis 支持的数据类型有哪些？
91. redis 支持的 Java 客户端都有哪些？
92. Jedis 和 redisson 有哪些区别？
93. 怎么保证缓存和数据库数据的一致性？
94. redis 持久化有几种方式？
95. redis 怎么实现分布式锁？
96. redis 分布式锁有什么缺陷？
97. redis 如何做内存优化？
98. redis 淘汰策略有哪些？
99. redis 常见的性能问题有哪些？该如何解决？
100. 说一下 Jvm 的主要组成部分？及其作用？
101. 说一下 Jvm 运行时数据区？
102. 说一下堆栈的区别？
103. 队列和栈是什么？有什么区别？
104. 什么是双亲委派模型？
105. 说一下类加载的执行过程？
106. 怎么判断对象是否可以被回收？
107. java 中都有哪些引用类型？
108. 说一下 jvm 有哪些垃圾回收算法？
109. 说一下 jvm 有哪些垃圾回收器？
110. 详细介绍一下 CMS 垃圾回收器？
111. 新生代垃圾回收器和老生代垃圾回收器都有哪些？有什么区别？
112. 简述分代垃圾回收器是怎么工作的？
113. 说一下 jvm 调优的工具？
114. 常用的 jvm 调优的参数都有哪些？
> Java线程执行native方法时程序计数器为空，如何确保native执行完后的程序执行的位置
native是非java代码编写的，比如C,C++, 它们无法在java编译时生成字节码，即JVM获取不到native实现，只能通过系统指令去调用native方法,所以执行native时程序计数器值为空undefined。native方法由原生平台直接执行，native方法执行后会退出(栈帧pop)，方法退出返回到被调用的地方继续执行程序。

### 秒杀系统
1. 如何控制秒杀商品页面购买按钮的定时点亮？[抢买问题]
2. 如何防止超卖？
3. 如何防止重复下单？
4. 排队下单，类似12306入Queue的操作
参考答案：https://github.com/zhonghuasheng/JAVA/tree/master/seckill#


### 面试技巧
1. 面试前出于礼貌和面试官确认自己讲话是否能被听懂，方言的问题
2. 自我介绍尽量控制在35秒左右（基本信息介绍，工作经历介绍，求职的原因介绍）
3. 在回答问题是使用我的理解是什么什么，不要去绝对回答这个问题，技术没有完全的对错，每个人对技术的理解都不同
4. 面试过程中如果遇到自己没有接触到的知识点，可以这样说：这个知识点我们有接触过，我尝试回答一下我的理解