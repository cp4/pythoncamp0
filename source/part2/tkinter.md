可视工具：tkinter
===
## 初识tkinter
为了使编程更加直观有趣，使用可视化的界面更引人入胜。GUI就是Graphical User Interface，图形化用户接口的意思。很多编程平台都有自己的GUI，python既是一门语言，也是一种开发环境，提供了多种GUI，其中，官方认可的GUI叫做tkinter，基于Tcl/tk的GUI。  
官网文档入口：
https://docs.python.org/2/library/tkinter.html
### 安装
官方文档中说，tkinter是和python绑定、一般来说直接可用的，如果不可用呢？怎么安装却没有正式提及。顺着文档链找进去，才在[这里](http://tkinter.unpythonic.net/wiki/How_to_install_Tkinter)找到正式描述：
Windows和OS X的python包管理器对tkinter支持较好，但是Linux和BSD系统需要单独安装，在Ubuntu系统下，使用命令：
````python
 sudo apt-get install python python-tk idle python-pmw python-imaging
 ````
 其实Ubuntu默认即已经安装了python，其中有些包是不必安装的，但是这个安装命令会安装tkinter。
 
## 使用tkinter
 首先，要引用tkinter包，对python2.x
      import tkinter as tk
 对python2.7及以上，以及python3.x则要用
      import Tkinter as tk
 以下一概用tk指代包名称。

### 基本框架
tkinter中需要建立一个**窗口**，作为整个程序的主界面，其他内容都在窗口内发生。  
主窗口的建立语句是
     *window* = tk.Tk()
其中window是自定义名称，后面的语句建立了一个窗口对象。  

tkinter也是事件驱动的编程框架，需要外部事件的推动才能运行。不同于simplegui，tkinter中必须明确建立事件循环，即，用来等待外部事件的循环。否则的话，整个tkinter都运行不了。开启事件循环的代码：
     tkinter.mainloop()

## 注意
### 使用中文
python默认将所有程序代码视为ASCII，如果使用了中文，它就会不认识，然后报错。经验证，在不显式提示编码信息的情况下，使用   
      u"中文"
或者    
      u"中文".encode(”utf-8")
都是无效的。   
显式提示编码信息的方法有，在代码文件的第1行或者第2行，输入：
     # coding=utf-8
*注意：*coding和=之间不能用空格。  
或者      
     # -*- coding: utf-8  
 *注意2：*如果要确认当前文件的编码方式，在Linux下可以使用file -i filename命令   
*参考*[https://www.python.org/dev/peps/pep-0263/](https://www.python.org/dev/peps/pep-0263/)
      
  
