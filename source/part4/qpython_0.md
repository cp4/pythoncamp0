QPython
===
## 安装
源头在google play上面，诸多不便。使用小米_应用商店_可以下载qpython和qpython 3，但是下载后发现是0.x版本，而google上是1.0.6。  
在QPython微博上看到，应用宝把QPython推荐为精品应用，安装应用宝后下载QPython，是0.9.4，略好……
####坑
运行kivy测试程序时，import kivy出现错误：
> KeyError: "ANDROID_APP_PATH"

google可搜到，但不多，无解决方案。baidu，找到似乎是river的答案：增加"#qpy:kivy"，初试失败。后来把QPython整个卸载掉，又用小米商店重装后，使用river的解决方式，成功。
[这里](http://tieba.baidu.com/p/3620158767)也有人解答，回帖也出现river的影子，里面的回答有价值。

## 使用
代码的运行有三种模式。
1. console模式
2. kivy模式
3. Webapp模式

Console不说了，Kivy相当于本地GUI，Webapp则遵从web开发方法。  
从kivy主页来看，这个GUI就是给移动应用开发的，可以接受触摸等操作。
我认为Web开发在未来的移植性会较好，qpython[微博](http://www.weibo.com/qpython?from=profile&wvr=5&loc=infdomain)主推super webapp模式。但没找到所谓的supper webapp是什么，从给出的链接看，就是webapp开发嘛。  
考虑web开发可能需要学习前端知识，更适合熟悉HTML开发的工程师，暂时不想做，如果有时间还真想试试。

## 代码的输入
QOCR模式，太酷了。
用手机录入代码非常非常麻烦，大妈写了一篇PC开发的文章[如何自在的折腾QPy](http://codelab.qpython.org/pythonic/init-my-qpy-env.html)，但是QPython本身提供的QOCR方式也非常巧妙，小规模代码用起来也不错。
这是一种把代码编码成二维码，然后用手机扫描二维码就自动录入代码的方式。代码转换成二维码的工具网址是：http://qpython.com/#qrcode
