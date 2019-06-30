# 1.Object类
## 1.类简介  
Object类属于java.lang包，Object是所有类的超类，也就是java中所有的类都继承自Object，如果没有写继承关系的话，则默认继承自Object类。   
## 2.常用方法
** 1. toString方法  **
直接打印对象的名字，就是调用对象的toString()方法，打印的是对象在堆内存中的地址值。也就是说默认的toString方法打印的就是对象的地址值。我们可以自己重写toString()方法。Idea 的技巧，通过Alt+INS 可以快捷添加toString()方法。看一个类是否重写了toString()方法，可以通过打印该对象名字来判断，如果打印的是对象地址，则代表没有重写，否则就重写了。例如：Scanner类、ArraryList类都重写了toString()方法。Random类则没有重写。  
** 2. equals方法：public boolean equals (Object obj) ** 
- 默认功能(属于Object类)：比较其他对象是否与此对象相等。      
- 基本数据类型：比较数据的值。  
- 引用数据类型：比较对象的地址。没什么意义，所以一般要重写equals() 方法，即比较两个对象的属性。 

** 注意： **  

** (1) **在修改equals()方法时，需要比较子类的属性，而在创建对象时，是用父类的名字指向了子类的对象，也就是使用了多态的方法，多态是存在弊端的，即不能访文子类有的内容(属性和方法)，此时就需要一个解决方案。我们常用的解决方法就是：向下转型(即强转)。  

** (2) **在重写equals方法时一般要考虑的情况：比较的对象是否为本身？比较的对象是否能够发生向下转型？比较的对象是否为NULL？。在Idea 中Alt+INS 同样可以快捷重写equals()方法，但是它判断是否可以向下转型时是用的是反射技术。   

# 2.Objects类
** 1.equals()方法 **  
Objects类属于java.util包，它是在JDK7中添加的一个工具类，它由一些静态方法组成。这些方法时空指针安全的(null-save) 或者说空指针容忍的(null-tolerant)。其中的一个方法就是用于比较两个对象时候相等。    
** 2.什么叫null-save 或者null-tolerant ?  **  
比较两个对象s1，s2，如果s1为null的时候，则s1.equals(s2),就会触发一个异常，成为空指针异常，这是因为s1是null，无法调用方法等。而Objects类的equals()方法解决了这个问题。称之为null-save。      

# 3.Data类
## 1.类简介 
属于java.util包，用来表示时间和日期，1970年1月1日作为毫秒的起始日期。该类返回的时间就是先到到起始点经历了多少毫秒。这个其实时间是以英国所在时区为标准的，中国所在时区要增加8个小时。  

## 2.构造方法
** (1)无参构造方法： **    
```java
Date date = new Data();//直接打印则会显示 当前系统时间。
```
** (2)带参构造方法： **    
```java
Date date = new Date(0L);//x为一个long类型的毫秒值  
``` 
** (3)注意 **   
理解为1970年1月1日8时加上参数时间后的时间点，直接打印这个date则会打印出1970年1月1日8时。  
## 3.成员方法
```java
getTime() //功能：把时间转换为毫秒相当于System.currentTimeMillis()方法
```
# 4.DateFormat类
## 1.类简介
** (1)概述 **
属于java.text包，它是一个抽象类，直接子类SimpleDataformat、MessageFormat、NumberFormat。  

** (2)其功能： **格式化：日期->文本、解析：文本->日期  
## 2.成员方法
```java
String format(Date date)//按照指定模式，把Date日期转格式化为符合模式的字符串
Date parse(String source)//把符合模式的字符串，解析为Date日期。此方法和format方法刚好相反，format方法是把Date类对象转换为我们指定的日期格式，而这个方法是把我们指定的日期格式转换为Date类对象。
/**/
```
** (3)注意 **  
parse方法声明了一个异常，称之为解析异常，如果字符串和构造方法的模式不匹配，则抛出异常。 
** (4)使用该类 **  
我们在使用时一般使用它的直接子类，SimpleDateFormat,下述为其构造方法  
```java
SimpleDateFormat(String pattern)
```
** (5)pattern注意 **  
** 参数pattern使用固定的格式： **y代表年,M代表月,d代表日,H代表时,m代表分,s代表秒。时间符号y、M...符号本身不能改变，但是连接时间的符号可以改变。例如：pattern可以为：“yyyy-MM-dd-HH-mm:ss”。也可以为："yyyy年MM月dd日HH时mm分ss秒"   
# 3.Calender类
## 1.类简介 
Calender是一个抽象类，在Date类之后出现，替代了许多Date类中的方法，该类的出现时为了更加方便的获取时间信息，这个类中包含了许多静态方法，因此获取时间更加方便。Calender类中的成员变量也是静态的，因此可以使用Calendar.字段，来访问或更改其值。  
## 2.字段摘要
 ** Calendar类中提供很多成员常量，代表给定的日历字段： **
 
| 字段值          | 含义                             |
| ------------ | --------------------               |
| YEAR         | 年                                 |
| MONTH        | 月（从0开始，可以+1使用）            |
| DAY_OF_MONTH | 月中的天（几号）                    |
| HOUR         | 时（12小时制）                      |
| HOUR_OF_DAY  | 时（24小时制）                      |
| MINUTE       | 分                                 |
| SECOND       | 秒                                 |
| DAY_OF_WEEK  | 周中的天（周几，周日为1，可以-1使用） |
## 3.该类对象获取方式  
获取一个Calender子类对象：由于语言敏感性，Calendar类在创建对象时并非直接创建，而是通过静态方法创建，返回子类对象，如下：  
Calendar静态方法    
```java
	public static Calendar getInstance()//功能：使用默认时区和语言环境获得一个日历
```
## 4.常用成员方法

```java 
	public int get(int field)//返回给定日历字段的值。
	public void set(int field, int value)//将给定的日历字段设置为给定值。
	public abstract void add(int field, int amount)//根据日历的规则，为给定的日历字段添加或减去指定的时间量。
	public Date getTime()//返回一个表示此Calendar时间值（从历元到现在的毫秒偏移量）的Date对象。
```
** 注意： **指定日历字段的方式为：Calender.字段。例如：Calender.YEAR。  
# 4.System类
## 1.类简介
属于java.lang包，其中提供了大量的静态方法，可以获取与系统相关的信息或系统级操作。  
## 2.常用成员方法：
```java 
	public static currentTimeMillis()//返回一毫秒为单位的当前时间。使用场景，获取程序运行的毫秒值
	pubilc static void arraycopy(Object src,int srcPos,Object dest, int destPos,int length)//将src数组中的从srcPos开始的length个元素拷贝到dest数组从destPos开始的位置处
	/*
	参数：
	src:源数组
	srcPos:源数组起始位置
	dest：目标数组
	destPos:目标数组起始位置
	length:要复制数组元素的数量
	*/
```
# 5.StringBuilder类
## 1. StringBuilder类原理
String 底层是一个final的Byte数组，由于是final的，所以其长度和内容是不可改变的。例如我们有三个字符串进行拼接"a"+"b"+"c"，那么我们在进行拼接时，实际上在内存中会产生一个中间字符串，即"ab"如果拼接的多了，产生的中间字符串会更多，因此这种拼接效率是非常低下的，并且很消耗内存。为了解决这个问题，java引入了StringBuilder类。我们可以把StringBuilder类理解为字符串缓冲区，它是一个容器，它底层也是一个Byte数组，但是与String不同的是，它的数组并不是final的，因此数组的长度是可以改变的。StringBuilder默认的长度为16个字节，在容量不够时，它会自动扩容。我们在进行字符 串拼接时，相当于在给一个容器中增加一个元素。StringBuilder类属于java.lang包。   
## 2. 构造方法
```java
	//常用的构造方法有两个
	//第一个:无参构造方法
	StringBuilder()
	//第二个：带一个字符串为参数的构造方法
	StringBuilder(String  str)
```
## 3. 常用成员方法
** 1. append方法 **  
```java 
	public StringBuilder oppend()//功能：向StringBuilder中添加数据，返回调用方法的对象，通常不需要接受对象。
```
** 2. toString方法**
```java
	//StringBuilder和String对象可以相互转换
	//String转化成StringBuilder 采用StringBuilder的构造方法即可
	public String toString()//StringBuilder装换为String 采用Stringbuilder的toString()方法
```

# 6.基本类型包装类
## 1.java包装类概述
java包装类位于java.lang包。Java提供了两个类型系统，基本类型与引用类型，使用基本类型在于效率，然而很多情况，会创建对象使用，因为对象可以做更多的功能，如果想要我们的基本类型像对象一样操作，就可以使用基本类型对应的包装类，定义了包装类，就可以使用包装类中的相关方法。常用包装类(公8个)如下：  

| 基本类型    | 对应的包装类        |
| ------- | --------------------- |
| byte    | Byte                  |
| short   | Short                 |
| int     | **Integer**           |
| long    | Long                  |
| float   | Float                 |
| double  | Double                |
| char    | **Character**         |
| boolean | Boolean               |
## 2. 拆箱与装箱
基本类型与对应的包装类对象之间，来回转换的过程称为”装箱“与”拆箱“：  

* ** 装箱 **：从基本类型转换为对应的包装类对象。  

* ** 拆箱 **：从包装类对象转换为对应的基本类型。  

```java
	//基本数值---->包装对象
	//方式一 使用包装类的构造方法
	Integer i = new Integer(4);//使用构造函数函数
	Integer i2 = new Integer("4")//第二种构造方法
	//方式二 使用包装类的静态方法valueof
	Integer iii = Integer.valueOf(4);//使用包装类中的valueOf方法
	Integer iii2 = Integer.valueOf("4");
	
	//包装对象---->基本数值
	int num = i.intValue();//返回该Interger对象的int值

	//如果应该传递数字组成的字符串，但是却传递了字母，那么编译器就会报错
```

## 3. 自动拆箱与自动装箱
由于我们经常要做基本类型与包装类之间的转换，从Java 5（JDK 1.5）开始，基本类型与包装类的装箱、拆箱动作可以自动完成。例如：  

```java
Integer i = 4;//自动装箱。相当于Integer i = Integer.valueOf(4);
i = i + 5;//等号右边：将i对象转成基本数值(自动拆箱) i.intValue() + 5;
//加法运算完成后，再次装箱，把基本数值转成对象。
```
## 4. 基本类型与字符串类型之间
#### 1.String类型装换为基本类型
除了Character类之外，其他所有包装类都具有parseXxx静态方法可以将字符串参数转换为对应的基本类型：  
```java
	public static byte parseByte(String s)//将字符串参数转换为对应的byte基本类型。
	public static short parseShort(String s)//将字符串参数转换为对应的short基本类型。
	public static int parseInt(String s)//将字符串参数转换为对应的int基本类型。
	public static long parseLong(String s)//将字符串参数转换为对应的long基本类型。
	public static float parseFloat(String s)//将字符串参数转换为对应的float基本类型。
	public static double parseDouble(String s)//将字符串参数转换为对应的double基本类型。
	public static boolean parseBoolean(String s)//将字符串参数转换为对应的boolean基本类型。
```
#### 2.基本类型转换为String类型
共有三种方式，这里介绍其中最简单的一种：  
即：基本类型+""，例如：34+""  

