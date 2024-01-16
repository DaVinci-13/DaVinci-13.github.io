---
title: Addressable
layout: doc
date:   2024-01-16 10:28:00 +0800
categories: unity3d, Asset Management, Addressable
---

# Addressable
基于assetbundle； 更方便地管理

## 设置

### Addressable Groups
1. 获取所有的Addressable Name：
读取对应的Addressable Asset Group设置的YAML格式的*.asset文件内容，使用文件和字符串相关类进行操作，取得“m_address”属性。

2. 创建Group

3. 设置Build Path和Load Path

4. Build

5. Play Mode Script模式
    - Use Asset Database（fastest）：编辑器下调试使用，直接从AssetDatavase加载
    - Simulate Groups（advanced）：
        - 在不打包的情况下模拟AssetBundle操作
        - Send Profiler Events：bundle包加载释放分析
    - Use Existing Build（requires built groups）：实际上是从AssetBundle打包和加载

6. Label： Addressable Asset Group设置中Build Mode可根据Label进行aa包的简单分包
    - 一个资源可以标记多个Label
    - 批量按Label加载：


### 缓存
AA包下载缓存路径设置：Initialization Objects

### Addressable Profiles
1. 四个路径
LocalBuildPath  
LocalLoadPath  
RemoteBuildPath  
RemoteLoadPath  

2. Local和Remote的区别：包体内的资源包和包体外的资源包

3. 脚本动态设置路径方法：
    1. 选择custom,输入``{NameSpace.ClassName.StaticStr}``，
        - 原理：根据反射得到对应类的静态string类型值
        - 限制：应用运行过程中修改值无效
    2. E直接修改catalog.json中的m_InternalIds属性
        - 位置：  
            Editor环境下，[ProjectPath]/Library/com.unity.addressable/aa/{BuildTarget}/catalog.json；  
            Windows环境下，[AppPath]/[AppName]_Data/StreamingAssets/aa/catalog.json.
        - 限制：只有PC才能获得StreamingAssets路径下的读写权限

### Event Viewer
查看调试信息：bundle包的时间线分（加载、释放、引用计数）  


## 加载资源
1. 通过Addressable Name加载
2. 通过Asset Reference加载：
Assets弱引用
```csharp
public class Main:MonoBehaviour
{
    public AssetReference ref;
    void Start()
    {
        ref.LoadAssetAsync<GameObjcet>().Cpmpleted += (obj)=>{};
    }
}
```
3. AA包查找顺序：本地缓存->远程资源

4. 释放：``  Addressable.Release(obj); ``

## 增量更新
1. 基本操作
前提：`Addressable Group Setting`设置打开`Build Remote Catalog`。  
原理：Build AA时除了AA包还会生成本次构建的catalog的`.hash`和`.json`文件。根据这两个文件本地缓存与Remote资源比对进行增量更新。
操作：`Update a Previous Build`
注意：**使用时更新**，只有用到此资源时才去检测更新，但可以通过脚本API更改为应用启动时更新。

2. 应用启动时更新
步骤： ``CheckForCatalogUpdates`` -> ``UpdateCatalogs`` -> ``GetDownloadSizeAsync`` -> ``DownloadDependciesAsync``  
注意：更新过程中可能存在用户操作和网络问题，此时可以通过AsyncOperationHandle的Status状态码进行处理，并提示重试。
e.g. 
```csharp
public class CheckUpdateAndDownload : MonoBehaviour
{
    void Start()
    {
        StartCoroutine(DoUpdateAddressable());
    }
    IEnumerator DoUpdateAddressable()
    {
        AsyncOperationHandle<IResourcesLocator> initHandle = Addressables.InitializeAsync();
        yield return initHandle;
        //检测更新
        var checkHandle = Addressables.CheckForCatalogUpdates(true);
        yield return checkHandle;
        if(checkHandle.Status != AsyncOperationStatus.Succeed)
        {
            Debug.LogError("CheckForCatalogUpdates Errors\n" + checkHandle.OperationException.ToString());
            yield break;
        }
        if(checkHandle.Result.Count>0)
        {
            var updateHandle = Addressables.UpdateCatalogs(checkHandle.Result, true);
            if(updateHandle.Status != AsyncOperationStatus.Succeed)
            {
                Debug.LogError("UpdateCatalogs Errors\n" + updateHandle.OperationException.ToString());
                yield break;
            }
            //更新列表迭代器
            List<IResourceLocator> locators=updateHandle.Result;
            foreach(var locator in locators)
            {
                List<object> keys=new List<object>();
                keys.AddRange(locator.Keys);
                //获取待下载文件总大小
                var sizeHandle = Addressables.GetDownloadSizeAsync(keys.GetEnumerator());
                yield return sizeHandle;
                if(sizeHandle.Status != AsyncOperationStatus.Succeed)
                {
                    Debug.LogError("GetDownloadSizeAsync Errors\n" + sizeHandle.OperationException.ToString());
                    yield break;
                }
                long totalDownloadSize=sizeHandle.Result;
                if(totalDownloadSize>0)
                {
                    //下载
                    var downloadHandle = Addressables.DownloadDependciesAsync(keys, true);
                    while(!downloadHandle.S=IsDone)
                    {
                        if(downloadHandle.Status == AsyncOperationStatus.Failed)
                        {
                            Debug.LogError("DownloadDependciesAsync Errors\n" + downloadHandle.OperationException.ToString());
                            yield break;
                        }
                        float percetage = downloadHandle.PercentCompelete;
                        Debug.Log($"已下载{percetage}");
                        yield return null;
                    }
                    if(downloadHandle.Status == AsyncOperationStatus.Succeed)
                    {
                        Debug.Log("下载完毕！");
                    }
                }
            }
        }
        else{
            Debug.Log("没有检测到更新");            
        }
        //todo： EnterGamePlayLogic
    }
}
```

## 打包工具继承
官方：Build -> Defaut Build Script。