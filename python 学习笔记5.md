---
title: python学习笔记之* zip()了解
---
#1.把list的每一个值赋给不同的变量
python太灵活了，直接给list中的每一个值定义不同的变量，以逗号分隔就行，但是左边的变量的个数必须与右边的list的长度一样
```python
aa,bb,cc = ['1',2,'ccc']
print(aa)
print(bb)
print(cc)
```
左边的变量也可以指定是一个数组，在变量前加*号代表是数组，包含的时候余下所有的变量值的集合，例子说明：
```python
def drop_first_last(grades):
    first, *middle, last = grades
    avg = sum(middle) / len(grades)
    print(avg)

drop_first_last([1,2,3,4,5])
```
上述代码中，fir代表的是1，last代表的是5，middle代表的是[2,3,4] 

#2.zip 压缩
目前看到的是把两个数组压缩到一起，例子如下：
```python
a = [1,2,3]
b = ['a','b','c']
for q,w in zip(a,b):
    print(q,w)

```

#3.lambda 表达式
lambda可以理解为没有名字的方法，写法为lambda x(x为参数):x*7(此处为函数语句)。
简单来说，编程中提到的 lambda 表达式，通常是在需要一个函数，但是又不想费神去命名一个函数的场合下使用，也就是指匿名函数。  
//TODO 不好理解，以后慢慢体会
```python
answer = lambda x: x*7
print(answer(10))
```

#4.map 关键字  
map(fuction,list),第一个为需要执行的函数，第二个为一个list。如果这样调用一个函数，则遍历list中的每一个值，执行方法，然后得到一个新的map object。
```python
in_come = [10,30,60]

def double_money(dollers):
    return  dollers * 2

map1 = map(double_money,in_come)
new_income = list(map1)
print(new_income)

```


  

  
