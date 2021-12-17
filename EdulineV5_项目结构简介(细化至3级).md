# 项目文件结构说明

项目结构

```shell
.
├── AnyModel                                    保存和获取当前登录用户的个人信息(包括Token、TokenSecret、昵称、手机号、会员信息,是否认证、设置密码以及支付密码是否设置)
│   ├── V5_UserModel.h
│   └── V5_UserModel.m
├── AppDelegate.h
├── AppDelegate.m                               里面涉及到网易快速本机登录、缓存当前首页数据、获取后台配置信息、初始化信息接口处理
├── Assets.xcassets                             除去三方素材源的图标图片素材以外,项目所有图片图标素材都放在这里,分板块儿分文件夹存放 素材文件夹板块儿名字识别素材属于那个板块儿
│   ├── AppIcon.appiconset                      基本常识 app桌面图标
│   ├── Contents.json
│   ├── ExamPageIcon                            考试板块儿素材
│   ├── FindPage
│   ├── LaunchImage.launchimage                 app启动动画素材
│   ├── LoginAndRegister                        登录和注册板块儿所有素材 
│   ├── MycenterIcon                            个人中心(我的板块儿)素材(包括设置页面板块儿)
│   ├── StudyPageIcon                           学习板块儿素材
│   ├── TeacherPage                             讲师主页板块儿涉及到的素材
│   ├── circleIcon                              圈子板块儿涉及素材
│   ├── courseActivityIcon                      课程详情页有关课程活动涉及到的素材
│   ├── courseIcon                              课程整个板块儿涉及到的素材都在这里(包括课程主页、课程详情页、播放页等)
│   ├── defaultImage.imageset                   默认图(展位图、缺省图)
│   ├── guide1.imageset                         app启动动画结束后引导图第一张素材
│   ├── guide2.imageset                         app启动动画结束后引导图第二张素材
│   ├── guide3.imageset                         app启动动画结束后引导图第三张素材(如果有第四张第五张引导图,请按照同样命名格式处理然后在appdelegate里面启动app方法里面添加)
│   ├── homepage                                首页板块儿涉及到的素材存放       
│   ├── lauch375.imageset                       启动图
│   ├── lauchIphoneX.imageset                   启动图适配iPhoneX
│   ├── liveIcon                                课程涉及到直播相关的本工程项目的图片(三方的素材不归这个文件归纳,找对应三方技术支持)
│   ├── menberIcon                              会员板块儿涉及到素材
│   ├── newScoreIcon                            个人中心进入积分页面的素材
│   ├── order                                   所有订单页面的素材
│   ├── placeholder_logo.imageset               app的logo展位图
│   ├── questionIcon                            问答板块页面素材
│   ├── tabbarIcon                              app主页面底部导航素材
│   └── zixunIcon                               资讯板块素材
├── Base.lproj
│   └── LaunchScreen.storyboard                 xcode拒绝launch素材来设置启动图模式,只能用launchScreen来设置
├── BaseVC
│   ├── BaseViewController.h                    本工程项目所有原生VC的基类,页面顶部标题,左右按钮、分割线都在这里设置
│   ├── BaseViewController.m
│   ├── CommentBaseView.h                       评论功能所需的工具基类(课程评论、圈子评论)
│   ├── CommentBaseView.m
│   ├── CommonPopView.h                         评论功能公共类所需视图,点击评论输入框弹起来的时候显示的视图
│   ├── CommonPopView.m
│   ├── EdlineV5_Color.h                        所有当前项目涉及到的文字、按钮、背景颜色、分割线的颜色设置文件(还有根据后台配置的主题色)
│   ├── EdlineV5_Color.m
│   ├── EmptyCell.h                             用cell来处理tableview列表空数据(只要是tableview空数据需要用cell来显示 则在这里处理默认文字和默认图)
│   ├── EmptyCell.m
│   ├── HorizontalScrollText.h                  公告广告功能滚动控件
│   ├── HorizontalScrollText.m
│   ├── JustCircleProgress.h                    圆圈形进度控件(课程播放页进度控件)
│   ├── JustCircleProgress.m
│   ├── LBHProgressView.h                       课程活动进度控件进度条
│   ├── LBHProgressView.m
│   ├── LBHScrollView.h                         基于ScrollView重写UIGestureRecognizerDelegate手势代理
│   ├── LBHScrollView.m
│   ├── LBHTableView.h                          基于TableView重写UIGestureRecognizerDelegate手势代理
│   ├── LBHTableView.m
│   ├── MoneyPassWordPopView.h                  支付时候密码弹框控件
│   ├── SHPasswordTextView.h                    支付密码输入控件
│   ├── SHPasswordTextView.m
│   ├── StarEvaluator.h                         课程详情页 星级控件
│   ├── StarEvaluator.m
│   ├── UICollectionView+EmptyData.h            瀑布流列表空数据设置模式
│   ├── UICollectionView+EmptyData.m
│   ├── UITableView+EmptyData.h                 tableview空数据设置模式
│   ├── WKWebIntroview.h                        基于WKWebview写的公共视图类
│   ├── WKWebIntroview.m
│   ├── WkWebViewController.h                   基于WKWebview写的公共控制器类
│   └── WkWebViewController.m
├── Course                                      课程详情页
│   ├── CourseCell                      
│   │   ├── CourseCatalogCell.h                 课程详情页目录列表cell,相关控件修改在这里处理
│   │   ├── CourseCatalogCell.m
│   │   ├── CourseCommentCell.h                 课程详情页课程评论列表cell,相关控件修改在这里处理
│   │   ├── CourseCommentCell.m
│   │   ├── CourseRecordCell.h                  课程详情页笔记列表cell,相关控件修改在这里处理
│   │   ├── CourseRecordCell.m
│   │   ├── CourseStudentsCollectionCell.h      课程详情页学生列表瀑布流列表cell,cell上相关控件在这里修改
│   │   ├── CourseStudentsCollectionCell.m
│   │   ├── CourseTestListCell.h                课程详情页考试列表cell,cell视图上控件修改可在这里修改
│   │   ├── CourseTestListCell.m
│   │   ├── KaquanCell.h                        课程卡券列表cell 课程详情页点击显示课程相关卡券
│   │   ├── KaquanCell.m
│   │   ├── NewClassCourseCell.h                班级课课程目录列表cell 班级课里面的目录列表上控件修改可在这里修改
│   │   ├── NewClassCourseCell.m
│   │   ├── ShitikaCell.h                       实体卡列表cell
│   │   ├── ShitikaCell.m
│   │   ├── ShopCarCell.h                       购物车课程列表cell,购物车管理和结算页面列表cell公用
│   │   └── ShopCarCell.m
│   ├── CourseCommentDetailVC.h                 课程评论详情页面,点击课程点评cell 进入到这个页面 点评的评论页面,页面底部是评论入口
│   ├── CourseCommentDetailVC.m
│   ├── CourseCommentListVC.h                   课程点评列表页面,点击评论,查看自己评论、显示全部评论等代理方法都是在这页面
│   ├── CourseCommentListVC.m
│   ├── CourseCommentViewController.h           课程点评输入内容页面(修改点评和点评的评论内容输入页面都是在这个页面)
│   ├── CourseCommentViewController.m
│   ├── CourseDetailPlayVC.h                    课程播放页面(课时播放逻辑,记笔记入口,音视频播放器,直播间进入前代理设置,直播间进入逻辑等都在这个页面)
│   ├── CourseDetailPlayVC.m
│   ├── CourseIntroductionVC.h                  课程简介页面(里面用wkwebview来显示简介)
│   ├── CourseIntroductionVC.m
│   ├── CourseListVC.h                          点播课程和直播课程课时目录页面(点击课时的代理方法都在这里,以及和课程详情页播放页目录点击代理实现)
│   ├── CourseListVC.m
│   ├── CourseMainViewController.h              课程详情页面(课程活动,分享,收藏,购买课程,加入购物车,咨询功能入口都在这个页面实现)
│   ├── CourseMainViewController.m
│   ├── CourseMakeNoteVC.h                      课程播放页面点击底部“记笔记”进入到这个页面,当前课时的记笔记功能在这个页面实现
│   ├── CourseMakeNoteVC.m
│   ├── CourseModel                             课程详情页相关model 
│   │   ├── CouponModel.h                       卡券列表model 将接口数据转化成模型 便于调用
│   │   ├── CouponModel.m
│   │   ├── CourseListModel.h                   课程目录列表model 将目录接口数据转换成model 便于在传值的时候引用
│   │   ├── CourseListModel.m
│   │   ├── ShopCarModel.h                      购物车列表model 将获取当前用户购物车的课程列表数据转还成model 便于在购物车管理结算的时候引用数据
│   │   └── ShopCarModel.m
│   ├── CourseStudentListViewController.h       课程详情页学生列表数据控制器
│   ├── CourseStudentListViewController.m
│   ├── CourseTestListVC.h                      课程详情页和该课程相关的考试列表控制器
│   ├── CourseTestListVC.m
│   ├── GroupDetailViewController.h             课程活动 砍价 拼团 详情页(砍价、发起拼团 参团,发起砍价 等功能在这个页面实现,伴随活动分享功能)
│   ├── GroupDetailViewController.m
│   ├── GroupListPopViewController.h            课程详情页点击拼团 参团按钮弹出的当前接口返回的团购列表控制器
│   ├── GroupListPopViewController.m
│   ├── SharePosterViewController.h             分享课程,课程活动等分享页面(口令分享等功能)
│   ├── SharePosterViewController.m
│   ├── ShitikaViewController.h                 实体卡列表控制器 使用实体卡功能在这个页面处理
│   ├── ShitikaViewController.m
│   ├── ShopCarManagerFinalVC.h                 课程购物车结算页面,使用卡券,积分选择
│   ├── ShopCarManagerFinalVC.m
│   ├── ShopCarManagerVC.h                      课程购物车管理页面 取消加入购物车,删除课程等功能实现
│   ├── ShopCarManagerVC.m
│   ├── TreeTableView
│   │   ├── CourseTreeListViewController.h      班级课树状结构目录控制器,点击课时、课时点击代理方法实现
│   │   ├── CourseTreeListViewController.m
│   │   ├── MYTreeItem.h                        班级课课程目录model,桥接控制器和manager              
│   │   ├── MYTreeItem.m
│   │   ├── MYTreeTableManager.h                班级课目录manager工具类
│   │   └── MYTreeTableManager.m
│   └── courseView
│       ├── CourseActivityView.h                课程详情页活动视图,视图上所有控件需要修改的都在这里
│       ├── CourseActivityView.m
│       ├── CourseCommentTopView.h              课程详情页点评列表顶部星级显示,只显示自己点评和显示所有点评按钮控件视图
│       ├── CourseCommentTopView.m
│       ├── CourseContentView.h                 课程详情页 有关课程信息视图(价格、标题,星级、进度、在学人数等控件,看不懂就点xcode运行时的构架看)
│       ├── CourseContentView.m
│       ├── CourseCouponView.h                  课程详情页 卡券视图(显示当前课程接口返回的卡券信息)
│       ├── CourseCouponView.m
│       ├── CourseDownView.h                    课程详情页和播放页面底部所有控件视图(购买按钮,开始学习按钮,加入购物车按钮等都在这里)
│       ├── CourseDownView.m
│       ├── CourseTeacherAndOrganizationView.h  课程详情页讲师和机构相关信息视图
│       ├── CourseTeacherAndOrganizationView.m
│       ├── GrouListCell.h                      课程详情页参团列表cell
│       ├── GrouListCell.m
│       ├── KanjiaListCell.h                    课程活动--砍价详情页底部已经砍价数据列表cell
│       ├── KanjiaListCell.m
│       ├── playAnimationView.h                 课时正在播放的动画设置
│       └── playAnimationView.m
├── CoursePage                                  课程主页相关页面
│   ├── CourseClassifyVC.h                      课程主页顶部课程分类下拉主页
│   ├── CourseClassifyVC.m
│   ├── CourseScreenVC.h                        课程主页顶部筛选下拉设置主页
│   ├── CourseScreenVC.m
│   ├── CourseSearchHistoryVC.h                 首页顶部搜索栏点击后进入课程历史搜索页面
│   ├── CourseSearchHistoryVC.m
│   ├── CourseSearchListVC.h                    课程主页板块儿页面控制器(展示课程列表)
│   ├── CourseSearchListVC.m
│   ├── CourseSortVC.h                          课程主页顶部排序下拉设置页面
│   ├── CourseSortVC.m
│   ├── CourseTypeVC.h                          课程主页顶部课程类型下拉设置页面(类型由后台接口返回)
│   ├── CourseTypeVC.m
│   └── View
│       ├── CourseCommonCell.h                  课程主页顶部下拉各种列表cell(公用)
│       ├── CourseCommonCell.m
│       ├── SearchHistoryListCell.h             搜索课程历史记录页面记录列表cell
│       └── SearchHistoryListCell.m
├── EdulineToolLib                              手动导入的一些三方工具库
│   ├── Categories
│   │   ├── ScanPhotoViewController.h           图片预览功能控制器
│   │   ├── ScanPhotoViewController.m
│   │   ├── UIView+HUD.h                        基于HUD写的拓展,用于view和VC弹框提示
│   │   ├── UIView+HUD.m
│   │   ├── UIViewController+HUD.h
│   │   └── UIViewController+HUD.m
│   ├── IAP_Tool                                苹果内购文件(一套流程都在这里处理)
│   │   ├── STRIAPManager.h
│   │   └── STRIAPManager.m
│   ├── MBHUD                                   HUD弹框提示三方工具
│   │   ├── MBProgressHUD+Add.h
│   │   └── MBProgressHUD+Add.m
│   ├── SDCycleScrollView                       最基本的东西广告位轮播滚动工具
│   │   ├── PageControl
│   │   ├── SDCollectionViewCell.h
│   │   ├── SDCollectionViewCell.m
│   │   ├── SDCycleScrollView.h
│   │   ├── SDCycleScrollView.m
│   │   ├── UIView+SDExtension.h
│   │   └── UIView+SDExtension.m
│   ├── TYAttributedLabel                       TY富文本三方工具(具体使用,自行百度或者github参考,入门级三方工具)
│   │   ├── NSMutableAttributedString+TY.h
│   │   ├── NSMutableAttributedString+TY.m
│   │   ├── TYAttributedLabel.h
│   │   ├── TYAttributedLabel.m
│   │   ├── TYDrawStorage.h
│   │   ├── TYDrawStorage.m
│   │   ├── TYImageCache.h
│   │   ├── TYImageCache.m
│   │   ├── TYImageStorage.h
│   │   ├── TYImageStorage.m
│   │   ├── TYLinkTextStorage.h
│   │   ├── TYLinkTextStorage.m
│   │   ├── TYTextContainer+Extended.m
│   │   ├── TYTextContainer.h
│   │   ├── TYTextContainer.m
│   │   ├── TYTextStorage.h
│   │   ├── TYTextStorage.m
│   │   ├── TYTextStorageProtocol.h
│   │   ├── TYViewStorage.h
│   │   └── TYViewStorage.m
│   └── libqrencode                          二维码生成工具(不懂的百度,很简单)
│       ├── QRCodeGenerator.h
│       ├── QRCodeGenerator.m
│       ├── bitstream.c
│       ├── bitstream.h
│       ├── mask.c
│       ├── mask.h
│       ├── qrencode.c
│       ├── qrencode.h
│       ├── qrinput.c
│       ├── qrinput.h
│       ├── qrspec.c
│       ├── qrspec.h
│       ├── rscode.c
│       ├── rscode.h
│       ├── split.c
│       └── split.h
├── FindPage                                发现主页各类文件
│   ├── CircleMainPage                      圈子小板块儿页面文件
│   │   ├── CircleDetailCommentCell.h       圈子详情底部评论列表cell(圈子评论视图上的控件修改在这个文件处理)
│   │   ├── CircleDetailCommentCell.m
│   │   ├── CircleDetailViewController.h    圈子详情控制器(显示顶部圈子内容以及底部圈子评论列表两个小板块儿)
│   │   ├── CircleDetailViewController.m
│   │   ├── CircleListCell.h                圈子主页列表cell(各种圈子列表公用cell,cell上的视图都在这里修改)
│   │   ├── CircleListCell.m
│   │   ├── CircleListVC.h                  圈子主页列表控制器(响应cell上的各种代理)
│   │   ├── CircleListVC.m
│   │   ├── CirclePostViewController.h      圈子发布页面(选择图片发布等操作)
│   │   ├── CirclePostViewController.m
│   │   ├── CircleRootViewController.h      圈子小板块儿主页根视图(存放相关的圈子列表控制器)
│   ├── ExamPage                            考试小板块儿主页文件存放
│   │   ├── AnswerSheetViewController.h     考试答题卡页面(显示各个题号,可点击直接跳转到对应题目详情)
│   │   ├── AnswerSheetViewController.m
│   │   ├── ExamDetailViewController.h      知识点练习和专项练习类型的试题详情页(练习、收藏等功能)
│   │   ├── ExamDetailViewController.m
│   │   ├── ExamMainViewController.h        考试板块大型分类主页控制器(知识点、专项、套卷、公开考试,有后台配置)
│   │   ├── ExamMainViewController.m
│   │   ├── ExamPaperDetailViewController.h 公开考试类型的考试详情页(可收藏可进入答题卡,上一题、下一题、交卷功能处理)
│   │   ├── ExamPaperDetailViewController.m
│   │   ├── ExamPaperErrorTestAgainVC.h     错题重练详情页面(具体需求按照产品说的来,练习的时候错的题目)
│   │   ├── ExamPaperErrorTestAgainVC.m
│   │   ├── ExamPointSelectVC.h             知识点选择页面(知识点练习需要先选择知识点类型后再生成相应的试题)
│   │   ├── ExamPointSelectVC.m
│   │   ├── ExamResultDetailViewController.h 考试结果详情页面(里面展示得分,考试解释时间、试题标题等信息,以及页面底部显示的试卷里面题目的正确错误以及未答,底部还可以查看详情等功能处理)
│   │   ├── ExamResultDetailViewController.m
│   │   ├── SpecialProjectExamList.h          专项试题列表控制器(专项分层级、购买、答题功能都在这个页面处理)
│   │   ├── SpecialProjectExamList.m
│   │   ├── TaojuanDetailListViewController.h 套卷详情页(展示套卷和套卷下的试卷,购买和进入答题按钮操作)
│   │   ├── TaojuanDetailListViewController.m 
│   │   ├── TaojuanListViewController.h       套卷列表控制器(购买套卷和开始答题按钮点击功能,点击列表cell进入套卷详情页)
│   │   ├── TaojuanListViewController.m
│   ├── FindRootViewController.h              发现主页板块儿控制器(由后台配置发现主页显示的内容)
│   ├── FindRootViewController.m
│   ├── ZiXunDetailVC.h                       资讯详情页控制器(点击资讯列表cell进入的页面,展示资讯详情和资讯的评论列表,可点赞可评论)
│   ├── ZiXunDetailVC.m
│   ├── ZiXunListVC.h                         资讯列表控制器(展示资讯分类下的资讯列表内容,左上角按钮进入分类选择)
│   ├── ZiXunListVC.m
│   ├── ZixunCommmentDetailVC.h               资讯评论详情页(点击资讯评论cell进入的页面、评论详情页面)
│   └── ZixunCommmentDetailVC.m
├── HomePage                                  app首页文件
│   ├── HomeRootViewController.h              app首页根控制器(显示轮播图,分类,分类课程,后台推荐课程,推荐机构,推荐讲师信息)
│   ├── HomeRootViewController.m
│   ├── IntendedCourseVC.h                     意向课程选择类型页面(如果不清楚什么是意向课程分类就问产品大佬,选择课程意向分类后,需要将对应id传递给返回页面请求接口获取意向课程信息)
│   ├── IntendedCourseVC.m
├── InstitutionsPage                          机构小板儿文件
│   ├── InstitutionCourseMainVC.h             机构主页的课程页面控制器(展示该机构下的机构课程列表,列表里面的相关操作处理和普通课程列表操作一样)
│   ├── InstitutionCourseMainVC.m
│   ├── InstitutionListVC.h                   机构数据列表(右上角按钮可点击显示机构平台分类,点击了分类返回机构数据列表重新请求数据刷新页面)
│   ├── InstitutionListVC.m
│   ├── InstitutionRootVC.h                   机构详情主页(显示机构基本信息、推荐课程,推荐讲师、推荐资讯数据,点击对应信息进入课程、讲师、资讯详情页面)
│   ├── InstitutionRootVC.m
├── LoginAndRegister                          用户注册登录相关页面文件合集(具体注册登录相关配置需求逻辑,不清楚可以询问相关负责人)
│   ├── InstitutionSearchVC.h                 机构搜索结果列表显示控制器(后台开关,机构选择是否开启,开启时候在app启动后需要选择所属机构)
│   ├── InstitutionSearchVC.m
│   ├── InstitutionsChooseVC.h                机构选择页面控制器(页面由选择历史记录和搜索入口构成)
│   ├── InstitutionsChooseVC.m
│   ├── LoginRegisterViews                    用户注册和登录相关公用视图合集
│   │   ├── LoginMsgView.h                    登录页面的短信验证方式登录视图
│   │   ├── LoginMsgView.m
│   │   ├── LoginPwView.h                     登录页面账号密码登录方式视图
│   │   ├── LoginPwView.m
│   │   ├── SurePassWordView.h                设置用户账号登录密码页面控制器视图(设置密码)
│   │   ├── SurePassWordView.m
│   │   ├── ThirdLoginView.h                  登录页面底部三方登录方式配置视图(由后台开关控制哦)
│   │   └── ThirdLoginView.m
│   ├── LoginViewController.h                 用户登录页面(账号密码、短信验证、以及三方登录方式)
│   ├── LoginViewController.m
│   ├── RegisterAndForgetPwVC.h               用户登录页面注册时候设置密码和忘记密码进入页面
│   ├── RegisterAndForgetPwVC.m
│   ├── SurePwViewController.h                用户注册时候设置密码确定密码页面
│   └── SurePwViewController.m
├── MyCenterPage                              “我的”主板块儿相关文件合集
│   ├── ApplyPage                             讲师和机构认证板块儿页面合集
│   │   ├── InstitutionApplyVC.h              机构认证页面控制器(涉及机构选择、行业选择等认证所需数据提供,认证状态分认证中,被驳回,认证成功)
│   │   ├── InstitutionApplyVC.m
│   │   ├── TeacherApplyVC.h                    讲师认证页面控制器(行业选择、机构选择、身份证照片私人信息、教师资格证照片等认证所需数据提供,认证状态分认证中,被驳回,认证成功)
│   │   ├── TeacherApplyVC.m
│   │   ├── TeacherCategoryVC.h                  认证时候选择所属行业时候分类选择页面控制器(包含后台提供选择的行业类型显示,点击选择确认后返回认证页面,并显示已选择的行业类型)
│   │   └── TeacherCategoryVC.m
│   ├── BalanceDetailVC.h                      余额明细详情页面控制器(显示余额明细,明细类型是增加还是扣除由后台返回,按照后台规则处理,有时候后台类型规则会出错)
│   ├── BalanceDetailVC.m
│   ├── CategoryCommonModel                   认证所属行业分类model(将接口返回的行业分类信息转换成model便于数据引用)
│   │   ├── TeacherCategoryModel.h
│   │   └── TeacherCategoryModel.m
│   ├── CollectionListVC.h                    当前登录用户的课程收藏列表(点播、直播、班级课收藏列表)
│   ├── CollectionListVC.m
│   ├── FeedBackViewController.h              设置板块儿里面意见反馈控制器(输入内容以及提供用户手机号即可向平台反映自己宝贵的意见)
│   ├── FeedBackViewController.m
│   ├── IncomeDetailVC.h                      当前登录用户的收入明细详情页面控制器(分别分成和推广所得以及全部和本月所得)
│   ├── IncomeDetailVC.m
│   ├── LearnRecordVC.h                       当前登录用户的学习记录页面(学习记录页面按照时间点顺序来排序显示数据,点击学习记录跳转到课程播放详情页)
│   ├── LearnRecordVC.m
│   ├── MenberRecordVC.h                      当前登录用户会员充值记录页面(显示用户的充值记录)
│   ├── MenberRecordVC.m
│   ├── MenberRootVC.h                        当前登录用户点击个人中心“会员”按钮进入会员主页(显示用户会员等级,后台配置的会员类型(周卡月卡年卡等))
│   ├── MenberRootVC.m
│   ├── MessageRoot                           用户消息主页
│   │   ├── MessageDetailVC.h                 系统消息详情页面(显示系统消息全部内容)            
│   │   ├── MessageDetailVC.m
│   │   ├── MessageListVC.h                   消息列表(课程提醒、互动消息、系统消息、提问公用一个列表,点击消息即可进入对应类型的详情页面)
│   │   ├── MessageListVC.m
│   │   ├── MessageRootVC.h                   消息页面根控制器(存放四种消息列表)
│   │   ├── MessageRootVC.m
│   │   ├── QuestionChatViewController.h      提问(聊天)控制器(回复提问,相当于聊天页面,消息发送由接口直接发送并没有im)
│   │   └── QuestionChatViewController.m
│   ├── MoubaoBindViewController.h            支付宝绑定页面(调用支付宝sdk授权绑定)
│   ├── MoubaoBindViewController.m
│   ├── MyBalanceVC.h                         用户余额详情页面(涉及到余额充值,充值类型有支付宝微信以及苹果内购哦)
│   ├── MyBalanceVC.m
│   ├── MyCollectCourseVC.h                   用户收藏的课程主页根控制器(存放点播、直播、班级课列表,并且收藏课程管理功能也是在这里哦)
│   ├── MyCollectCourseVC.m
│   ├── MyIncomeVC.h                          用户的收入详情主页(可提现到微信支付宝和余额、并且顶部右上角是收入明细页面入口、推广收入页面还包含推广用户推广课程)
│   ├── MyIncomeVC.m
│   ├── MyRootViewController.h                “我的”主页(由顶部用户基本信息、订单入口、收入余额积分信息、底部后台配置的个人中心显示组成)
│   ├── MyRootViewController.m
│   ├── MyScoreNewVC.h                        用户积分主页(积分基本信息,签到入口、积分获取方式推荐、底部积分明细列表组成)
│   ├── MyScoreNewVC.m
│   ├── MycouponsListVC.h                     卡券列表(可使用、已使用、已过期三个列表公用)
│   ├── MycouponsListVC.m
│   ├── MycouponsRootVC.h                     卡券列表根控制器(存放三种类型的卡券列表)
│   ├── MycouponsRootVC.m
│   ├── OrderController                       用户订单文件
│   │   ├── OrderRootVC.h                     订单列表根控制器(全部、已支付、待支付、已取消四个列表)
│   │   ├── OrderRootVC.m
│   │   ├── OrderScreenViewController.h       订单主页右上角筛选控制器
│   │   ├── OrderScreenViewController.m
│   │   ├── OrderTypeViewController.h         订单列表公用控制器(显示用户对应四种类型的订单数据列表)
│   │   └── OrderTypeViewController.m
│   ├── OtherTypeLoginBindVC.h                三方登录类型绑定和解除绑定页面(sdk授权绑定再接合后台接口绑定登录方式)
│   ├── OtherTypeLoginBindVC.m
│   ├── PWResetViewController.h               用户重置登录密码页面(重置密码功能)
│   ├── PWResetViewController.m
│   ├── PersonalInformationVC.h               “我的”主页点击登录用户头像进入个人信息页面(可更换头像、昵称修改、手机号绑定修改,性别修改以及个性签名功能)
│   ├── PersonalInformationVC.m
│   ├── SetingViewController.h                 用户设置页面(根据后台配置,显示相关配置,密码修改,支付密码设置,三方账号绑定,修改学习兴趣(意向选择),缓存清除等相关入口)
│   ├── SetingViewController.m
├── OrderPage                                 订单支付页面文件合集
│   ├── LingquanViewController.h              卡券选择页面(当前可用卡券选择页面,涉及使用和取消使用)
│   ├── LingquanViewController.m
│   ├── OrderSureViewController.h             订单支付确定页面(选择支付方式支付宝微信余额支付)
│   ├── OrderSureViewController.m
│   ├── OrderViewController.h                 订单详情页(显示订单信息、卡券选择、积分抵扣功能)
│   ├── OrderViewController.m
│   ├── ScoreListCell.h                       订单确认的时候积分抵扣列表cell(显示积分等级,可抵扣金额)
│   ├── ScoreListCell.m
│   ├── ScoreListModel.h                      积分抵扣列表数据model
│   ├── ScoreListModel.m
│   ├── ScoreListViewController.h             积分抵扣列表(根据后台配置显示可使用的积分抵扣数据,选择某个积分抵扣额度即可抵扣相应额度)
│   └── ScoreListViewController.m
├── RootViewController
│   ├── RootV5VC.h                            五大主页导航控制器(存放“首页”、“课程”、“发现”、“学习”、“我的”五大控制器,点击底部导航切换主页面)
│   ├── RootV5VC.m
├── StudyPage
│   ├── StudyRootVC.h                        “学习”主页根控制器(由顶部学习时长信息、最近在学、和底部加入课程和学习课程列表构成,最近在学点击跳转到课程播放页面,点击查看更多进入学习记录页面)
│   ├── StudyRootVC.m
│   ├── StudyTypeCourseListViewController.h   “学习”主页底部加入课程列表(点播、直播、班级课三种课程列表,点击列表cell进入课程播放页面)
│   ├── StudyTypeCourseListViewController.m
├── TeacherPage                               讲师相关页面合集
│   ├── TeacherIntroVC.h                      讲师简介页面(由wkwebview加载简介数据)
│   ├── TeacherIntroVC.m
│   ├── TeacherListVC.h                       讲师列表数据(显示讲师头像、名字、签名信息,点击跳转讲师详情主页)
│   ├── TeacherListVC.m
│   ├── TeacherMainPageVC.h                   讲师详情主页(由讲师基本信息,介绍、动态、课程组成,还涉及关注和提问功能入口)
│   ├── TeacherMainPageVC.m
│   ├── TeahcerCourseListVC.h                 讲师主页讲师相关课程列表(点击跳转到对应课程详情页)
│   ├── TeahcerCourseListVC.m
│   ├── UserCommenListVC.h                    讲师主页关注、粉丝、最近访客点击跳转页面(显示对应用户信息列表)
│   ├── UserCommenListVC.m
├── V5_API
│   ├── EdulineV5Client.h                     项目网络接口请求单列(配置网络请求的基本信息、后台接口基本头部参数配置)
│   ├── EdulineV5Client.m
│   ├── EdulineV5_Tool.h                      项目所有工具类方法合集(时间各种样式转换方法、文字显示高度预计算等方法)
│   ├── EdulineV5_Tool.m
│   ├── Net_API.h                             项目接口请求方式配置(GET POST PUT DELETE)
│   ├── Net_API.m
│   ├── Net_Path.h                            项目原生接口配置文件(所有接口连接都存放在此)
│   ├── Net_Path.m
│   └── V5_Constant.h                         项目里面所有原生宏定义文件
└── 启动页面
    ├── HcdGuideView.h                        引导图页面(用UICollectionView来显示需要展示的引导图信息,配置左右滑动引导图)
    ├── HcdGuideView.m
    ├── HcdGuideViewCell.h                    引导图显示cell(用UIImageView显示引导图,并附上一个按钮,按钮用于点击关闭引导流程)
    ├── HcdGuideViewCell.m
    ├── LanchAnimationVC.h                    app启动动画控制页面(启动动画倒计时设置,动画显示完成或者直接跳过倒计时回调到引导图或者root控制器)
    ├── LanchAnimationVC.m
    └── LanchAnimationVC.xib
