---
title: android的新布局了解
---
#1.原来的五大布局
LinearLayout 线性布局  
RelativeLayout  相对布局  
FrameLayout   祯布局  
AbsoluteLayout  绝对布局  
TableLayout    表格布局  
其中用的比较多的有**LinearLayout,RelativeLayout,FrameLayout**。

#2. support design library(CoordinatorLayout)
去年，android引入的support design library. 该包包含一些MetrailDesign风格的布局，包括Navigation View(导航视图),Floationg labels for editing text(一个流失布局的输入框的标签),Floating Action Button(底部悬浮按钮),Snackbar(底部可以自动消失的条),CoordinatorLayout**协调布局**

CoordinatorLayout是一个超能力的FrameLayout.  
例如:  
1.应用的顶层布局;  
2.作为一个协调子布局的容器;  

CoordinatorLayout中的view可以定义Behaviors，Behaviors可以让view之间有不同的交互方式.

#3. PercentFrameLayout和PercentRelativeLayout
PerfentFrameLayout和PercentRelativeLayout分别继承与FrameLayout和PercentRelativeLayout.根据名称就可以判断出来，支持百分比的属性，下面是用法。
```percent
<android.support.percent.PercentFrameLayout
         xmlns:android="http://schemas.android.com/apk/res/android"
         xmlns:app="http://schemas.android.com/apk/res-auto"
         android:layout_width="match_parent"
         android:layout_height="match_parent">
     <ImageView
         app:layout_widthPercent="50%"
         app:layout_heightPercent="50%"
         app:layout_marginTopPercent="25%"
         app:layout_marginLeftPercent="25%"/>
 </android.support.percent.PercentFrameLayout/>
```



#4.参考资料
http://android-developers.blogspot.jp/2015/05/android-design-support-library.html?utm_campaign=android_series_layoutattributes_012116&utm_source=medium&utm_medium=blog
https://medium.com/google-developers/layouts-attributes-and-you-9e5a4b4fe32c#.tsu2sptw8
http://blog.csdn.net/xyz_lmn/article/details/48055919




















