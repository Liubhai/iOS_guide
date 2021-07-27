# 项目文件结构说明

项目结构

```shell
.
├── Agora_edu_sdk                     :声网直播原生文件
│   ├── AgoraRtm.h 
│   ├── AgoraRtm.m
│   ├── KeyCenter.h
│   ├── KeyCenter.m
│   ├── Manager
│   ├── Replay
│   ├── Room
│   └── Utils
├── AnyModel                         :EdulineV5用户信息模型数据
│   ├── V5_UserModel.h
│   └── V5_UserModel.m
├── Assets.xcassets                :本地素材
├── Base.lproj
│   ├── LaunchScreen.storyboard         :EdulineV5启动图
├── BaseVC                                :EdulineV5一些基本公用类
│   ├── BaseViewController.h            :EdulineV5公用控制器
│   ├── BaseViewController.m
│   ├── EdlineV5_Color.h                :EdulineV5颜色管理类
│   ├── EdlineV5_Color.m
│   ├── EmptyCell.h                        :EdulineV5空数据cell
│   ├── EmptyCell.m
│   ├── WKWebIntroview.h                :EdulineV5公用wkwebview
│   ├── WKWebIntroview.m
│   ├── WkWebViewController.h
│   └── WkWebViewController.m
├── Course                                :课程详情相关页面
├── CoursePage                            :“课程”主页相关页面
├── EdulineToolLib                        :一些简单工具类文件
├── FindPage                                :发现页面板块儿的页面
├── HomePage                                :”主页“板块儿页面
├── InstitutionsPage                    :机构相关页面
├── LivePage                                :声网直播相关页面
├── LoginAndRegister                    :用户注册、登录、密码相关页面
├── MyCenterPage                            :”我“板块儿相关页面
├── OrderPage                                :用户订单相关页面
├── PrefixHeader.pch
├── RootViewController                    :项目导航
├── StudyPage                                :学习页面
├── TeacherPage                            :讲师相关页面
├── V5_API                                :项目配置
│   ├── Api_Config.h
│   ├── EdulineV5Client.h                :网络请求单列
│   ├── EdulineV5Client.m
│   ├── EdulineV5_Tool.h                :简单的公用工具方法
│   ├── EdulineV5_Tool.m
│   ├── Net_API.h                        :网络接口请求
│   ├── Net_API.m
│   ├── Net_Path.h                        :接口文档
│   ├── Net_Path.m
│   └── V5_Constant.h                    :三方配置、宏定义等
├── Video_SDK                                :阿里云点播视频播放SDK原生文件
│   └── AlivcSDK
└── 启动页面
    ├── HcdGuideView.h                    :启动页面引导图
    ├── HcdGuideView.m
    ├── HcdGuideViewCell.h                :引导图cell
    ├── HcdGuideViewCell.m
    ├── LanchAnimationVC.h                :启动图逻辑页面
    ├── LanchAnimationVC.m
    └── LanchAnimationVC.xib
