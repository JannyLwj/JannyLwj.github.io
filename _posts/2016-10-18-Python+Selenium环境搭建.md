---
layout: post
category : lessons
tagline: "Supporting tagline"
tags : [Python, Selenium]
---

#   Python+Selenium环境搭建(Author: Janny)   
1. 前提        
安装好Python（我这里用的Pycharm）,安装好pip，并将python和pip的路径添加的环境变量的PATH下面：    
<img src="/assets/images/web1.jpg" alt=" " class="img-responsive" />    
2. 安装Selenium    
pip install -U selenium     
试试如下命令    
from selenium import webdriver    
安装成功    
3. 添加如下代码    
<img src="/assets/images/web2.jpg" alt=" " class="img-responsive" />    
4. 打开不同的浏览器，代码分别如下    
<img src="/assets/images/web3.jpg" alt=" " class="img-responsive" />     
5. 运行代码    
报错，需要driver    
Webdriver需要启动不同的driver来启动浏览器    
    Chromdriver: chromedriver.exe         
    <http://chromedriver.storage.googleapis.com/index.html>     
    
    IE: IEDriverServer.exe                                
    <http://selenium-release.storage.googleapis.com/index.html>  
    
    Firefox: geckodriver.exe        
    https://github.com/mozilla/geckodriver/releases/        
然后就能运行起来了        
