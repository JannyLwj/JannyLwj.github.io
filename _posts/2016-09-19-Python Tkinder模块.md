---
layout: post
category : lessons
tagline: "Supporting tagline"
tags : [Python]
---

#   Python Tkinder模块(Author: Janny)           
#  Tkinder模块是在学习写计算器的时候接触到的，是TK图形用户界面工具包标准的Python借口，轻量级的跨平台图形用户界面开发工具。    
   1.	Calculator 代码见：  <https://github.com/JannyLwj/Calculator/blob/master/Calculator.py>    
   2.	Tkinter练习代码见：  <https://github.com/JannyLwj/TestTkinder>    
   3.	今天学习Tkinter中的events事件：     

   Binding：绑定事件和事件处理函数    
       有三个层次的binding：Instance binding, Class binding, Application binding；         
   （1）Instance binding：将事件响应绑定到指定的widget，使用widget.bind(sequence, func, add)；    
   （2）Class binding：将事件响应绑定到一个类型下的全部widgets，使用bind_class(class, sequence, func, add)；    
   （3）Application binding：当事件发生时，无论Application的哪个widget在focus状态下，都会产生handler响应，使用bind_all(sequence, func, add)；    
    
    
   Event sequences：包含一个或多个事件模板的字符串（a string containing one or more event patterns    ）
   事件模板：<[modifier-]...type[-detail]>    
   （1）事件模板放在<>中；    
   （2）type表示事件的类型，例如key press 或 mouse click；    
   （3）modifier可以增加一些组合操作，例如shift 或 control；    
   （4）detail描述具体的key，对于鼠标而言指代的哪个键，1 for button 1, 2 for button 2, 3 for button 3；    
    下面是一个例子：    
   <img src="/assets/images/event.jpg" alt=" " class="img-responsive" />       
        
            
    Event type：事件类型    
    •	Activate：widget从非激活状态到激活状态    
    •	Button：点击鼠标按键（The user pressed one of the mouse buttons）    
    •	ButtonRelease：松开鼠标按键（The user let up on a mouse button）    
    •	Configure：用户改变widget的尺寸    
    •	Deactivate：widget由激活状态变成非激活状态    
    •	Destroy：widget被销毁    
    •	Enter：用户将鼠标移动到widget上    
    •	Expose：当被其它窗口覆盖后再出现时触发（This event occus whenever at least some part of your application or widget becomes visible after having been coverd up by another window）    
    •	FocusIn：widget获得输入的focus    
    •	FocusOut：input focus从widget中移出    
    •	KeyPress：用户点击键盘上的按键(The user pressed a key on the keyboaed)    
    •	KeyRelease：用户松开键盘上的按键(The user let up a key on the keyboard)    
    •	Leave：用户将鼠标移除widget    
    •	Map：widget变得可见(A widget is being mapped, that is, made visible in the application)    
    •	Motion：用户将整个鼠标移入widget(The user moved the mouse pointer entirely within a widget)    
    •	MouseWheel：用户滑动鼠标滚轮    
    •	Unmap：widget变得不可见(A widget is being unmapped and is no longer visible)    
    •	Visibility：当application的某部分在屏幕上变的可见(Happens when at least some part of the application windoww becomes visible on the screen)
        
            
                
    Event modifiers：事件修饰语    
    •	Alt：alt按键    
    •	Any：任意的按键    
    •	Control：control按键    
    •	Double：短时间内事件发生两次(Specifies two events happending close together in time)    
    •	Lock：shift lock按键    
    •	Shift：shift按键    
    •	Triple：Triple kill，和double一样的原理     
    
    
    Key names:键盘上按键的名字    
        键盘对应的Event types是keyPress和KeyRelease，有三种不同的方法来表示：    
    •	keysym：key的字符串名字    
    •	keycode：key code，表示哪个键被按下    
    •	keysym_num：shows a numeric code equivalent to the key symbol    
    
    
    通知事件的产生。它可以是一个函数，也可以是一个类型的方法：    
    def hanglerName(event)：    
    def handlerName(self, event)：    
    下面是Event object的属性：    
    •	char：KeyPress和KeyRelease Event，char被设为该character    
    •	delta：MouseWheel Event    
    •	height：Configure Event，表示widget的新的height（像素）    
    •	keycode：KeyPress和KeyRelease Event， 表示数字按键的值    
    •	keysym：KeyPress和KeyRelease Event，表示一些特殊的按键的值    
    •	keysym_num：KeyPress和KeyRelease Event，this is set to a numeric version of the .keysym field    
    •	num：鼠标按键，1，2，3    
    •	serial：An integer serail number that is incremented every time the server processes a client request    
    •	state：A integer describing the state of all the modifier keys    
    •	time：两次时间发生的时间间隔    
    •	type：A numeric code describing the type of event    
    •	widget：指向触发事件的widget    
    •	width：Configure Event，表示widget的新的width（像素）    
    •	x：当事件发生时，鼠标所在处的Y坐标，以widget的左上角为原点    
    •	y：当事件发生时，鼠标所在处的Y坐标，以widget的左上角为原点    
    •	x_root：当事件发生时，鼠标所在处的X坐标，以屏幕的左上角为原点    
    •	y_root：当事件发生时，鼠标所在处的Y坐标，以屏幕的左上角为原点    
    
