### **联合退出接口**

```
接 口 名：http://bao.91bihu.com/unite/SignOut
测试地址：http://lzl.91bihu.com/unite/SignOut
请求方式：HTTP GET 
请求参数：{agentId:0, token:'',secCode}
```

#### 请求参数详解

| **参数名** | **描述** | **备注** |
| :--- | :--- | :--- |
| agentId | 经纪人ID | 从壁虎平台获取的经纪人ID |
| token | token | 登录成功返回的 |
| secCode | 加密串 | `secCode=MD5(agentId=经纪人ID&secretKey=密钥&token=token)`其中secretKey，商务合作后会提供 |

#### 接口返回数据：

返回 JSON 格式数据

```js
{“code”：200，“msg”:"成功"}
```

参数说明

| 参数名 | 描述 |
| :--- | :--- |
| code | 返回的状态码 |
| msg | 状态码对应的message |

根据`HTTP状态码`判断退出是否成功

| HTTP状态码 | 描述 |
| :--- | :--- |
| 200 | 成功 |
| 403 | 未授权,服务器拒绝请求 |
| 406 | 验证不通过 |
| 500 | 请求接口内部错误 |



