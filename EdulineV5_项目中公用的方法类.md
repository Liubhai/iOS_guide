# 项目中公用的方法类

### 项目中一些常用的公用方法都存放在`EdulineV5_Tool`文件里面

*    关于label简单的高度、宽度的获取方法

```
// 字符串 高度
+ (float) heightForString:(NSString *)value fontSize:(UIFont*)font andWidth:(float)width;

// 字符串 宽度
+ (float) widthForString:(NSString *)value fontSize:(UIFont*)font andHeight:(float)height;
```

* 基于时间戳转换成各种格式的时间字符串,譬如

```
//普通格式
+ (NSString *)formateTime:(NSString *)time;
// @"yyyy-MM-dd HH:mm"格式
+ (NSString *)formateYYYYMMDDHHMMTime:(NSString *)time;


```

* 获取一个随机字符串


```
+ (NSString *)getRandomString;
```

* 一些加密方法

```
+ (NSString *)sortedDictionary:(NSDictionary *)dict;

+ (NSString *)getImageFieldMD5:(NSData *)imageData;

+ (NSString *)getmd5WithString:(NSString *)string;
```

* 重点是针对按钮图文排列的问题,如果一个按钮要求有`icon`和文字,那么就需要调整`icon`和文字的样式,譬如 `图片在左文字在右` `图片在右文字在左` 等等

```
+ (void)dealButtonImageAndTitleUI:(UIButton *)sender;
```

* 处理一些因为网络接口数据解析数字字符的时候精度丢失的问题,譬如后台返回数据是99.98,但是解析后数据变成99.99999999等情况,那么就需要用如下方法处理后台返回的数字字符串校正.

```
+ (NSString *)reviseString: (NSString *)str;
```

***注:建议后续开发人员把常用、可复用和公用的方法都加在这个文件里面,便于修改适配和查找.***
