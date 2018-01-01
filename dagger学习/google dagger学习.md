---
title: google dagger2 学习1
---
#1.了解
Mvp模式在android下的开发越来越流行了，在学习mvp的时候接触到了Dagger，在很久以前也接触到了，但是没有认真去研究，以前是由square的团队写的，现在由谷歌来维护了，并
改了名称dagger2.  
Dagger是一个依赖注入框架，适用于android和java。   
Square的官方解释:  
A fast dependency injector for Android and Java.
#2.依赖注入
要想理解并运用Dagger,首先需要了解依赖注入的概念。  
```java
如果类A依赖类B，创建对象B的时候不是在A内部，而是通过构造函数或者Setter方法注入到A类中，称之为依赖注入。

class A{
    private B b;    
    public A(B b){
            this.b = b;
    }
    public void doSth(){
            b.xx(); // B b1 = new B(); b1.xx();(非依赖注入)
            ...
    }
}  
class B{
    public void xx(){}
}
```
dagger是一个依赖注入框架，dagger的目的就是专注于功能性代码的编写，并且易于测试。



#2.参考资料
http://stackoverflow.com/questions/130794/what-is-dependency-injection
http://q.cnblogs.com/q/33437/  
http://square.github.io/dagger/  


















