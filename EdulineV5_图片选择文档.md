# 图片选择文档

图片选择以及图片展示(包括选择图片后的预览)由`TZImagePickerController`、`UIImagePickerController`、`ScanPhotoViewController`三个类共同完成

* 首先在使用图片选择功能时,我们使用`UIAlertController`来展示选择图片弹框效果,然后创建`UIAlertAction`,并通过`addAction`方法来添加`Action`到`Controller`里面,同时也可以通过修改`Action`的`@"_titleTextColor"`属性来改变按钮文字颜色
* 本地相册选取图片由`TZImagePickerController`(pod管理版本)来完成,需要设置最多选择多少张图片

```
TZImagePickerController *imagePickerVc = [[TZImagePickerController alloc] initWithMaxImagesCount:PostImageMaxCount - _pictureArray.count delegate:self];
```
* 相机拍照获取图片由系统原生`UIImagePickerController`来实现
    * 首选需要获取相机权限是否开启

    ```
    [UIImagePickerController isSourceTypeAvailable:UIImagePickerControllerSourceTypeCamera];
    ```
    * 这里需要友情提示一下,模态弹起需要设置成`UIModalPresentationFullScreen`,这样才好
    * 关于图片预览效果由ScanPhotoViewController来实现可设置能否删除

    ```
    ScanPhotoViewController *scanVC = [[ScanPhotoViewController alloc]init];
    scanVC.imgArr = 预览前的图片数组;
    scanVC.index = 当前点击预览的图片的下标;
    scanVC.delegate = self;(指定代理)
    scanVC.modalPresentationStyle = UIModalPresentationFullScreen;
    [self presentViewController:scanVC animated:YES completion:^{
    }];
      
    ```


### 值得一提的是在网络图片预览的时候用的是`TZImagePickerController`来实现的,并且可以保存网络预览图片到本地(后续更新细说).
