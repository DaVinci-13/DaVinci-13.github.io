---
title: Android和IOS交互
layout: doc
date:   2023-04-07 19:23:00 +0800
categories: Unity3d, Android IOS
---

# Android交互
## Unity API 调用 Android 交互方法：

    ```csharp
    // 获得位于com.unity3d.player包下的UnityPlayer类，固定写法  
    AndroidJavaClass jc = new AndroidJavaClass("com.unity3d.layer.UnityPlayer");   // 参数是包名+类名
    // 获得jc所代表的类里的currentActivity对象，固定写法。这是Unity供的classes.jar中的功能，可通过currentActivity获取到安卓端代MainActivty的对象  
    AndroidJavaObject jo = jc.GetStatic<AndroidJavaObject>"currentActivity");
    // 调用MainActivty中的自定义方法  
    text.text = jo.Call<int>("add", 1, 2).ToString();
    ```

## Android 工程调研 Unity 方法
- 1、打开Android Studio新建一个项目，新建一个模块（Module），取名UnityAndroidLibrary。注意选择最小SDK16，因为Unity最小支持的是16。
- 2、在该模块（ProjectName/UnityAndroidLibrary/rc/main/java/packageName/）下新建一个Empty Activity。创建时勾上Launcher Activity。
- 3、删除跟该界面一同生成的Mactivity_main.xml布局文（因为之后布局归Unity管理），同时删除该模块MainActivity中onCreate()里调用setContentView()法。
- 4、进入Unity的安装目录（如D:\Unity 5.4.f1\Editor\Data\PlaybackEngines\AndroidPlayerVariations\mono\Release\Classes下）复制classes.jar文件，粘贴到该模块UnityAndroidLibrary/libs目录下。右键该jar选择dd as Library，选Add to Module UnityAndroidLibrary。
- 5、打开UnityAndroidLibrary模块的AndroidManifest.xml清单文件，该文件会覆盖掉Unity一些设置，修改如下。（从默认的app模块中的清单文件拷过来，把报错的地方去掉即可。记得加后面的meta-data点）
- 6、回到模块的MainActivity，修改该类继承自UnityPlayerActivity。在该类中添加自定义的方法，用给Unity调用
- 7、在AS中Project目录选中unityandroidlibrary，Build菜单下选Make Module unityandroidlibrary’单独编译这个模块。
- 8、在unityandroidlibrary/build/intermediates/bundles/debug目录右键Show in Explorer。删除debug/libs/classes.jar（等同于刚从Unity那边拷过来的内容），把debug/classes.jar拖到debug/libs中（这个是包含了刚新增的扩展方法的）。把libs和res这两个文件夹备份（如复制到桌面）。　
- 9、在unityandroidlibrary/buildintermediates/manifests/full/debugAndroidManifest.xml右键Show in Explorer，也把个清单文件复制出来（如复制到桌面）。打开在桌面的副本修改package包名为在Unity中想要的包名，如包名最后段改为unityandroidtest（注意包名要全部小写）。
- 10、打开Unity，创建一个工程UnityAndroidTestBuild Settings切换为安卓平台，Player Settings修改包名，包名同上一步的一致（先调平台再调包名）。Assets下新建文件夹Plugins/Android（名字固定的，心别漏了s），将上两步得到的三个文件拖到该文件夹中。
- 11、新建一个C#脚本，VS打开编辑如下。把该脚本挂到一场景中的游戏对象上（如Main Camera)。
- 12、最后一步，连上真机并打开USB调试，Build & Run，路径选择桌面。此时会把APK输出到桌面并安装到真上运行，即可看到调用结果。下图是我用AS的安卓模拟器（AVD）运行的效果。注意了，要打包发布出来用，直接在Unity编辑器点运行会报错，但打包出来安卓机运行没有问题的。

    ```java
    //Andoird调Unity：
    UnityPlayer.UnitySendMessage("Main Camera", "ChangeColor", "");
    ```

---
# IOS交互