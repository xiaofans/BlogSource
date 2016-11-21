---
title: google threadsample 多线程间通信学习
---
#1.研究    

   一般在listview中的adapter若涉及到异步操作的时候(加载图片)，往往需要开启多线程。现在对于图片的展示有比较成熟的开源框架，所以可以很容易的实现。如果是一些别的问题，就需要自己去实现了。我在做自己的项目中遇到了一个遍历指定目录的视频，并且截取视频的一个缩略图。在生成视频的缩略图的时候，需要进行耗时操作，经过一番查找之后，发现google的这个例子很有学习意义，所以就下载了源码进行研究。
  
> **1.0 地址** 

http://developer.android.com/training/multiple-threads/index.html

我自己做的gradle版本  
https://github.com/xiaofans/GoogleThreadSample  


> **1.1 threadsample的功能**  

加载网络图片  
缓存网络图片 


> **1.2 threadsample的思路**  

把下载图片和解析图片封装成任务类PhotoTask,使用一个LinkedBlockingQuene存放并循环使用PhotoTask去进行图片下载和解析。这里的循环使用是指当一个PhotoTask完成的时候，把该Task装入TaskQuene中，再有一个新的图片的时候，从TaskQuene取出该Task去下载新的图片，若当前TaskQuene为空，重新起一个PhotoTask实例。

类PhotoManager为单例，startDownload,removeDownload,cancelAll等主要Api,方便调用者调用。PhotoManager依赖PhotoTask,负责处理Task的状态，图片展示通过Handler与主线程(控件ImageView)进行通信。PhotoDecodeRunnable和PhotoDownloadRunnable分别对图片进行解析和下载，在两个不同的线程池中。这两个线程暴露出接口，于PhotoTask通信，传递下载或者解析状态。

PhotoTask里通过弱引用引用了ImageView的自定义类PhotoView,等下载完毕之后方便显示图片。


项目同时使用了LruCache内存缓存机制，对已经下载完毕的图片进行缓存，在加载图片的时候，提供了是否缓存的Api。



#2.总结  
> **2.1 onAttachedToWindow与onDetachedFromWindow**  
 
这两个方法经常在自定义控件的时候用到  
onAttachedToWindow 附在窗口   
onDetachedFromWindow  与窗口分离  

http://developer.android.com/reference/android/view/View.html  
该文中有说明自定义View的时候应该重写的方法

> **2.2 Quene**   

Quene队列，先进先出，项目中用到了LinkedBlockingQuene.Quene提供了如下方法  
add(E e)  
element()  
offer(E e)  
peek()  
pool()    
remove()  

> **2.2 LinkedBlockingQuene**  

并发库中的BlockingQueue是一个比较好玩的类，顾名思义，就是阻塞队列。该类主要提供了两个方法put()和take()，前者将一个对象放到队列尾部，如果队列已经满了，就等待直到有空闲节点；后者从head取一个对象，如果没有对象，就等待直到有可取的对象。 












