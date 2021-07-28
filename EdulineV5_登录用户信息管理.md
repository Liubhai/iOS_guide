# 登录用户信息管理

### 项目用`V5_UserModel`来管理存储当前登录用户的相关信息

* 用户登录`login`(`账号密码登录`、`手机号验证码登录`、`一键登录`、`三方授权登录`)、用户注册`register `,在操作成功后都需要对这个`model`里面的信息进行更新修改.

* 用户信息页面修改用户信息成功后也需要对这个`model`进行修改更新

* 在`我`的页面每次`viewWillAppear`的时候执行更新用户信息,以保证用户信息的正确性

### 用户信息包含基本内容

```
用户UID
[V5_UserModel saveUid:[NSString stringWithFormat:@"%@",[[[responseObject objectForKey:@"data"] objectForKey:@"user"] objectForKey:@"id"]]];
用户账号
[V5_UserModel saveUname:[NSString stringWithFormat:@"%@",[[[responseObject objectForKey:@"data"] objectForKey:@"user"] objectForKey:@"nick_name"]]];
用户昵称
[V5_UserModel saveNickName:[NSString stringWithFormat:@"%@",[[[responseObject objectForKey:@"data"] objectForKey:@"user"] objectForKey:@"user_name"]]];
用户手机
[V5_UserModel savePhone:[NSString stringWithFormat:@"%@",[[[responseObject objectForKey:@"data"] objectForKey:@"user"] objectForKey:@"phone"]]];
用户性别
[V5_UserModel saveGender:[NSString stringWithFormat:@"%@",[[[responseObject objectForKey:@"data"] objectForKey:@"user"] objectForKey:@"gender"]]];
用户头像
[V5_UserModel saveAvatar:[NSString stringWithFormat:@"%@",[[[responseObject objectForKey:@"data"] objectForKey:@"user"] objectForKey:@"avatar_url"]]];
用户VIP状态
[V5_UserModel saveVipStatus:[NSString stringWithFormat:@"%@",[[[responseObject objectForKey:@"data"] objectForKey:@"user"] objectForKey:@"vip_status"]]];
用户签名
[V5_UserModel saveIntro:[NSString stringWithFormat:@"%@",[[[responseObject objectForKey:@"data"] objectForKey:@"user"] objectForKey:@"signature"]]];
用户是否需要设置登录密码
[V5_UserModel saveNeed_set_password:[[NSString stringWithFormat:@"%@",[[[responseObject objectForKey:@"data"] objectForKey:@"user"] objectForKey:@"need_set_password"]] boolValue]];
用户是否需要设置支付密码
[V5_UserModel saveNeed_set_paypwd:[[NSString stringWithFormat:@"%@",[[[responseObject objectForKey:@"data"] objectForKey:@"user"] objectForKey:@"need_set_paypwd"]] boolValue]];


```

### 用户退出登录的时候需要执行如下代码将`model`里面的数据重置

```
[V5_UserModel deleteUserPassport];

```
