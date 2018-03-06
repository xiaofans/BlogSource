## **java运行时的内存分配**

数据存储在五个地方:

1.**寄存器**:最快的存储区，位于处理器内部。寄存器的数量有限，你不能直接控制，寄存器根据需求自己分配(C和C++允许向编译器建议寄存器的分配方式)。

​	寄存器介绍:https://baike.baidu.com/item/%E5%AF%84%E5%AD%98%E5%99%A8/187682?fr=aladdin

2.**堆栈**:位于通用RAM(随机访问存储器)中，通过**堆栈指针**可以从**处理器**那里获得直接支持。堆栈指针向下移动，则分配新的内存，堆栈指针向上移动，则释放那些内存。这是一种快速有效的分配存储方法，仅次于寄存器。创建程序时，Java系统必须知道存储在堆栈内所有项的确切生命周期，以便上下移动堆栈指针。这一约束限制了程序的灵活性，所以虽然某些Java数据存储于堆栈中---特别是对象引用，但是Java对象不存储于其中。

​	**堆栈中存储了什么?**

​	上面所说的对象引用、基本类型变量(boolean、char、byte、short、int、long、float、double、void*)、高精度数字(BigInteger、BigDecimal)。

3.**堆**:一种通用的内存池(也位于RAM区)，用于存放所有的Java对象、堆不同于堆栈的好处是:编译器不需要知道存储的数据在堆里存活多长时间。因此，在堆里分配存储有很大的灵活性。当然为这种灵活性必须要付出相应的代价:用堆进行存储分配和清理可能比用堆栈进行存储分配需要更多的时间(如果确实可以在Java中像C++中一样在堆栈中创建对象)。

**String的位置存放?**

​	Java对String对象存储特殊对待，在堆中分成了两块一块是字符串常量池(String constant pool)用于存储字符串常量对象，另外一块用于存储普通对象和字符串对象。

			String a = "1";
			String b = "1";
			System.out.println(a == b);  // true
			System.out.println(a.equals(b));  //true
			
			String a = new String("1");
			String b =  new String("1");
			System.out.println(a == b);  // false
			System.out.println(a.equals(b));  //true


4.**常量存储**:常量值通常直接存放在程序代码内部，这样做是安全的，因为它们永远不会被改变。

5.**非RAM存储**:存于硬盘上或者其他媒介上。

关于这个问题网上的一些相关文章

https://www.cnblogs.com/zyj-bozhou/p/6723863.html

http://blog.csdn.net/okyoung188/article/details/55506594



## 按位操作符

按位操作符用来操作整数基本数据类型中的单个“比特”(bit)，即二进制位。按位操作符会对两个参数中对应的位执行布尔代数运算，并最终生成一个结果。

&与:两个输入位都是1，输出1。否则输出0。

|或:两个输入位有一个是1，输出1。都为0的时候，输出0。

^异或:输入的某一位是1，但不全都是1，输出1。

~非:取反，属于一元操作符，以上的位二元操作符。若输入0，则输出1。若输入1，则输出0。



## 静态数据的初始化和静态块

无论创建多少个对象，静态数据都只占用一份存储区域。static关键字不能用于局部变量，因此它只能作用于域。

静态块代码仅执行一次:当首次生成这个类的一个对象时，或首次访问属于那个类静态数据成员时(即便从未生成过那个类的对象)。

```java
public class T3 {
	public T3(){
	System.out.println("t3");
}

static{
	System.out.println("static");
}

public static void main(String[] args) {
	T3 t3 = new T3();
}}

output
static
t3
```

