# OpenApi
Provide a variety of crack/free API interface(提供各种破解/免费的Api接口)

[TOC]

## 壁纸

网站：https://unsplash.com/

开放接口：https://unsplash.com/api-terms (以下提供的非此处的接口，通过其他方式获取到的)

该网站提供各种类型的高清图片，可以作为壁纸使用；当然也可以利用此资源自己开发App发布到线上，收费可以下载壁纸各种玩法。

### 分类列表

首页上有一个collections Tab，里面有不同的分类，先提供出获取当前页分类的接口，如下：

Api接口：

- Feature: https://unsplash.com/napi/collections/featured?page=1&per_page=8
- Curated: https://unsplash.com/napi/collections/curated?page=1&per_page=8

请求地址: https://unsplash.com/napi/collections/featured

请求方式：GET

请求参数：

|  参数名  | 类型 |      描述      |
| :------: | :--: | :------------: |
|   page   | Int  |     第几页     |
| per_page | Int  | 一页多少条数据 |

### 指定分类下的图片列表

Api接口：https://unsplash.com/napi/collections/1401382/photos?page=1&per_page=10&order_by=latest&share_key=637bb90e21f7749ae81918efed8c88e1

请求地址：https://unsplash.com/napi/collections/${分类ID}/photos	(此处的分类ID是上一个接口的响应数据中的id字段)

请求方式：GET

请求参数：

|  参数名   |  类型  |      描述      |
| :-------: | :----: | :------------: |
|   page    |  Int   |     第几页     |
| per_page  |  Int   | 一页多少条数据 |
| Share_key | String |   开发者key    |

<!--当前key是官方的，可通过一些方式定时获取官方的key；获取申请官方的key即可，有次数限制。-->



## 苹果序列号

根据序列号查询Iphone设备的信息，暂时可以使用的方式都是返回HTML，暂未找到JSON/XML的格式请求地址，后续会不断更新。

#### 方式一

请求地址：http://www.guofenchaxun.com/result/okyanzhengsns.php

请求方式：POST

请求参数：

| 参数名 |  类型  |  描述  |
| :----: | :----: | :----: |
| postsn | String | 序列号 |

> 响应的内容是HTML网页内容，需要从中取出需要的信息；



#### 方式二

请求地址：http://www.apple110.com/

请求方式：POST

请求头参数：

| 参数名  |  类型  |               描述               |
| :-----: | :----: | :------------------------------: |
| Referer | String | 固定值： http://www.apple110.com |

请求参数：

| 参数名 |  类型  |  描述  |
| :----: | :----: | :----: |
|   sn   | String | 序列号 |

> 响应的内容是HTML网页内容，需要从中取出需要的信息；

响应内容：

```html
<table class="clear">
    <caption style="font-size:18px; margin-bottom: 10px;">苹果序列号 
        <span style="color:#40a329">XXXX</span> 查询结果：
    </caption>
    <tbody>
        <tr>
            <th>序列号</th>
            <td>XXXX</td>
        </tr>
        <tr>
            <th>手机型号</th>
            <td>iPhone 6s</td>
        </tr>
        <tr>
            <th>手机大小</th>
            <td>64GB</td>
        </tr>
        <tr>
            <th>手机颜色</th>
            <td>玫瑰金色</td>
        </tr>
        <tr>
            <th>手机版本</th>
            <td>A1688</td>
        </tr>
        <tr>
            <th>手机模型</th>
            <td>MKT82CH/A</td>
        </tr>
        <tr>
            <th>手机网络</th>
            <td>GSM/CDMA/LTE</td>
        </tr>
        <tr>
            <th>手机产地</th>
            <td>中国（郑州）</td>
        </tr>
        <tr>
            <th colspan="2">出厂日期以及激活日期，请扫描下面二维码查询！</th>
        </tr>
    </tbody>
</table>
```

## 北京交警App

研究此App是为了开发一款进京证可以办理的一个提醒小程序，其他接口大家可自行去抓包研究。

### 验证码

请求地址：https://api.accidentx.zhongchebaolian.com/mobile/mobile/global/verification

请求方式：POST

请求参数：

|  参数  |  类型  |       描述       |
| :----: | :----: | :--------------: |
| phone  | String |      手机号      |
| regist | String | 是否是注册(0或1) |

响应参数：

```json
{
    "verification": "",
    "rescode": "200",
    "resdes": "短信发送成功",
    "ssidcode": null
}
```

### 登录

请求地址：https://api.accidentx.zhongchebaolian.com/mobile/mobile/global/login

请求方式：POST

请求参数：

|    参数    |  类型  |             描述              |
| :--------: | :----: | :---------------------------: |
|   phone    | String |            手机号             |
|   source   | String |               0               |
|  deviceid  | String |            设备码             |
| devicetype | String |          设备类型(0)          |
|  citycode  | String |      城市编码(北京1101)       |
|  valicode  | String |            验证码             |
|  vertype   | String |     验证类型(注册1登录0)      |
|    lon     | String |             位置              |
|   token    | String | 可用这个(1517bfd3f7f8bc4f551) |
|    lat     | String |             位置              |

响应参数：

```json
{
    "citycode": "",
    "userid": "9839BExx445248DE20Axxx2763DFB1",
    "provincecode": null,
    "userType": "1",
    "accesstoken": null,
    "policeno": "",
    "provincetiny": null,
    "ssid": "HWSXZ87384833338772825500",
    "rescode": "200",
    "resdes": "登陆成功",
    "ssidcode": null
}
```

### 天气&限号

请求地址：https://api.accidentx.zhongchebaolian.com/mobile/mobile/global/weather

请求方式：POST

Header:  Accept:application/json, text/javascript, */*; q=0.01

请求参数：

|   参数   |  类型  |        描述        |
| :------: | :----: | :----------------: |
| location | String | 城市编号(北京1101) |

响应参数：

```json
{
    "cityname": "北京市",
    "date": "08月19日",
    "week": "周日",
    "daypicurl": "http://api.map.baidu.com/images/weather/day/zhongyu.png",
    "nightpicurl": "http://api.map.baidu.com/images/weather/night/xiaoyu.png",
    "weathersection": "25 ~ 22℃",
    "weatherdes": "中雨转小雨",
    "washcar": "不宜",
    "dayornight": "1",
    "weathercode": "8",
    "instructionsurl": "http://staticx.zhongchebaolian.com:80/photobase/photos/notice/instructions.html",
    "graphicaldutyurl": "http://staticx.zhongchebaolian.com:80/photobase/photos/notice/graphicalduty.html",
    "rescode": "200",
    "resdes": "获取天气信息成功"
}
```

### 是否可办理进京证

请求地址：https://enterbj.zhongchebaolian.com/enterbj/platform/enterbj/curtime_03

请求方式：POST

判断条件：当返回的内容长度为0时，服务可用；当内容长度大于0，服务不可用(我是反编译看官方代码看到的判断条件)