---
title: google dagger2 学习3
---
#1.在项目中引入dagger2(android-boilerplate分析)  
1.1 gradle文件配置  
首先在app module(或者你定义的module)下的build.gradle文件中加入dagger依赖和dagger需要的annotation依赖。
```java
 compile "com.google.dagger:dagger:$DAGGER_VERSION"
 apt "com.google.dagger:dagger-compiler:$DAGGER_VERSION"
 provided 'org.glassfish:javax.annotation:10.0-b28' //Required by Dagger2
```  
然后再根目录的gradle文件中加入  
```java
buildscript {
  repositories {
    jcenter()
  }
  dependencies {
    classpath 'com.android.tools.build:gradle:1.2.2'
    classpath 'com.neenbedankt.gradle.plugins:android-apt:1.8' /**此处加入apt插件依赖**/
    
  }
}
```  

1.2 android-boilerplate 分析  
android-boilerplate是一个基于mvp架构的一个实例，里面有使用dagger2. 这里说一下其中关于dagger的使用。
该项目中有一个injection的包，主要包含自定义的component module.其结构大概如下:  

```json
injection
| --component
    | --ActivityComponent    生命周期同Activity的组件 @PerActivtiy
    | --ApplicationComponent 生命周期同Application的组件 @Singleton
| --module
    | --ActivityModule      该Module提供Activity实例，可为fragment提供Context 这其中的Provide方法都使用了@PerActivity注解   
    | --ApplicationModule   该Module提供的对象存活于在Application的生命周期中，这其中的Provide方法都使用了Singleton注解
| --ActivityContext         Activity的Context自定义限定注解  
| --ApplicationContext      Application的Context自定义限定注解  
| --PerActivity             自定义PerActicity Scope，其ActivityComonent的生命周期同Activity的生命周期
```  


其中用到了  
**@Qualifier**限定符来限定了依赖是ActivityContext还是ApplicationContext.  

**@Scope** scope给我们带来了“局部单例”，生命周期取决于scope自己（特殊的单例）,单例也是一种Scope，我们需要自定义Scoped原因是Scope必须有与其对应生命周期的组件在一起。  


#2.参考资料
https://github.com/ribot/android-boilerplate  
http://gold.xitu.io/entry/5642b89c00b0c060fe88d97e  
http://blog.csdn.net/qq_17766199/article/details/50606011

https://github.com/codepath/android_guides/wiki/Dependency-Injection-with-Dagger-2  
http://fernandocejas.com/2015/04/11/tasting-dagger-2-on-android/  
http://www.cnblogs.com/tiantianbyconan/archive/2016/01/02/5095426.html



















