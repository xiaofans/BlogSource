---
title: python学习笔记之方法(functions)
---
#1.方法定义 
python里使用**def**关键字来定义方法，一个普通方法的示例如下  
```python
def hello():
    print('xxxxxxxxx');

hello()
```
#2.返回值 
同大部分语言一样，返回值使用**return**关键字，带有返回值的方法示例如下:
```python
def getAStr():
     str = 'hello'   
     return str

getAStr()
```
#3.参数，默认参数，可扩展的参数，拆包参数
python对参数的支持比较灵活(同java语言相比)，支持固定的参数，可变的参数，拆包参数。
**固定参数**简单理解，即给方法传递单个的参数示例如下。  
```python
def sayhello(name):
    print('hello',name)
sayhello('xiaofan')
```
**默认参数**是值调用该方法的人没有传递参数情况下使用的值。示例如下
```python
def sayhello(name='xiaofan'):
    print(name)
sayhello()
```  
可扩展的参数就是方法本身不知道传递的参数数量，可能是一个，可能是多个，***在参数前加*即可定义可扩展的参数***
```python
def sayhello(*name):
    for n in  name:
        print('hello',name)
sayhello('xiaofan','xiaowang','dami')
```
**拆包参数**不太好理解，英文上的定义为unpacking arguments.个人理解为与可扩展的参数相反，例如一个方法需要多个参数，一个一个传递写起来比较麻烦，可以把这些参数放到一个数组中，然后传给方法，同样，在传给方法的时候需要加*号。
```python
def sayhello(name,where,date):
    print('hello',name,where,date)

xiaofan = ['xiaofan','henan','2016-07-05'];
sayhello(*xiaofan)
```

#4.变量作用域  
方法内定义的变量作用域为方法内。  
方法外定义的变量，其下方的代码可以访问到。

  

  
