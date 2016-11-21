---
title: react-native学习笔记3问题记录
---

#1.fetch post请求
使用fetch 发送post请求的方式如下:
```js
    let formData = new FormData();
    formData.append('validateCode', code);
    formData.append('validateKey', key);
    formData.append('username', username);
    formData.append('pwd', password);
    formData.append('remeberme', '');
    formData.append('backUrl', '');
        fetch(login,{
            method:'post',
            body:formData,
            headers: {
                'Accept': 'application/json',
                'Content-Type': 'multipart/form-data'
            },
        })
        .then((response) => response.text())
        .then((responseJson) => {
           
            })
        .catch((error) => {
            console.error(error);
        });
```
需要注意的是，fetch的get请求会返回实际的文本，而post请求返回的response会包含headers,body等信息,需要使用(response) ==> response.text()来得到实际返回的内容。

#2.react native post形式上传图片
目前测试的是使用XMLHttpRequest进行的form表单上传，fetch形式的上传应该也可以，上传方式如下:
```js
  _uploadAvatar(){
        var photo = {
            uri: this.state.imageSource,
            type: 'image/jpeg',
            name: this.state.imageSource.substring(this.state.imageSource.lastIndexOf('/')),
        }
        var xhr = new XMLHttpRequest();
        xhr.open('POST',uploadImages);
        xhr.onload = () => {
            let jsonRes = JSON.parse(xhr.responseText)
            if (xhr.status !== 200) {
                Alert.alert(
                    '提示',
                    '上传失败，请重试 '
                );
                return;
            }
            this.setState({fileid:jsonRes.fileid})
            Alert.alert(
                '上传成功',
                jsonRes.fileid
            );
        };
        var formdata = new FormData();
        formdata.append('Filedata', photo);
        if (xhr.upload) {
            xhr.upload.onprogress = (event) => {
                console.log('upload onprogress', event);
                if (event.lengthComputable) {
                    this.setState({uploadProgress: event.loaded / event.total});
                }
            };
        }
        xhr.send(formdata);
    }
```

#3.ract native 处理android返回按键
react native的程序是一个单个的activity(待确认),点击返回会回到主页面，为了使在二级页面点返回的时候，不回到home页,react native引入
BackAndroid.使用方式如下:
```js
var navigator; 

React.BackAndroid.addEventListener('hardwareBackPress', () => {
    if (navigator && navigator.getCurrentRoutes().length > 1) {
        navigator.pop();
        return true;
    }
    return false;
});

<Navigator ref={(nav) => { navigator = nav; }} />
```
参考链接:http://stackoverflow.com/questions/34496246/handling-back-button-in-react-native-navigator-on-android

#4.页面之间的传值
以页面A,B为例
A页面向B页面传递
```
A页面
  _this.props.navigator.push({
                title: 'xxx',
                id: 'xxx1',
                params: {
                   key:value
                }
            })
B页面接收
this.props.key
```
此时,B页面位于上方，要是打算传值给A页面的话，就需要使用回调的方式
```
A页面
  _gotoTrivalProductAdd(){
        this.props.navigator.push({
            title: '添加商品',
            id: 'trivalProductAdd',
            params: {
                planId:this.state.id,
            },
            callback:this._onProductAdded //使用CallBack
        })
    }

    // 回调函数实现
    _onProductAdded(detail){
        var products = this.state.products;
        products.push(detail)
        this.setState({products:products})
    }
    
B页面回传
   _this.props.route.callback(xxx);
```
#5.web Storm ide激活码 2016.2.3
http://blog.csdn.net/it_talk/article/details/52448597







  


