
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
     
### Canvas组件
tk.Canvas()创建一个Canvas。  
bd或者borderwidth可以设置边框的“厚度”。这个“厚度”会占用canvas的实际可用空间，而不是挤占外部空间。  
####Canvas事件
为了让canvas组件响应外部事件，需要bind方法进行绑定：
    canvas.bind("event-name-string", event_handler)
比如，我们要绑定鼠标事件，则event-name-string为"Button"，任何鼠标按键按下都会触发该事件，如果要绑定特定鼠标按键的按下事件，则鼠标的左键、中键、右键对应的事件名称分别是：Button-1、Button-2、Button-3（*请注意，只有双键的鼠标，右键仍然是Button-3*）。
Button事件实际上相当于按键按下事件；如果想捕获按键弹起事件，需使用ButtonRelease事件，特定鼠标按键的弹起事件命名同Button事件。   
*注意*当同时使用了Button和Button-i绑定事件句柄之后，事件发生后，Button绑定失效。
*注意2*如果同一事件绑定了两个句柄，则代码中后绑定的一个会覆盖先绑定的一个。
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
      
  
