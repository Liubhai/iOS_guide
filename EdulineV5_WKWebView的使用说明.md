# WKWebView的使用说明

### 项目中一切网页都用`WKWebView`来实现,包括`课程详情页`、`讲师主页`,`机构主页`的简介以及`资讯详情页`,还有`内部链接跳转`.

* `WKWebIntroview`公用基础`WKWebView`,在其初始化方法中已经配置好相关的属性`WKWebViewConfiguration`和`WKUserScript`,在使用过程中直接引用初始化即可

```
[[WKWebIntroview alloc] initWithFrame:self.playerView.frame];
```

* `WkWebViewController`是公用的基础控制器,用来直接单独作为一个显示`WKWebView `的控制器,同样也是直接引用并初始化即可

### 在课程板块儿有涉及到电子书,图文等类型的课时阅读观看,其内容加载也是使用`WKWebIntroview`来实现,由于苹果审核规则中明确要求将以前的WebView用`WKWebView`来替换,那就只能将项目中所有(包括三方工具、相关SDK)修改或者更新到新版本

* 公用的很多类就是为了适配项目功能而定制复用,如果二开有其他需要,可自行修改.


### 针对`WKWebView`的加载特性,需要在其加载完成的代理方法中处理其高度问题

```
-(void)webView:(WKWebView *)webView didFinishNavigation:(WKNavigation *)navigation;
```

* 在`finish`代理方法中注入`evaluateJavaScript`来控制渲染效果,并根据`@"document.body.offsetHeight;"`来获取高度.

```
- (void)evaluateJavaScript:(NSString *)javaScriptString completionHandler:(void (^ _Nullable)(_Nullable id, NSError * _Nullable error))completionHandler;
```

***注:*** 值得一提的是,有些h5页面加载会引发状态栏消失的问题,只需要在页面返回的时候强制让状态栏恢复显示就行,别慌,小问题.
