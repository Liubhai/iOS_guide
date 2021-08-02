# 普通评论输入框功能文档(发消息、评论回复)

`课程点评`、`课程点评回复`、`资讯评论`、`资讯评论回复`和`我的消息提问`,这些地方的内容输入框都是基于`CommentBaseView`这个基类来处理的.

* 初始化方法里面`leftButtonImageArray`是输入框左边的图标数组,里面传入图标名称,根据数组里面的图标和图标个数依次在输入框左边创建相应图标按钮(图标按钮点击事件代理依据按钮的`tag`值来判断), `placeHolderTitle`代表输入框的默认文字, `sendButtonTitle`是输入框右边的发送按钮的文字,都可以外部传入.

```
- (instancetype)initWithFrame:(CGRect)frame leftButtonImageArray:(nullable NSArray *)leftButtonImageArray placeHolderTitle:(nullable NSString *)placeHolderTitle sendButtonTitle:(nullable NSString *)sendButtonTitle;
```

* 简单的说下三个相关的通知:通过这三个通知,我们可以获取到键盘的高度,然后依据这个高度来改变输入框的`y`坐标,避免输入框被键盘遮挡,`UITextViewTextDidChangeNotification `这个通知执行的方法里面可以做很多事情,譬如限制字数,限制输入的内容的文字类型等等.

```
//输入框的内容每发生改变就会执行这个方法(通过键盘输入)
[[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(textViewValueDidChanged:) name:UITextViewTextDidChangeNotification object:nil];
//键盘将要弹起的时候
[[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(keyboardWillShow:) name:UIKeyboardWillShowNotification object:nil];
//键盘将要收起来的时候
[[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(keyboardWillHide:) name:UIKeyboardWillHideNotification object:nil];
```

* 如果在键盘弹起来的时候需要一个在输入框上面有半透明遮挡的效果,那么就可以随便放一个普通`view`并指定其`alpha(透明度)`,再根据键盘弹起和收起的通知代理方法,控制显示或者隐藏即可.(当然,这只是本项目里面的处理逻辑,如果有更好的方法或者三方工具,那更好).

* 友情提示:通知add后一定要在合适的时机remove.

