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
| CarVin | 车架号 | 行驶证对应的**车辆识别代码** |
| EngineNo | 发动机号 | 行驶证所对应的发动机号码 |
| CityCode | 投保城市ID | 壁虎开通城市ID（参看附录**投保城市**） |
| AgentId | 代理人id | 壁虎提供的顶级代理人ID |
| Token | 登录时返回的token值 | 登录时返回的token值 |
| timestamp | 时间戳 | 请求接口当前时间的时间戳\(**unix时间戳**\) |
| SecCode | 加密串 | SecCode=\(LicenseNo+CityCode+AgentId+Token+TimeStamp+**SecretKey**\)按照首字母升序排列后进行MD5并且编码格式为UTF-8 |





