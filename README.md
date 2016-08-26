# ToastCompat
我本想用SnackBar来替代，可SnackBar有下面几个问题要注意：

1. make()方法的第一个参数的view,不能是有一个ScrollView.
因为SnackBar的实现逻辑是往这个View去addView.而ScrollView我们知道,是只能有一个Child的.否则会Exception.

2. 如果大家在想把Toast替换成SnackBar.需要注意的是,Toast和SnackBar的区别是,前者是悬浮在所有布局之上的包括键盘,而SnackBar是在View上直接addView的.
所以SnackBar.show()的时候,要注意先把Keyboard.hide()了.不然,键盘就会遮住SnackBar.

想想还是自己维护了Toast的队列，那么首先要判断用户是否关闭了消息通知权限，如果没有关闭我还是想用系统提供的队列,网上了很多没有发现可用代码，只能自己看源码了。

http://blog.csdn.net/a3676212/article/details/51830299
