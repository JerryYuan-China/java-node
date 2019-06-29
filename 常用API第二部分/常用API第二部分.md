# 1.Object类
1. 类简介  
Object类属于java.lang包，Object是所有类的超类，也就是java中所有的类都继承自Object，如果没有写继承关系的话，则默认继承自Object类。 
2. toString方法  
直接打印对象的名字，就是调用对象的toString()方法，打印的是对象在堆内存中的地址值。也就是说默认的toString方法打印的就是对象的地址值。   
我们可以自己重写toString()方法。Idea 的技巧，通过Alt+INS 可以快捷添加toString()方法。  
看一个类是否重写了toString()方法，可以通过打印该对象名字来判断，如果打印的是对象地址，则代表没有重写，否则就重写了。例如：Scanner类、ArraryList类都重写了toString()方法。Random类则没有重写。     
3. equals方法：public boolean equals (Object obj)  
默认功能(属于Object类)：比较其他对象是否与此对象相等。    
基本数据类型：比较数据的值。  
引用数据类型：比较对象的地址。没什么意义，所以一般要重写equals() 方法，即比较两个对象的属性。  
在修改equals()方法时，需要比较子类的属性，而在创建对象时，是用父类的名字指向了子类的对象，也就是使用了多态的方法，多态是存在弊端的，即不能访文子类有的内容(属性和方法)，此时就需要一个解决方案。我们常用的解决方法就是：向下转型(即强转)。
在重写equals方法时一般要考虑的情况：比较的对象是否为本身？比较的对象是否能够发生向下转型？比较的对象是否为NULL？。在Idea 中Alt+INS 同样可以快捷重写equals()方法，但是它判断是否可以向下转型时是用的是反射技术。      
4. Objects类的equals()方法
Objects类属于java.util包，它是在JDK7中添加的一个工具类，它由一些静态方法组成。这些方法时空指针安全的(null-save) 或者说空指针容忍的(null-tolerant)。其中的一个方法就是用于比较两个对象时候相等。  
什么叫null-save 或者null-tolerant ?  
比较两个对象s1，s2，如果s1为null的时候，则s1.equals(s2),就会触发一个异常，成为空指针异常，这是因为s1是null，无法调用方法等。而Objects类的equals()方法解决了这个问题。称之为null-save。    

# 2.Data类
1. 毫秒值得概念和作用  
2. 构造方法和成员方法  
3. DataFormat类  
4. 练习_计算一个人已经出生了多少天  
# 3.Calender类
1. 类介绍  
2. 常用成员方法  
# 4.System类
类简介。属于java.lang包，其中提供了大量的静态方法，可以获取与系统相关的信息或系统级操作。
常用成员方法：
返回一毫秒为单位的当前时间  public static currentTimeMillis()
使用场景，获取程序运行的毫秒值
pubilc static void arraycopy(Object src,int srcPos,Object dest, int destPos,int length)
参数：
src:源数组
srcPos:源数组起始位置
dest：目标数组
destPos:目标数组起始位置
length:要复制数组元素的数量
功能：将src数组中的从srcPos开始的length个元素拷贝到dest数组从destPos开始的位置处
# 5.StringBuilder类
1. StringBuilder类原理
2. 构造方法
3. toString方法
# 6.基本类型包装类
1. 包装类的概念
2. 包装类的拆箱与装箱
3. 自动拆箱与自动装箱
4. 基本类型与字符串类型之间

