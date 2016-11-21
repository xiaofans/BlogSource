---
title: android下事件传递机制
---
#1.事件传递 dispatchTouchEvent onTouchEvent 
1.所有的Touch事件被封装成了MotionEvent,每个事件都是以 ACTION_DOWN 开始 ACTION_UP 结束。  
  
2.事件从Activity的dispatchTouchEvent开始传递，只要没有被停止或者拦截，从最上层的View或者ViewGroup一直向下子View传递。子View可以通过onTouchEvent对事件进行处理。  

3.事件由父View向子View传递，ViewGroup可以通过onInterceptTouchEvent对事件进行拦截，停止其向下传递。
  
4.如果事件由上向下一直没有被停止，而且最底层view没有消耗事件，事件就会向上传递，这个时候父View可以对事件进行消费，如果没有被消费的话，最终会到Activity的onTouchEvent的方法。  

5.如果 View 没有对 ACTION_DOWN 进行消费，之后的其他事件不会传递过来。  

一个无阻碍事件的传递流程如下:  
**Activity.dispatchTouchEvent --> ViewGroup.dispatchTouchEvent ---> View.DispatchEvent  ---> View.OnTouchEvent --> ViewGroup.OnTouchEvent ---> Activity.onTouchEvent.**


#2.事件拦截  onInterceptTouchEvent 
事件由父 View(ViewGroup)传递给子 View，ViewGroup 可以通过 onInterceptTouchEvent()对事件做拦截，停止其往下传递。 
上述无障碍事件传递若包含拦截的话会是这样:
**Activity.dispatchTouchEvent --> ViewGroup.dispatchTouchEvent ---> ViewGroup.OnInterceptTouchEvent(若return true的话，事件不会向下传递了) --> View.DispatchEvent**  

关于代码如下:
```java
public boolean dispatchTouchEvent(MotionEvent ev) {
    if(!onInterceptTouchEvent()){
        for(View child : children){
            if(child.dispatchTouchEvent(ev))
                return true;
        }
    }
    return super.dispatchTouchEvent(ev);
}
```


#3.onInterceptTouchEvent和dispatchTouchEvent的区别

1.ViewGroup有onInterceptTouchEvent事件  
2.dispatchTouchEvent 是传递事件 
3.onInterceptTouchEvent 决定是否拦截事件 传递给子view或者不传递给子view



#4.setOnTouchListener与onTouchEvent
OnTouchListener 优先于 onTouchEvent()对事件进行消费。 如果进行了setOnTouchListener，那么OnTouchEvent就不会调用了，而是调用Listener中的onTouchEvent.


#5.requestDisallowInterceptTouchEvent 
不允许父View拦截事件。放设置为true的时候。


#6.参考资料
http://stackoverflow.com/questions/9586032/android-difference-between-onintercepttouchevent-and-dispatchtouchevent
http://a.codekk.com/detail/Android/Trinea/%E5%85%AC%E5%85%B1%E6%8A%80%E6%9C%AF%E7%82%B9%E4%B9%8B%20View%20%E4%BA%8B%E4%BB%B6%E4%BC%A0%E9%80%92



















