# RetrofitUrlManager
[ ![Jcenter](https://img.shields.io/badge/Jcenter-v1.2.5-brightgreen.svg?style=flat-square) ](https://bintray.com/jessyancoding/maven/retrofit-url-manager/1.2.5/link)
[ ![Build Status](https://travis-ci.org/JessYanCoding/RetrofitUrlManager.svg?branch=master) ](https://travis-ci.org/JessYanCoding/RetrofitUrlManager)
[ ![Android Arsenal](https://img.shields.io/badge/Android%20Arsenal-RetrofitUrlManager-brightgreen.svg?style=flat-square) ](https://android-arsenal.com/details/1/6007)
[ ![API](https://img.shields.io/badge/API-9%2B-blue.svg?style=flat-square) ](https://developer.android.com/about/versions/android-2.3.html)
[ ![License](http://img.shields.io/badge/License-Apache%202.0-blue.svg?style=flat-square) ](http://www.apache.org/licenses/LICENSE-2.0)
[ ![Author](https://img.shields.io/badge/Author-JessYan-orange.svg?style=flat-square) ](https://www.jianshu.com/u/1d0c0bc634db)
[ ![QQ-Group](https://img.shields.io/badge/QQ群-301733278-orange.svg?style=flat-square) ](https://shang.qq.com/wpa/qunwpa?idkey=1a5dc5e9b2e40a780522f46877ba243eeb64405d42398643d544d3eec6624917)

## Let Retrofit support multiple baseUrl and can be change the baseUrl at runtime.

## Overview
![overview](art/overview.gif)

## Introduction
以最简洁的 **Api** 让 **Retrofit** 同时支持多个 **BaseUrl** 以及动态改变 **BaseUrl**.

## Notice
[**框架的分析和思路**](http://www.jianshu.com/p/2919bdb8d09a)

[**更完整的 Sample**](https://github.com/JessYanCoding/ArmsComponent)

## Download
``` gradle
 compile 'me.jessyan:retrofit-url-manager:1.2.5'
```

## Usage
### Initialize
``` java
 // 构建 OkHttpClient 时,将 OkHttpClient.Builder() 传入 with() 方法,进行初始化配置
 OkHttpClient = RetrofitUrlManager.getInstance().with(new OkHttpClient.Builder())
                .build();
```

### Step 1
``` java
 public interface ApiService {
     @Headers({"Domain-Name: douban"}) // 加上 Domain-Name header
     @GET("/v2/book/{id}")
     Observable<ResponseBody> getBook(@Path("id") int id);
}

```

### Step 2
``` java
 // 可在 App 运行时,随时切换 BaseUrl (指定了 Domain-Name header 的接口)
 RetrofitUrlManager.getInstance().putDomain("douban", "https://api.douban.com");
```

### If you want to change the global BaseUrl
```java
 // 全局 BaseUrl 的优先级低于 Domain-Name header 中单独配置的,其他未配置的接口将受全局 BaseUrl 的影响
 RetrofitUrlManager.getInstance().setGlobalDomain("your BaseUrl");

```

## Donate
![alipay](https://raw.githubusercontent.com/JessYanCoding/MVPArms/master/image/pay_alipay.jpg) ![](https://raw.githubusercontent.com/JessYanCoding/MVPArms/master/image/pay_wxpay.jpg)

## About Me
* **Email**: <jess.yan.effort@gmail.com>
* **Home**: <http://jessyan.me>
* **掘金**: <https://gold.xitu.io/user/57a9dbd9165abd0061714613>
* **简书**: <http://www.jianshu.com/u/1d0c0bc634db>

## License
```
 Copyright 2017, jessyan

   Licensed under the Apache License, Version 2.0 (the "License");
   you may not use this file except in compliance with the License.
   You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

   Unless required by applicable law or agreed to in writing, software
   distributed under the License is distributed on an "AS IS" BASIS,
   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
   See the License for the specific language governing permissions and
   limitations under the License.
```
