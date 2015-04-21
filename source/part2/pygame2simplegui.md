使用simplegui
===
simplegui是www.codeskulptor.org开发的用于交互的python人机界面。接口比较简单，易于上手。  
如果想在本地使用simplegui怎么办呢？python的GUI大户Pygame下有对simplegui支持的封装。安装该模块即可在本地使用simplegui了。
###安装SimpleGUICS2Pygame包
 SimpleGUICS2Pygame[官网](https://pypi.python.org/pypi/SimpleGUICS2Pygame)上对于安装有介绍，各大OS安装方式有区别，根据同学们的使用来看，Ubuntu, Windows较易，OS X问题较多。
#####在Windows下pip安装方式
如果使用python2.7以上版本，已经自动安装好了pip。在命令行窗口下，输入pip --version可以看到
>pip 1.5.6 from C:\Python27\lib\site-packages (python 2.7)  

输入命令：
> pip install SimpleGUICS2Pygame

最这么easy。
但是，这还不够。pip的包管理功能看来还不如ubuntu下的apt工具。SimpleGUICS2Pygame的运行依赖于Pygame，如果没有Pygame，运行会抱怨：Pygame不可用。
######安装Pygame
直奔Pygame[官网下载页](http://www.pygame.org/download.shtml)，下载最新的msi包，安装，妥。
###使用SimpleGUICS2Pygame
官网说得很清楚了：
>Simply change
>>import simplegui

>by
>>import SimpleGUICS2Pygame.simpleguics2pygame as simplegui