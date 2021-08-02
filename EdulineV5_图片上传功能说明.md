# 图片上传功能说明

### `后台接口只支持单张图片上传`

* 在`讲师认证`、`机构认证`、`个人信息修改`功能点里面,都是只有单张图片上传,在这里说明下单张图片上传的时候,首先需要请求接口校验这张图片是否已经存在于后台,然后再上传图片.

```
验证图片是否存在接口
+ (NSString *)verifyImageExit {
    return [Net_Path fullPath:@"upload/fast" repalce:@"" byReplece:@""];
}
```

```
上传图片接口
+ (NSString *)uploadImageField {
    return [Net_Path fullPath:@"upload/putFile" repalce:@"" byReplece:@""];
}
```

* 那如果需要上传多张图片的时候,如何处理呢?譬如:`发布动态`,`评论动态`等功能.这时候就需要创建队列来处理!

    * 首先创建队列 在队列里面执行`for`循环

    ```
    dispatch_queue_t queue = dispatch_queue_create("uploadcircleimage", DISPATCH_QUEUE_CONCURRENT);
    
    ```
    * 在`for`循环里面每一次将所需要上传的图片用`UploadImageModel`模型来组装好,记录每一个`model`里面的`imageArray`(这个数组里面其实装的是一个图片)和`imageIndex`下标

    ```
    UploadImageModel *model = [UploadImageModel new];
    model.imageId = @"";
    model.imageArray = [NSMutableArray new];
    [model.imageArray addObject:weakself.pictureArray[i]];
    model.imageIndex = [NSString stringWithFormat:@"%@",@(i+1)];
    [weakself.pictureIdsArray addObject:model];
    
    ```
    * 然后紧接着执行上传图片的接口请求,把图片信息转成`NSData `,如果图片过大,则需要裁剪.

    ```
    NSData *dataImg=UIImageJPEGRepresentation(model.imageArray[i], 0.5);
    [formData appendPartWithFileData:dataImg name:@"file" fileName:[NSString stringWithFormat:@"image%d.jpg",i] mimeType:@"image/jpg"];
    ```
    * 在上传图片接口请求成功的情况下将后台返回的图片`ID`赋值给之前的`model`

    ```
    model.imageId = [NSString stringWithFormat:@"%@",[[responseObject objectForKey:@"data"] objectForKey:@"id"]];
    ```
    * 当所有图片都执行了上传接口后,返回到`主线程`,最后再循环检索装有`UploadImageModel`的数组,如果某个`model`里面的`imageId`为空,那么对应的下标的第几张图就上传失败,并做出相应提示.

    ```
    if (finishNum == weakself.pictureArray.count) {
    dispatch_async(dispatch_get_main_queue(), ^{
        _rightButton.enabled = YES;
        NSString *faildIndex = @"";
        for (int k = 0; k<weakself.pictureIdsArray.count; k++) {
            UploadImageModel *modelpass = weakself.pictureIdsArray[k];
            if (!SWNOTEmptyStr(modelpass.imageId)) {
                if (!SWNOTEmptyStr(faildIndex)) {
                    faildIndex = [NSString stringWithFormat:@"%@",modelpass.imageIndex];
                } else {
                    faildIndex = [NSString stringWithFormat:@"%@、%@",faildIndex,modelpass.imageIndex];
                }
            }
        }
        [weakself hideHud];
                        
        if (SWNOTEmptyStr(faildIndex)) {
        [weakself showHudInView:weakself.view showHint:[NSString stringWithFormat:@"上传第 %@ 图片超时,请重试",faildIndex]];
        } else {
            [weakself postCircle];
        }
        });
    }
    ```
#### 至此,图片在上传过程中的相关逻辑和注意事项就完事了,在配合实际代码参详.
