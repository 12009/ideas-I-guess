## 说明

## 目录

[TOC]



## Java解决方案



### 异常

#### 异常介绍

- https://www.geeksforgeeks.org/checked-vs-unchecked-exceptions-in-java/

#### 只读异常

- ReadOnlyBufferException
- Unchecked exception thrown when a content-mutation method such as `put` or `compact` is invoked upon a read-only buffer.
- **1) Checked:** are the exceptions that are checked at compile time. If some code within a method throws a checked exception, then the method must either handle the exception or it must specify the exception using *throws* keyword.
- **2) Unchecked** are the exceptions that are not checked at compiled time. In C++, all exceptions are unchecked, so it is not forced by the compiler to either handle or specify the exception. It is up to the programmers to be civilized, and specify or catch the exceptions.
- In Java exceptions under *Error* and *RuntimeException* classes are unchecked exceptions, everything else under throwable is checked.
- Throwable
  - Error:unchecked
  - Exception
    - checked
    - RuntimeException:unchecked

#### 并发

- java.util.concurrent.TimeoutException
  - http://www.blogjava.net/xylz/archive/2011/07/12/354206.html	
  - 此异常是用来描述任务执行时间超过了期望等待时间，也许是一直没有获取到锁，也许是还没有执行完成。







### 代码规范

- 类名：每个单词首字母大写
- 方法名：动词+名词，动词小写，名词首字母大写
- 变量名：名词，首字母小写，多个单词的话，在后面单词每个首字母大写







### maven

- 发布jar包，跳过测试单元
  -  mvn clean install -Dmaven.test.skip=true
- 执行jar包
  - 有main入口，需要在pom里面指定，有时候可能会影响项目的整体性
  - java -jar myjar.jar
  - 没有main入口
  - java -cp myjar.jar com.example.MainClass(src中有main的入口类)
  - java -cp target/rtidb-client-1.3.8-SNAPSHOT.jar com._4paradigm.rtidb.utils.Command
- jar的可执行
  - 如果涉及到外部包的依赖，一定要添加插件
  - https://blog.csdn.net/change_on/article/details/79379400



### 命令行下创建完整java项目

- mvn archetype:generate
- 回车
- 填写groupID等信息，就行了
- 注意填写package的时候，写的是包名

## Java类的使用

### Future

- 用于多线程场景使用，异步操作，非阻塞模型
- 基本介绍：https://blog.csdn.net/u014209205/article/details/80598209

#### 实战

- 定义future类，存放我们的操作变量
- 定义callable类，存放通信的消息子，也就是用来通知程序运行结果，以及监控程序的运行状态
- 定义Executors类，存放线程实例
- Executors 要登记 callable 
- callable里面有要操作的动作
- future类变量，获取 Executors submit 的信息。也就是说分配这个动作信息给future
- future之后将会做一系列动作，然后接收返回结果到future变量中
- 我们可以通过打印future变量，获取结果信息



### ByteBuffer

- 常用的缓冲区
- 信道的读写方法只接收ByteBuffer
- 图解：https://my.oschina.net/flashsword/blog/159613
- 文档
  - http://tutorials.jenkov.com/java-nio/buffers.html
  - https://docs.oracle.com/javase/7/docs/api/java/nio/ByteBuffer.html

#### 实战

- ByteBuffer buffer=ByteBuffer.allocate(256);
- 更常用的是从byte获取
-  ByteBuffer buffer=ByteBuffer.wrap(byteArray);
- byte类似于一个中间类型，是bytebuffer的桥梁
- buffer.clear(); 清楚数据，实际只是变更索引值，回到第一个位置，之后重写数据
- bytebuffer to byte ： buffer.get(new byte[6])   String value = new String(byte);
- Byte to bytebuffer :    ByteBuffer.wrap(byteArray);  buffer.put(byteArray)



### Builder

- 一般用于创建对象同时配置对象的内容
- 我在google的proto 里面正好用到这个builder
- 不深究，先给粗浅的用法对于proto生成的java 代码

#### 实战

- .build()之后一般直接生成好了对象
- 如果要动态配置build，就需要Builder对象，然后set配置。set相关内容后，才能build最终对象出来

## 问题

### 命令端

#### no main manifest attribute

- 在执行jar包缺少main入口的原因

#### Error: Could not find or load main class clean

- 





[TOC]

