---
title: react-native学习笔记2简单总结
---

#1.组件
讲组件要先从React中说起，React的特点之一就是'Component-Based'，使用React可以构建能够管理自己状态的组件，组件可以组合从而构成复杂的页面。
由于ReactNative是React的一部分，所有RN也具有这样的属性。在RN中构建页面或者组件需要继承类Component,然后在render()方法中渲染出自己想要的ui。
对目前Component中已知的方法总结如下:
```
render() 渲染组件ui
componentDidMount 组件渲染完成，这个方法比较重要，因为一般的页面呈现都需要网络请求，可以在组件加载完毕之后进行请求。
getInitialState 在组件渲染之前调用，再可以方法里可以指定组件的初始状态
```
Component的特性  
1.props 属性参数，通过属性参数可以在组件创建时指示组件显示的内容，属性等。  
2.state 状态 组件通过state来管理数据的改变。   
对component的解释官方说明如下
```
There are two types of data that control a component: props and state. props are set by the parent and they are fixed throughout the lifetime of a component. For data that is going to change, we have to use state.
```

#2.布局 
react native中的使用flex layout 柔性布局。使用较多的有以下三个属性:
```
flexDirection:布局方式 row:横向布局 cloumn 竖向布局
justifyContent:flex-start, center, flex-end, space-around, space-between.针对主布局方向，即是flexDirection的方向作用。
alignItems:flex-start, center, flex-end, space-around, space-between.针对辅布局方向，即是flexDirection的另外一方向作用。
```
#3.网络请求/数据绑定
网络请求了解了Fetch，在得到数据后，通过state对ui进行刷新，下面是一个例子:
```
  fetchStroyDetail: function() {
    var reqUrl = BASE_URL + this.props.story.id;
    this.setState({
      isLoading: true,
      detail: null,
    });
    fetch(reqUrl)
      .then((response) => response.json())
      .catch((error) => {
        this.setState({
          isLoading: false,
          detail: null,
        });
      })
      .then((responseData) => {
        this.setState({
          isLoading: false,
          detail: responseData,
        });
      })
      .done();
  }
```
#4.本地存储  
简单的本地存储RN提供了一个AsyncStorage类，简单用法如下:
```
try {
  await AsyncStorage.setItem('@MySuperStore:key', 'I like to save it.');
} catch (error) {
  // Error saving data
}
################################################################################
try {
  const value = await AsyncStorage.getItem('@MySuperStore:key');
  if (value !== null){
    // We have data!!
    console.log(value);
  }
} catch (error) {
  // Error retrieving data
}
```

#5.参考资源 
http://blog.csdn.net/u010046908/article/details/50916511 react-native 网络请求教程
http://www.race604.com/react-native-component-lifecycle/ react native 生命周期
https://github.com/race604/ZhiHuDaily-React-Native/blob/master/StoryScreen.js 网络请求实例  
http://facebook.github.io/react-native/ 官网


  


