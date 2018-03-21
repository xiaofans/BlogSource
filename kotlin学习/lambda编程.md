​	Lambda表达式，简称lambda,本质上就是可以传递给其他函数的一小段代码。有了lambda，可以轻松地把通用的代码结构抽取成函数。最常见的一种lambda用途就是和集合一起工作。

**Lambda表简介:作为函数参数的代码块**

​	在代码中存储和传递一小段行为是常有的任务，在老版本的Java中，可以使用匿名内部类来实现。

​	**函数式编程提供了另外一种解决问题的方法：把函数当做值来对待。可以直接传递函数，而不需要先声明一个类再传递这个类的实例。**使用lambda表达式之后，代码会更加简洁。

​	

```
button.setOnClickListener{
  // 点击后执行的动作
}
```

**Lambda表达式的语法**

​	一个lambda把一小段行为进行编码，你能把它当作值到处传递，它可以被独立的声明并存储到一个变量中。

```
{x:Int,y:Int -> x+y}
```

​	Kotlin的lamnda表达式始终用花括号包围。**注意实参并没有用括号括起来**。**箭头把实参列表和lambda的函数体隔开。**

​	可以把lambda表达式存储在一个变量中，把这个变量当作普通函数对待(即通过相应实参调用它):

```
val sum = {x:Int,y:Int -> x + y}
println(sum(1,2))
```

​	

```
val people = listOf(Person("alice",29),Person("Bob",31))
println(people.maxBy{p:Person -> p.age})
// 花括号中的代码片段是lambda表达式，把它作为实参传给函数。这个lambda接收一个类型为Person的参数并返回它的年龄
```

​	**如果lambda是唯一的实参，你可以在写代码的时候省略这些括号。当有多个实参时，既可以把lambda留在括号内抢到它是一个实参，也可以把它放到括号的外面，两种都是可醒的。如果你想传递两个或者更多的lambda，不能把超过一个的lambda放到外面，这时使用常规语法来传递他们通常是更好的选择。**



```
val people = listOf(Person("alice",29),Person("Bob",31))
//把lambda作为命名实参传递
val names = people.joinToString(separator="",transform={p:Person -> p.name})
println(names)
// 把lambda放在括号外传递
people.joinToString(" "){p:Person -> p.name}

```

**省略lambda参数类型**

```
people.maxBy{p:Person -> p.age}
people.maxBy(p -> p.age)
```

​	**和局部变量一样，如果lambda参数的类型可以被推导出来，你就不需要显式地指定它。**

​	也存在编译器不能推断出lambda参数类型的情况，但这里我们暂不讨论。可以遵循这样一条简单的规则：先不声明类型，等编译器报错后再指定它们。

​	最后简化是使用默认参数名称it代替命名参数。如果当前上下文期望的是只有一个参数的lambda且这个参数的类型可以推断出来，就会生成这个名称。

​	

```
peope.maxBy{it.age}
```

​	**成员引用**

​	 如果把函数转换成一个值，你就可以传递它。使用::运算符来转换，这种表达式称为成员引用，它提供了简明语法，来创建一个调用单个方法或者访问单个属性的但数值。双冒号把类名称与你要引用的成员(一个方法或一个属性)

```
val getAge = person::age
Person是类
age是成员
```

​	还可以引用顶层函数(不是类的成员)

```
fun salute() = println("Salute")
run(::salute)
```

## 集合的函数式API	

**基础:filter和map**

​	fliter函数可以从集合中移除你不想要的元素，但是它并不会改变这些元素。元素的变换可以使用map。

```
val list = listOf(1,2,4,5)
println(list.filter{it %2 == 0}
```

```
val lsit = listOf(1,2,3,4)
println(list.map{it * it})
```

**all、any、count和find：对集合应用判断式**

all函数:所有元素都满足判断式

any函数:至少存在一个匹配的元素

count函数:有多少个元素满足了判断式

find函数:返回第一个符合条件的元素

count vs size

**count元素只跟踪匹配元素的数量，不关心元素本身，所以更高效**

**groupBy:把列表转换成分组的map**

**flatMap和flatten:处理嵌套集合中的元素**



## 惰性集合操作：序列

​	使用map和filter这些函数会及早地创建中间集合，也就是说每一步的中间结果都存储在一个临时列表。**序列给了你执行这些操作的另一种选择，可以避免创建这些临时中间对象。**

​	如果数据较多，为了提高效率，可以把操作变成序列，而不是直接使用集合:

​		

```
people.asSequence() // 把初始集合转换成序列
	.map(Person::name)   // 序列支持和集合一样的API
	.filter{it.startsWith("A")}
	.toList()  // 把结果序列转换回列表
```

​	Kotlin惰性结合操作的入口就是Sequence接口。这个接口表示的就是一个可以逐个列举元素的元素序列。Sequence只提供了一个方法，iterator，用来从序列中获取值。

​	**带接收者的lambda：“with”和"apply"**

​	在lambda函数体内可以调用一个不同对象的方法，而且无须借助任何额外限定符:这种能力在Java中是找不到的。**这样的lambda叫作带接收者的lambda。**

​	**“with”函数**

​	很多语言都有这样的语句，可以用它对同一个对象执行多次操作，而不需要反复把对象的名称写出来。

​	

普通

```
fun alphabet():String{
	val result = StringBuilder()
	for(letter in 'A'..'Z'){
		result.append(letter)
	}
	result.append("\n Now I Know the alphabet!")
	return result.toString()
}
```

使用with

```
fun alphabet():String{
	val stringBuilder = StringBuilder()
	return with(stringBuilder){
		for(letter in 'A'..'Z'){
			this.append(letter)
		}
		append("\n Now I know the alphabet!")
		this.toString()
	}
}
```

​	with结构看起来像是一个特殊的语法结构，但是它实际上是一个接收两个参数的函数：这个例子中两个参数分别是stringBuilder和一个lambda。

​	**带接收者的lambda和扩展函数**

​	this指向的是函数接收者。在扩展函数体内部，this指向了这个函数扩展的那个类型的实例，而且也可以被省略掉，让你直接访问接收者的成员。注意一个扩展函数某种意义上来说就是带接收者的函数。

简化代码

```
fun alphabet() = with(StringBuilder()){
	for(letter in 'A'..'Z'){
		append(letter)
	}
	append("\n Now I know the alphabet!")
	toString()
}
```



**“apply”函数**

​	apply函数几乎和with函数一模一样，唯一的区别是apply始终会返回作为实参传递给它的对象(换句话说，接收者对象)

​	

```
fun alphabet() = StringBuilder().apply {
	for(letter in 'A'..'Z'){
		append(letter)
	}
	append("\nNow I know the alphabet!")
}.toString()
```

​	**apply被声明成一个扩展函数。它的接收者变成了作为实参的lambda的接收者。执行apply的结果是StringBuilder，所以接下来你可以调用toString把它转成String。**



​	**总结**

​	