PhoneGap
===
##PhoneGap 是什么
PhoneGap 利用不同手机 OS 都有的对 Web 的支持，通过 Web 强大的表现能力，开发跨Android， iOS 甚至WindowsPhone 的手机应用。  
具体的，PhoneGap 把用 Web 语言编写的应用，打包成为可以在 Android 或者 iOS 安装的App。安装后，这些App 通过手机 OS 的 Web 接口（WebView）运行。

##PhoneGap的安装
依据官网，PhoneGap 的安装需要 Node.js 支持，首先安装 Node.js，安装后可以通过 Node.js 的命令窗口安装PhoneGap。
> npm install -g phonegap

但是实际情况远没有这个简单，PhoneGap 不是一个自足的工具，需要依赖其他工具以及你的目标手机平台的本地化工具，比如我要开发 Android 应用，那么就需要 Android 的SDK，这一集成过程会有、并且确实有很多坑。下面依次介绍其依赖关系。
### 头号大将 Cordova
PhoneGap 的核心工具是Apache Cordova，看[介绍](http://docs.phonegap.com/en/4.0.0/guide_overview_index.md.html#Overview) 这货提供了 Web 开发语言的跨平台开发（那phonegap还有什么用？）。
Cordova 编写的 app 表现为一个 html 页面，比如是 index.html。 app 在执行的时候作为一个 WebView 运行。 WebView 可以独立运行，也可以作为原生开发与 Web 开发混合应用的 web 子部件运行。
##### plugin
_plugin_，是 WebView 与 OS 底层 API 的接口，通过 plugin， app 可以从 webview 调用，比如说，陀螺仪的 API， plugin 屏蔽掉了不同手机 OS 的底层 API 差异，但是如果 OS 对应硬件之间存在的硬件差异怎么办呢？ 硬件差异是不可能通过 API 来屏蔽的，这种情况， 可以使用*第三方plugin*， 也就是专门针对一定特异硬件的 API 接口，第三方API 是可以自行开发的。  
*注意*， Cordova 建立的项目默认是不包含任何 plugin 的，哪怕是 core plugin， 所有plugin 必须显式引入。
##### 跨平台
Cordova 怎么跨平台呢？它区分共用代码和各个平台的专用代码，每个平台会有自己的文件夹彼此隔离，Cordova 会把公共文件拷贝到平台文件夹下，编译出二进制文件。编译代码时，不要编辑各个平台文件夹下的代码，而应编写公共区域的代码，则修改会被更新到所有平台文件夹下。
##### 安装
Cordova 也需要通过 Node.js 来安装。
> npm install -g cordova

##### 使用
######初始化一个项目  
> cordova create x-file org.omc.xfile BookHub

这句话的意思是：创建一个工程，工程名叫 x-file；手机 app 都会有一个类似逆序 url 的路径关系，就是org.omc.xfile 这个东东，会体现在config.xml 里，会影响到在手机中的安装位置。 BookHub 才是这个 app 被用户打开后看到的程序名字。  
也可以只输入一个工程名字，其他都会默认。

######为新项目配置支持平台
> cordova platform add android

这里以 Android 举例，说明了增加对 Android 平台的支持，添加后，该项目可以部署到 Android 平台了；如果想知道有哪些平台可供添加，可以输入命令查看  
> cordova platforms ls

######编译代码
> cordova build android

该命令会编译一个 andorid 版本的app 安装文件，即，apk 文件。编译过程可能会进入下面提及的坑。
#######坑：
一直卡在> Configuring > 0/1 projects > root project > Resolving dependencies ':classpath'
> 这个问题是由于Gradle要下载一些依赖的Library，归功于我们伟大的GFW，让我们无法访问maven的官方网站。

VPN 设置为全局模式，解决该问题.


