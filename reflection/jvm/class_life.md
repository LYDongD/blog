## 类加载机制

> 类的生命周期

类加载 -> 链接 -> 初始化 -> 类使用 -> 类卸载

* 链接：
    * 验证
    * 准备
    * 解析

任何类在使用之前必须初始化，当；类被主动使用时，才会触发类的初始化：

* 主动使用（七种）
    * 创建类的实例。
    * 访问某个类或者接口的静态变量，或者对该静态变量赋值。
    * 调用类的静态方法。
    * 反射 （如Class.forName(“com.test.Test”)）。
    * 初始化一个类的子类。
    * Java 虚拟机启动时被标明为启动类的类。
    * JDK1.7 开始提供的动态 语言支持。

* 被动引用，处主动使用外，其他情况都被认为是被动使用，例如：
    * 引用父类的静态字段，只会引起父类的初始化，而不会引起子类的初始化；
    * 定义类数组，不会引起类的初始化；
    * 引用类的常量，不会引起类的初始化。

> 类的加载模式

双亲委派模型，优先委托parent指向的父类加载器进行加载，且不会重复加载。

* 优点
    * 安全，确保jvm需要的基础类能够被安全加载，应用自定义的同名类不会被重复加载导致核心类被覆盖

详情参考class_load.md

> 类的卸载

[参考](https://mp.weixin.qq.com/s/gWYxD7JAo7e6P0nLBbdZGA)

类在3种情况下会被卸载：

* 类的实例都被回收
* 加载类的ClassLoader已经被回收
* 类对象没有被引用

AppClassLoader不会被回收，导致通过该加载器加载的类也不会被回收，因此，动态代理，反射等应用需要动态创建类的情况，需要使用自定义类加载器，避免类对象过多导致方法区溢出


