#  iOS端项目应用配置

### 1、服务器域名配置
* 项目域名修改在两个文件中: `Api_Config.h`文件里面`HeaderUrl_V5`和`Net_API.m`文件里面`HeaderUrl_V5_Api`,后续会优化更新完善

### 2、第三方账号信息配置
* QQ、微信、微博配置,需要修改两处地方需要配置两个地方: 第一个 位于文件夹 `V5_Constant.h`对应的三方key; 第二个 需要配置`info.plist` 中的 `URL Types`,如图(等仓库建好 相关图片上传后再附上图片链接)

* 网易一键登录 配置在文件夹 `V5_Constant.h`对应的三方key

### 3、直播相关配置
* 直播配置相对复杂后续完善更新

### 4、图片素材管理
本工程所有图片素材记录在~/Assets.xcassets/内.将新的图片生成旧图片一样的规格一致的文件名称后,将新图片覆盖对应文件夹内的图片即可.

* 授权项目简单素材替换
  * AppIcon(应用图标)
  * 图片正在加载中的时候的站位图`defaultImage`
  * 底部导航`icon`位于`tabbarIcon`图片文件夹内
  * 引导图`guide`类图片有多少张引导图就用 `guide1` `guide2`类推,并在`AppDelegate.m`中`didFinishLaunchingWithOptions`启动方法中修改即可
  * 启动图替换 `LaunchScreen.storyboard`中添加启动图 `750*1334`格式png的启动图

* 添加图片的一些说明(规则)
 * iOS本地图标和图片都使用png格式的;
 * 本地图标和图片都需要2倍图和3倍图(最好是1倍图2倍图3倍图都有)
 * 图片命名问题 最好是`板块儿_功能_icon`这样命名 譬如:`audio_pause_icon`
 * 三方工具里面的图标和图片需要在对应的文件中去修改
