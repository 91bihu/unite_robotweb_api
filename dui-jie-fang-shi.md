## 对接方式

合作伙伴登录内部系统成功后，调用**壁虎提供的联合登录接口**,获取到`token`加在内嵌`url`后面访问即可。

示例：

```
//登录成功返回内容 {code:200,msg:"登录成功",token:"hfdjhjdhjfjdhfjdhdhjfjh"}
页面 Url：lzl.91bihu.com/DoQuote/index
调整为:lzl.91bihu.com/DoQuote/index?token=hfdjhjdhjfjdhfjdhdhjfjh
```

### 对接页面 {#对接模块}

| 名称 | url | 描述 |
| :--- | :--- | :--- |
| 报价页面 | /DoQuote/Index | 联合登录后，加上token,既可以输入车牌报价 |
| 选择险种页面 | /DoQuote/SelectInsuranceNew | 联合登录成功后，携带车辆信息调续保接口，得到续保信息后，直接跳转到此页面 |
| 列表页面 | /Customer/CheckLis | 客户列表页面 |



