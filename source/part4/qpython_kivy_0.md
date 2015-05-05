Kivy的基本使用
===
Kivy是一个跨平台的GUI库，Windows，OS X， Linux， Android， iOS通吃。
> 这样看来，Kivy开发有跨iPhone的可能，有待研究

在 Android 下使用 Kivy 的基本思路是把Kivy 作为一个module import进来，然后使用相应的 API 绘制各种图形。  
但是 Kivy 也支持一些内置的语法，这是后话。

##Kivy的基本运行逻辑
在 codeskulptor 中，运行图形程序的入口是 frame.start() ，这个 frame 是simplegui.create_frame() 建立的。 frame.start() 之后，程序会进入事件循环，等待用户的各种输入事件，比如点击按钮，进行输入等等。

类似的，Kivy也会有一个进入事件循环的入口，这个总入是 kivy 模块的 App 类，调用该类的 run() 方法相当于 frame.start() 。

     from kivy.app import App
     class MyApp(App):
         def build(self):
         	return Label(text='Hello world')
     MyApp().run()

上面，AyApp 继承了 kivy.app 的 App 类，也就继承了 run() 方法，后面的 MyApp().run() 运行程序。 那么 MyApp 类的定义中 build 函数是做什么的呢？ build() 在 run() 执行之后会首先被调用，类似于对整个 kivy 程序初始化的作用，该程序最终会返回一个 widget， 作为整个 kivy 程序的根组件，可以理解为其他图形可以被绘制的起点。 widget 是在 kivy.uix 中定义的， 比如 Label 就是从 label 中定义的。上面程序的完整表达是：

    from kivy.app import App
    from kivy.uix.label import Label

    class MyApp(App):
        def build(self):
            return Label(text='Hello world')

    if __name__ == '__main__':
        MyApp().run()
        
在 QPython 中运行 kivy 程序，还需要在开头加入一条说明语句：
    #qpy:kivy

所以完整的，可以运行的程序代码是：
    #qpy:kivy
    
    from kivy.app import App
    from kivy.uix.label import Label

    class MyApp(App):
        def build(self):
            return Label(text='Hello world')

    if __name__ == '__main__':
        MyApp().run()
