# 走近Java
1. 微软公司曾今是Java技术的铁杆支持者，令Java从跨平台技术变为绑定在Windows上的技术是微软的主要目的，然而后期Sun公司控告微软，致使微软不得不在后期产品中逐步移除Java平台，也间接导致.NET平台的产生，2002年微软发布.NET技术平台，这才有了后期的.NET与Java之争。

2. 多核并行，在JDK1.5就引入java.util.concurrent包实现粗粒度的并发框架，在JDK1.7中加入java.util.concurrent.forkjoin包则是对这个框架的一次重要扩充。Fork/Join模式是处理并行编程的一个经典方法。
# 自动化内存管理机制
## Java内存区域与内存溢出异常
## 垃圾收集器与内存分配策略
## 虚拟机性能监控与故障处理工具
## 调优案例分析与实战

# 虚拟机执行子系统
## 类文件结构
## 虚拟机类加载机制
## 虚拟机字节码执行引擎
## 类加载及执行子系统的案例与实战

# 程序编译与代码优化
## 早期（编译器）优化
## 晚期（运行期）优化

# 高效并发
## Java内存模型与线程
## 线程安全与锁优化

### JVM
* JVM初始分配的堆内存由-Xms指定，默认是物理内存的1/64；JVM的最大分配的堆内存由-Xmx指定，默认是物理内存的1/4.默认空余堆内存小于40%时，JVM就会增大堆直到-Xmx最大限制；空余堆内存大于70%时，JVM就会减少堆直到-Xms的最小限制。因此，服务器端一般设置-Xms、-Xmx相等以避免在每次GC后调整堆的大小。

### JConsole
* Java 5开始引入JConsole

### 深入拆解Java虚拟机
* 可以使用-XX:+HeapDumpOnOutOfMemoryError参数来让虚拟机出现OOM的时候自动生成dump文件
* ClassLoader的具体作用就是将class文件加载到jvm虚拟机中去，程序就可以正确运行了。但是，jvm启动的时候，并不会一次性加载所有的class文件，而是根据需要去动态加载。
* Java 虚拟机是如何判定两个 Java 类是相同的。Java 虚拟机不仅要看类的全名是否相同，还要看加载此类的类加载器是否一样。只有两者都相同的情况，才认为两个类是相同的。即便是同样的字节代码，被不同的类加载器加载之后所得到的类，也是不同的。
* ClassLoader
    * BootStrap ClassLoader：称为启动类加载器，是Java类加载层次中最顶层的类加载器，负责加载JDK中的核心类库，如：rt.jar、resources.jar、charsets.jar等
    * Extension ClassLoader：称为扩展类加载器，负责加载Java的扩展类库，默认加载JAVA_HOME/jre/lib/ext/目下的所有jar。
    * App ClassLoader：称为系统类加载器，负责加载应用程序classpath目录下的所有jar和class文件。
        * 除了Java默认提供的三个ClassLoader之外，用户还可以根据需要定义自已的ClassLoader，而这些自定义的ClassLoader都必须继承自java.lang.ClassLoader类，也包括Java提供的另外二个ClassLoader（Extension ClassLoader和App ClassLoader）在内，但是Bootstrap ClassLoader不继承自ClassLoader，因为它不是一个普通的Java类，底层由C++编写，已嵌入到了JVM内核当中，当JVM启动后，Bootstrap ClassLoader也随着启动，负责加载完核心类库后，并构造Extension ClassLoader和App ClassLoader类加载器。

# *JDK*
### JDK中自带的工具
#### `version 1.8`

#### Create and Build Applications
* appletviewer
* extcheck
* jar
* java
* javac
* javadoc
* javah
* javap
* jdb
* jdeps

#### Security
* keytool
* jarsigner
* policytool

#### Internationalization
* native2ascli

#### Remote Method Invocation(RMI)
* rmic
* rmiregistry
* rmid
* serialver

#### Java IDL and RMI-IIOP
* tnameserv
* idlj
* orbd
* servertool

#### Deploy Applications and Applets
* pack200
* unpack200
* javapackager
* javafxpackager

#### Java Web Start
* javaws

#### Monitor Java Applications
* jconsole
* jvisualvm

#### Monitor the JVM
* jps
* jstat
* jstatd
* jmc

#### Web Services
* schemagen
* wsgen
* wsimport
* xjc

#### Troubleshooting
* jcmd
* jinfo
* jhat
* jmap
* jsadebugd
* jstack

#### Scripting
* jrunscript
* jjs

# FAO
1. 函数式编程的一个重要优点就是这样的程序天然地适合并行运行，why？