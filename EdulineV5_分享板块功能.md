# 分享功能介绍

首先将需要的三方信息配置好在[iOS端项目应用配置](https://github.com/Liubhai/iOS_guide/blob/develop/EdulineV5_%E9%A1%B9%E7%9B%AE%E5%BA%94%E7%94%A8%E9%85%8D%E7%BD%AE.md)文件中按照要求分别配置好

### 分享海报功能
* 运用友盟原生分享,需要在执行分享弹框操作的页面执行如下代码,让友盟的分享弹框加载在当前页面上

```

- (UIView*)UMSocialParentView:(UIView*)defaultSuperView{
    return self.view;
}

```

* 友盟分享 
    * 截图当前分享的信息到本地,然后调起友盟分享,如图
    
    ```
    [UMSocialUIManager setShareMenuViewDelegate:self];
    [UMSocialUIManager setPreDefinePlatforms:@[@(UMSocialPlatformType_WechatSession),@(UMSocialPlatformType_WechatTimeLine),@(UMSocialPlatformType_QQ)]];
    // 显示分享面板
    [UMSocialUIManager showShareMenuViewInWindowWithPlatformSelectionBlock:^(UMSocialPlatformType platformType, NSDictionary *userInfo) {
        // 根据获取的platformType确定所选平台进行下一步操作
        // 创建分享消息对象
        UMSocialMessageObject *messageObject = [UMSocialMessageObject messageObject];
        
        UMShareImageObject *shareObject = [UMShareImageObject shareObjectWithTitle:nil descr:nil thumImage:image];
        // 设置网页地址
        shareObject.shareImage = image;
        // 分享消息对象设置分享内容对象
        messageObject.shareObject = shareObject;
        // 调用分享接口
        [[UMSocialManager defaultManager] shareToPlatform:platformType messageObject:messageObject currentViewController:self completion:^(id data, NSError *error) {
            if (error) {
                UMSocialLogInfo(@"************Share fail with error %@*********",error);
            }else{
                if ([data isKindOfClass:[UMSocialShareResponse class]]) {
                    UMSocialShareResponse *resp = data;
                    // 分享结果消息
                    UMSocialLogInfo(@"response message is %@",resp.message);
                    // 第三方原始返回的数据
                    UMSocialLogInfo(@"response originalResponse data is %@",resp.originalResponse);
                }else{
                    UMSocialLogInfo(@"response data is %@",data);
                }
            }
        }];
    }];
    
    ```

### 复制链接
* 分享链接就是复制一个后台接口返回一个用于分享的相关链接,用于直接粘贴给好友

### 复制口令
* 复制口令类似于淘宝口令,`EdulineV5`基于一种独有的组装规则将`目标ID`(课程、资讯以及活动等)与特殊文字组合起来,再根据一定`规则加密`生成一串口令,口令可以直接粘贴给好友,好友拿到这串口令打开我们app,即可跳转到目标ID对应的页面.

### **注:**`分享这块儿功能涉及到分销,分成和推广收益等,所以作为一个独特的板块儿来生成一份文档. `
