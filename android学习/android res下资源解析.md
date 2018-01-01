---
title: android res下资源解析
---

随着android sdk的更新，发现res文件夹下多了好几个文件，一直对这些文件的意义不是很清晰，今天特意抽出时间来了解一下，一方面了解，另一方面更好的开发，适配。
*  animator  放属性动画(property animation)的地方
*  anim      放补间动画(tween animation)的地方
*  color     防止颜色状态列表文件 
*  drawable  位图文件(bitmap.png, .9.png, .jpg, .gif)或者被编译成一下资源的xml文件(bitmap files.Nine-pathes.shapes.state lists animation drawables等)   
 *  drawable-land/land-v
 *  drawable-ldrtl-(m/h/no/xh/xxh/xxxh)dpi-v4  ldrtl布局方向，从左到右的布局
 *  drawable-v
 *  drawable-(m/h/no/xh/xxh/xxxh)dpi-v4
* layout  布局文件
 *  layout-land
 *  layout-ldrtl 
 *  layout-v(11,16,17,21)
 *  layout-sw600dp-land-v13 sw代表smallestwidth，系统只会在最短的屏幕可能尺寸少于600dp时使用这个资源，而不考虑用户能否看到600dp的高或宽的边缘。
 *  layout-sw600dp-land-v16
 *  layout-sw600dp-v13
 *  layout-sw720dp-v13
 *  layout-sw720dp-v16
 *  layout-w270dp-h560dp-v13
* mipmap  官方推荐放置icon启动图标，系统会进行优化，有更好的体验。
* menu 放置菜单文件
* raw  app用到的一些其他文件
* xml 可在运行时通过Resources.getXML()的任意文件。



**以下是google keep的例子**
<li>anim-v21
<li>color
<li>color-v11
<li>color-v23
<li>drawable
<li>drawable-land
<li>drawable-land-v19
<li>drawable-ldrtl-hdpi-v4
<li>drawable-ldrtl-mdpi-v4
<li>drawable-ldrtl-nodpi-v4
<li>drawable-ldrtl-xhdpi-v4
<li>drawable-ldrtl-xxhdpi-v4
<li>drawable-ldrtl-xxxhdpi-v4
<li>drawable-mdpi-v4
<li>drawable-hdpi-v4
<li>drawable-xhdpi-v4
<li>drawable-xxhdpi-v4
<li>drawable-xxxhdpi-v4
<li>drawable-nodpi-v4
<li>drawable-tvdpi-v4
<li>drawable-v19
<li>drawable-v21
<li>drawable-v23
<li>layout
<li>layout-land
<li>layout-ldrtl
<li>layout-sw600dp-land-v13
<li>layout-sw600dp-land-v16
<li>layout-sw600dp-v13
<li>layout-sw720dp-v13
<li>layout-sw720dp-v16
<li>layout-v11
<li>layout-v16
<li>layout-v17
<li>layout-v21
<li>layout-w270dp-h560dp-v13
<li>mipmap-hdpi-v4
<li>mipmap-mdpi-v4
<li>mipmap-xhdpi-v4
<li>mipmap-xxhdpi-v4
<li>mipmap-xxxhdpi-v4
<li>raw
<li>values****
<li>xml
<li>xml-17



**参考资源**  
http://developer.android.com/guide/topics/resources/providing-resources.html  
http://android-developers.blogspot.jp/2014/10/getting-your-apps-ready-for-nexus-6-and.html  
http://www.cnblogs.com/tianjian/p/3487138.html
