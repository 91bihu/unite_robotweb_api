# 续保接口

**接  口 名**：unite/unitecheckrenewal

**请求方式**：HTTP POST

**Content-Type**：application/json

**CharSet**：UTF-8

**请求参数**：

```
 车架号、发动机号续保 
 {"CarVin":"LS4ASE2A2GJ137027","EngineNo":"2192209","CityCode":"1",
 "AgentId":"102","Token":"4773EEC3EE9B572851C11DF730DCE827","TimeStamp":11111111,
 "secCode":"8ebe5e43bd5f305acaae4442dcfaee50"}

 车牌号续保
 {"LicenseNo":"京J97896","CityCode":"1","AgentId":"102",
 "Token":"4773EEC3EE9B572851C11DF730DCE827","TimeStamp":11111111,"secCode":"98057c3f1cc947b63bf4bf503d226936"}
```

#####  {#请求参数详解}

##### 请求参数详解 {#请求参数详解}

| **参数名** | **描述** | **备注** |
| :--- | :--- | :--- |
| LicenseNo | 车牌号 | 目前壁虎仅支持6位轿车车牌\(不包括8位新能源车\) |
| CarVin | 车架号 | 行驶证对应的**车辆识别代码，在没有车牌号的清下必填** |
| EngineNo | 发动机号 | 行驶证所对应的发动机号码，**在没有车牌号的情况下必填** |
| CityCode | 投保城市ID | 壁虎开通城市ID（参看附录**投保城市**） |
| AgentId | 代理人id | 壁虎提供的顶级代理人ID |
| Token | 登录时返回的token值 | 登录时返回的token值 |
| timestamp | 时间戳 | 请求接口当前时间的时间戳\(**unix时间戳**\) |
| SecCode | 加密串 | SecCode=\(LicenseNo+CityCode+AgentId+Token+TimeStamp+**secretKey**\)按照首字母升序排列后进行MD5并且编码格式为UTF-8 |

##### SecCode生成排序实例 {#seccode生成排序实例}

```
AgentId=11111&Carvin=xxxxxxxxxxxxxxxxxxxxxxxx&CityCode=17&EnginNo=xxxxxxxx&SecretKey=xxxxx&timestamp=1234567
&token=xxxxxxxxxxxxxxxx
```

> 本示例为使用**车架号**和**发动号**续保**   **

##### 备注说明： {#接口返回数据：}

* **SecCode 按照**示例所有的参数升序排列，拼接为一个字符串，再用 **MD5 **加密，特别注意 **secretKey **参与加密，但不参与参数传递。

* **secretKey **获取方式参照「壁虎授权」,**secretKey **参与加密，请注意大小写。

* 如果用车牌号续保，车架号和发动号可以不传。

##### 接口返回数据： {#接口返回数据：}

返回 JSON 格式数据

```
{“code”：200，“msg”:"续保成功","RenewalToken":"xxxx"}
```

**返回数据说明：**

| **字段** | **描述** |
| :--- | :--- |
| code | 返回的状态码\(HTTP状态码\)，根据状态码判断是否成功 |
| msg | 状态码对应的消息 |
| RenewalToken | 续保成功，需在请求页面路径中加上`RenewalToken`，作为访问壁虎页面的令 |

根据`HTTP状态码`判断是否续保成功

| HTTP状态码 | **描述** |
| :--- | :--- |
| 200 | 续保成功 |
| 206 | 续保失败 |
| 403 | 未授权,服务器拒绝请求 |
| 406 | 验证不通过 |
| 412 | 参数校验不通过 |
| 500 | 请求接口内部错误 |

**示例：**

```
http://bao.91bihu.com/DoQuote/SelectInsuranceNew?Token=XXXX&RenewalToken=XXXX
```

**Token:**由联合登录接口返回

