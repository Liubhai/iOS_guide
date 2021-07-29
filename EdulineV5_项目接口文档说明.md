# 项目接口文档说明

整个项目的接口都存放在`Net_Path`文件里面,并根据不同板块儿来排列.主要介绍文件里面的两个接口组装方法

*    首先是普通的一个或者不需要替换接口里面某个关键字的情况, `replace`是需要倍替换的关键字, `byReplace`是用来替换的具体参数值.譬如`course/base/{id}`,那么`{id}`就是需要用一个具体的值来整体替换.替换后的结果就是`course/base/一个具体的值`

```
+ (NSString *)fullPath:(NSString *)path repalce:(NSString *)replace byReplece:(NSString *)byReplace;
```
* 其次就是接口里面需要用多个具体的值去替换多个关键字的情况,按照两个数组里面的信息依次去替换就OK

```
+ (NSString *)fullPath:(NSString *)path repalceArray:(NSArray *)replace byRepleceArray:(NSArray *)byReplace;

+ (NSString *)fullPath:(NSString *)path repalceArray:(NSArray *)replace byRepleceArray:(NSArray *)byReplace {
    if (replace.count == byReplace.count) {
        for (int i = 0; i<replace.count; i++) {
            path = [[NSString stringWithFormat:@"%@",path] stringByReplacingOccurrencesOfString:replace[i] withString:byReplace[i]];
        }
    }
    return path;
}
```
#### 这样处理接口,为了能够方便使用和修改
