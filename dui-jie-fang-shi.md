## 对接方式

合作伙伴登录内部系统成功后，调用**壁虎提供的联合登录接口**,获取到`token`加在内嵌`url`后面访问即可。

示例：

```
//登录成功返回内容 {code:200,msg:"登录成功",token:"hfdjhjdhjfjdhfjdhdhjfjh"}
页面 Url：lzl.91bihu.com/DoQuote/index
调整为:lzl.91bihu.com/DoQuote/index?token=hfdjhjdhjfjdhfjdhdhjfjh
```

##  



