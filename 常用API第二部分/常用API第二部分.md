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
类简介  
属于java.util包，用来表示时间和日期，1970年1月1日作为毫秒的起始日期。该类返回的时间就是先到到起始点经历了多少毫秒。
1. 毫秒值得概念和作用  
这个其实时间是以英国所在时区为标准的，中国所在时区要增加8个小时
2. 构造方法和成员方法
无参构造方法：Date date = new Data();
直接打印则会显示 当前系统时间。

带参构造方法：Date date = new Date(0L);//x为一个long类型的毫秒值   
理解为1970年1月1日8时加上参数时间后的时间点
直接打印这个date则会打印出1970年1月1日8时

成员方法：getTime() 功能：把时间转换为毫秒相当于System.currentTimeMillis()方法
# DateFormat类

属于java.text包，它是一个抽象类，直接子类SimpleDataformat、MessageFormat、NumberFormat。

其功能：格式化：日期->文本、解析：文本->日期
成员方法：
String format(Date date)按照指定模式，把Date日期转格式化为符合模式的字符串
Date parse(String source)把符合模式的字符串，解析为Date日期
此方法和format方法刚好相反，format方法是把Date类对象转换为我们指定的日期格式，而这个方法是把我们指定的日期格式转换为Date类对象。
parse方法声明了一个异常，称之为解析异常，如果字符串和构造方法的模式不匹配，则抛出异常。 

我们在使用时一般使用它的直接子类，SimpleDateFormat,
SimmpleDateFormat类
构造方法：SimpleDateFormat(String pattern)
其中参数pattern使用固定的格式：
y代表年
M代表月
d代表日
H代表时
m代表分
s代表秒
时间符号y、M...符号本身不能改变，但是连接时间的符号可以改变。
例如：pattern可以为：“yyyy-MM-dd-HH-mm:ss”
也可以为："yyyy年MM月dd日HH时mm分ss秒"
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

