---
title: python学习笔记之基本语法
---
#1.变量声明  
python的变量标识符没有类型，不像java，必须指明变量的类型，个人感觉严谨程度java > javascript > python.   

#2.if/elif/else  
python的语法和java的还是有区别的
if xxx: //无括号 只有一个冒号
    xxx // 无分好
elif xxx :
     xxxx
else:
    xxxxx

#3.for
for循环的语法和java也有区别，如下：
for x in xx:
    xxxxx

#4.range/while
range:边界，这个java里面没有的，range(10)指的是从0到9的一个边界。range(1,10)指的是从1到9的边界。range(5,45,6)指的是从5到45并且自增值为6的一个边界，前两个自增的边界为1。例子如下：
for x in range(10)：
    xxxx
    
while：当什么情况下做什么操作，与java的意思一样，写法如下:
while xxx：
    xxxxx


#5.comments/break/continue 
comments:注释，python行注释使用#xxxx号，段落注释使用'''xxxx'''。  
break:学过其他语言的应该很好理解，跳出当前循环。  
continue:跳出当前循环，执行下次循环。  
  
