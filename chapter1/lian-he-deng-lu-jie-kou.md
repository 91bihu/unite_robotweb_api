### **联合登录接口** {#联合登录接口}

**壁虎**提供一个**联合登录接口**

```
接 口 名：http://bao.91bihu.com/unite/login
测试地址：http://lzl.91bihu.com/unite/login
请求方式：HTTP POST 
请求参数：{ agentId:0,userName:"",timestamp:1489044754,timeout:5000,secCode:""}
```

#### 请求参数详解

| 参数名 | 描述 | 描述 |
| :--- | :--- | :--- |
| agentId | 经纪人ID | 从壁虎平台获取的经纪人ID |
| userName | 用户名 | 合作方内部系统登录的用户名 |
| timestamp | 时间戳 | 请求接口当前时间的时间戳\(**unix时间戳**\) |
| timeout | 会话过期时间 | 合作伙伴平台会话过期时间\(单位**秒**\) |
| secCode | 加密串 | `secCode=MD5(agentId=经纪人ID&userName=用户名&secretKey=密钥&timestamp=时间戳&timeout=过期时间)`其中**secretKey**商务合作后会提供 |

**接口返回数据**：

返回 JSON 格式数据

```js
{“code”：200，“msg”:"成功","Token":"xxxx"}
```

参数说明

| 参数名 | 描述 |
| :--- | :--- |
| code | 返回的状态码 |
| msg | 状态码对应的消息 |
| Token | 登录成功后返回，需在请求页面路径中加上`Token`，作为访问壁虎页面的令牌 |

根据`HTTP状态码`判断登录是否成功

| HTTP状态码 | 描述 |
| :--- | :--- |
| 200 | 成功 |
| 416 | 失败 |
| 403 | 未授权,服务器拒绝请求 |
| 406 | 验证不通过 |
| 500 | 请求接口内部错误 |



