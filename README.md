 # x5webview-cordova-plugin
x5webview-cordova-plugin 是腾讯浏览服务(TBS)为cordova框架提供的用于android平台的cordova插件，旨在为android平台提供更好的webview浏览体验．

一．接入步骤：
1.向cordiva工程中添加x5webview插件,有如下两种方式：
```
(1)cordova plugin add x5webview-cordova-plugin
(2)cordova plugin add https://github.com/runner525/x5webview-cordova-plugin.git

```

2. config.xml
```
<preference name="webView" value="org.apache.cordova.x5engine.X5WebViewEngine"/>
```

3. init
```
import android.util.Log;
import com.tencent.smtt.sdk.QbSdk;

//加载X5内核
QbSdk.PreInitCallback cb = new QbSdk.PreInitCallback() {

    @Override
    public void onViewInitFinished(boolean arg0) {
        // TODO Auto-generated method stub
        //x5內核初始化完成的回调，为true表示x5内核加载成功，否则表示x5内核加载失败，会自动切换到系统内核。
        Log.w("app", " X5加载结果 " + arg0);
    }

    @Override
    public void onCoreInitFinished() {
        // TODO Auto-generated method stub
    }
};
//x5内核初始化接口
Log.d("app", " X5加载");
QbSdk.initX5Environment(getApplicationContext(),  cb);

```

4. platforms/android/gradle.properties
```
android.useDeprecatedNdk=true
```

二．熟悉android开发的同学可以参考x5官网来灵活使用x5内核．常用链接如下：

官网(https://x5.tencent.com/tbs/)

常见问题(https://x5.tencent.com/tbs/faq.html)

论坛(http://bbs.mb.qq.com/forum-112-1.html)

内核加载问题检测工具(http://bbs.mb.qq.com/thread-1944983-1-1.html)

