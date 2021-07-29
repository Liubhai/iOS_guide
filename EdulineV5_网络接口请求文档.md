# 网络接口请求文档

项目的网络请求基于`AFNetworking3.2.1`版本,用`pod`管理

* 使用`AFHTTPSessionManager`来管理网络请求

    * 根据`GET`、`POST`(含文件上传)、`PUT`、`DELETE`需求,有5个方式可供调用

    ```
    
 GET
+ (void)requestGETSuperAPIWithURLStr:(NSString *)urlStr
                   WithAuthorization:(NSString *)authorization
                            paramDic:(NSDictionary *)paramDic
                              finish:(void(^)(id responseObject))finish
                             enError:(void(^)(NSError *error))enError;
POST
+ (void)requestPOSTWithURLStr:(NSString *)urlStr
            WithAuthorization:(NSString *)authorization
                     paramDic:(NSDictionary *)paramDic
                       finish:(void(^)(id responseObject))finish
                      enError:(void(^)(NSError *error))enError;
POST File
+ (NSURLSessionDataTask * _Nonnull)POST:(NSString * _Nonnull)URLString
               parameters:(id _Nonnull)parameters
constructingBodyWithBlock:(void (^ _Nonnull)(id <AFMultipartFormData> _Nonnull formData))block
                 progress:(nullable void (^)(NSProgress * _Nonnull uploadProgress))uploadProgressBlock
                  success:(void (^ _Nonnull)(NSURLSessionDataTask * _Nonnull task, id _Nonnull responseObject))success
                  failure:(void (^ _Nonnull)(NSURLSessionDataTask * _Nonnull task, NSError * _Nonnull error))failure;
PUT
+ (void)requestPUTWithURLStr:(NSString *)urlStr
                    paramDic:(NSDictionary *)paramDic
                     Api_key:(NSString *)api_key
                      finish:(void(^)(id responseObject))finish
                     enError:(void(^)(NSError *error))enError;
DELETE
+ (void)requestDeleteWithURLStr:(NSString *)urlStr
                       paramDic:(NSDictionary *)paramDic
                        Api_key:(NSString *)api_key
                         finish:(void(^)(id responseObject))finish
                        enError:(void(^)(NSError *error))enError;
    ```

    *重点来了,根据需要,各类参数需要加密并且传给`HTTPRequestHeaders`里面,譬如`E-USER-AK``E-USER-SK`等等固定参数,其含义参考后台接口文档,加密规则见代码详情`Net_API.m`文件.

    * 关于接口正常参数(除去网络请求头里面的固定参数以外)也需要加密

    ```
    + (NSString *)sortedDictionary:(NSDictionary *)dict;
    ```
    * 固定参数里面涉及到单机构多机构切换、分享口令、用户层级(上线下线)等问题,应多根据后台文档来理解
