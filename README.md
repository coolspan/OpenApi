# OpenApi
Provide a variety of crack/free API interface(提供各种破解/免费的Api接口)



## 壁纸Api

网站：https://unsplash.com/

开放接口：https://unsplash.com/api-terms (以下提供的非此处的接口，通过其他方式获取到的)

该网站提供各种类型的高清图片，可以作为壁纸使用；当然也可以利用此资源自己开发App发布到线上，收费可以下载壁纸各种玩法。

#### 分类接口

首页上有一个collectionsTab，里面有不同的分类，先提供出获取当前页分类的接口，如下：

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

#### 分类下图片

Api接口：https://unsplash.com/napi/collections/1401382/photos?page=1&per_page=10&order_by=latest&share_key=637bb90e21f7749ae81918efed8c88e1

请求地址：https://unsplash.com/napi/collections/${分类ID}/photos	(此处的分类ID是上一个接口的响应数据中的id字段)

请求方式：GET

请求参数：

|  参数名   |  类型  |      描述      |
| :-------: | :----: | :------------: |
|   page    |  Int   |     第几页     |
| per_page  |  Int   | 一页多少条数据 |
| Share_key | String |   开发者key    |

注：当前key是官方的，可通过一些方式定时获取官方的key；获取申请官方的key即可，有次数限制。