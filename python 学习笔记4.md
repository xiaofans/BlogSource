---
title: python学习笔记之类class、对象object和init方法等
---
#1.类定义  
python中使用class关键字来定义一个类，后面跟类名和冒号 
```python
class Emeny:
```
#2.类方法
类方法与声明方法类似，但是第一个参数默认会有一个self参数，这个有点不太明白，先标注一下，如果不加self参数，会报错。
```python
class Emeny:
    def attack(self):
        print('ouch')
```
#3.声明对象
声明对象使用类名+括号
```python
class Emeny:
    def attack(self):
        print('ouch')

emeny = Emeny()
emeny.attack()
```
#4.类的init方法
python里面的init方法可以理解为java里面的构造方法，即在构造实例的时候会执行的方法，可以传值，进行初始化等一些操作。  下面的例子运行之后的结果为:hello init
```python
class Emeny:
   def __init__(self):
       print('hello init')

emeny = Emeny()

```

#5.类变量和实例变量
类变量:变量属于类，不随实例的改变而改变，类似于java里面的static
实例变量:变量属于实例，可以随着实例的不一样，变量不一样
```python
class Boy:
    gender = 'male' '''类变量'''

    def __init__(self,name):
        self.name = name  '''实例变量'''

```

#6.继承和多重继承
python和java一样，支持继承，继承的方式是在类名后加括号，括号指明继承的父类。  
```python
class Parent:

    def p_last_name(self):
        print('zhao')

class Child(Parent):
    def p_child_name(self):
        print('yu')

chi = Child()
chi.p_last_name()
chi.p_child_name()

```
如果想要实现多重继承的话，在类名后的括号里把继承的类以逗号分隔
```python
class Parent1:

    def p_last_name(self):
        print('zhao')

class Parent2:
    def p_family_words(self):
        print('凡人皆有一死，凡人皆需侍奉')

class Child(Parent1,Parent2):
    def my_method(self):
        print('aaa')

c = Child();
c.p_last_name()
c.p_family_words()


```

#7.pass关键字的作用
通过实例研究，个人觉得该关键字代表结束的含义，至少可以代表类结束，如只定义一个空的类，什么都没有，python解释器不知道该类是否已经结束。实例如下：  

```python
class Empty1:
    pass

e = Empty1();
```
 


  

  
