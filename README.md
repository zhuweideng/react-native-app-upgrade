
React Native App 版本升级封装库，兼容Android4以上所有版本

### 一、功能
#### Android
```xml
（1）版本检测
（2）下载更新
（3）进度提示
（4）自动安装
```

#### iOS
```xml
（1）版本检测
（2）自动跳转App Store
```

### 二、使用

```xml
  yarn add react-native-app-upgrade-wd

  // or 
  npm install react-native-app-upgrade-wd
 
```

iOS
打开Xcode, 将 ios_upgrade 导入到项目目录。


```javascript

  import { 
    downloadApk,
    versionName,
    versionCode,
    openAPPStore,
    checkIOSUpdate,
    addDownLoadListener,
  } from 'rn-app-upgrade';
  
  //可通过RN.versionName获取apk版本号和远程版本号进行比较
  if(Android) {
    if(res.versionCode > versionCode) {
        downloadApk({
            interval: 666, // listen to upload progress event, emit every 666ms
            apkUrl: "https://xxxx.apk",
            downloadInstall: true,
            callback: {
                onProgress: (received, total， percent) => {},
                onFailure: (errorMessage, statusCode) => {},
                onComplete: () => {},
            },
        });
    }
  } else {
    const IOSUpdateInfo = await checkIOSUpdate(appid, 当前版本号);
    IOSUpdateInfo.code // -1: 未查询到该App 或 网络错误 1: 有最新版本 0: 没有新版本
    IOSUpdateInfo.msg
    IOSUpdateInfo.version
  }
```


> [react-native-blob-util](https://github.com/RonRadtke/react-native-blob-util)


> 添加 tag

```
比如：我现在给当前代码，提交tag:v2.2.0
 
# 本地修改
git tag -a 2.2.0 -m "2.2.0"
 
git push origin master
 
 
# 提交远端
git push origin --tag
 
# 成功，登录github查看即可
```