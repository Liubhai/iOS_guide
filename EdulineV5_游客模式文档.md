# 游客模式文档

### 由于苹果审核需要,游客模式属于必备条件
* `游客模式` 用设备`device`的唯一标识符来生成一个新用户,设备唯一标识符 例如：`FBF2306E-A0D8-4F4B-BDED-9333B627D3E6`

```
[[[UIDevice currentDevice] identifierForVendor] UUIDString]
```
* 执行游客注册接口`touristLoginNet`,接口请求成功后,将接口返回的信息按照`V5_UserModel`来储存,具体参照[登录用户信息管理](https://github.com/Liubhai/iOS_guide/blob/develop/EdulineV5_%E7%99%BB%E5%BD%95%E7%94%A8%E6%88%B7%E4%BF%A1%E6%81%AF%E7%AE%A1%E7%90%86.md)

* 由于设备登录,并没有绑定手机号,然后app内很多操作权限都需要绑定手机号的用户才能操作,所以在这些操作执行的时候会提示设备登录的用户去用户个人信息里面去绑定手机号.


***注:如果app内含有其他三方登录方式,那么该考虑苹果登录方式的接入了(后续附上文档)***
