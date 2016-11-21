---
title: react-native入门(环境，ide选择)
---
#1.react与react native  
react为facebook的一个JavaScript的ui框架，react-native则是针对于手机版的。  
React:**building large applications with data that changes over time.**

#2.环境及初始化工程
**使用最简便的方式安装**  
安装chocolatey,打开cmd,使用以下命令安装: 
 
```json
@powershell -NoProfile -ExecutionPolicy Bypass -Command "iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))" && SET "PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin"  
```   

安装nodejs python react-native，打开cmd依次输入一下命令

```
choco install nodejs.install
choco install python2
npm install -g react-native-cli
```  

安装完毕之后，即可使用命令新建一个react native工程  

```
react-native init AwesomeProject
cd AwesomeProject
react-native run-android
```  

#3.ide选择
经过一番研究，目前发现有一下ide比较方便  
1.webStorm + react-native提示插件，插件地址如下:  
https://github.com/virtoolswebplayer/ReactNative-LiveTemplate  

2.vscode + react-native插件  
https://github.com/Microsoft/vscode-react-native 


#4.其他一些资源  
1.ReactNativeBase,简化语法，大大减少开发量
https://github.com/GeekyAnts/NativeBase

2.react-native项目模板化，现成组件  
https://github.com/infinitered/ignite    

3.提供一些常用系统组件  
https://getexponent.com/

4.https://github.com/yuanguozheng/JdApp 
http://blog.csdn.net/yuanguozhengjust/article/details/50553525
react native 国内资源教程


  


