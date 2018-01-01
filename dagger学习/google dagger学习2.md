---
title: google dagger2 学习2
---
#1.概念理解
 **@Inject**   
  
  声明依赖对象
 
 **@Module @Provides**   
  
  默认情况下，当注入一个对象的时候，Dagger会调用该类声明对象的方法，new InjectA().  但是有些情况下不适用，
  例如注入对象是接口的时候，或者是引用的第三方类。为了满足这些情况下的使用，Dagger提供@Provides注解方法，方法的返回值就是@Inject所依赖的对象，所有的@Provides方法必须属于一个Module，所以就有了Module注解类。也就是说Module提供了依赖的对象。通常情况下，@Provides方法以一个provide前缀开头，Module类以一个Module字符结尾。
    
 **@Component**  
  
   @Component连接Module和Inject，就像java程序的main方法和android里面的Application类一样，定义了入口。  
   component为injector(注入器) 实际发生inject的人 

 **@singleton**  
 @singleton 单例注解，在所以的依赖中，只提供一个对象实例。

#3.参考资料

http://blog.csdn.net/tiankong1206/article/details/45967935
http://google.github.io/dagger/users-guide  
http://saulmm.github.io/when-Thor-and-Hulk-meet-dagger2-rxjava-1


















