---
title: react-native学习笔记3 ios相关问题总结
---

#1.net work fetch failed
第一次运行ios项目，提示网络请求失败(ios9)，修改方式如下:
```
在Info.plist中的App Transport Security Settings中添加Allow Arbitrary Loads，类型为Boolean，值为yes
```

#2.安装cocoapods
https://my.oschina.net/w11h22j33/blog/206129    

#3.ios开发者证书申请  
http://blog.csdn.net/wangyueyishi/article/details/50903565   

#4.react native设置启动页图片
http://stackoverflow.com/questions/34027270/ios-launch-screen-in-react-native 
 
#5.xcode打ipa安装包
http://www.jianshu.com/p/481f8f0da6ab  

#6.react native 构建发布版本
```
 Product -> Scheme -> Edit Scheme (cmd + <) -> 选中release
```
#7.依赖第三方库
react-native-wechat-ios 微信支付 
https://github.com/beefe/react-native-wechat-ios 
 
react-native-image-crop-picker  图片选择
https://github.com/ivpusic/react-native-image-crop-picker 
  




