---
layout: post
category : lessons
tagline: "Supporting tagline"
tags : [Python]
---

#   Python爬虫之Scrapy框架安装配置(Suthor:Janny)
1.安装Python     
   添加如下变量到环境变量D:\python2.7.7;  D:\python2.7.7\Scripts
   配置好了之后，在命令行中输入 python –version，如果没有提示错误，则安装成功
 
2.安装pywin32    
    在windows下，必须安装pywin32
    安装地址：<http://sourceforge.net/projects/pywin32/>    
    下载对应版本的pywin32，直接双击安装即可，安装完毕之后验证：
 
    在python命令行下输入
    import win32com
    如果没有提示错误，则证明安装成功    
    
3.安装pip    
    pip是用来安装其他必要包的工具，首先下载 get-pip.py    
    下载好之后，选中该文件所在路径，执行下面的命令     
    python get-pip.py    
    执行命令后便会安装好pip，并且同时，它帮你安装了setuptools    
    安装完了之后在命令行中执行    
 
    pip --version    
    如果提示如下，说明就安装成功了，如果提示不是内部或外部命令，那么就检查一下环境变量有没有配置好吧，有两个路径。    
    <img src="/assets/images/pip.jpg" alt=" " class="img-responsive" />        
    
4.安装pyOPENSSL        
    在Windows下，是没有预装pyOPENSSL的，而在Linux下是已经安装好的。    
    安装地址：https://launchpad.net/pyopenssl    
    下载下来直接run    
    
5.安装 lxml   
    lxml的详细介绍 点我 ，是一种使用 Python 编写的库，可以迅速、灵活地处理 XML    
    直接执行如下命令     
    pip install lxml    
    就可完成安装，如果提示 Microsoft Visual C++库没安装，则点我下载支持的库。    
    安装lxml时，一直报错：unable to find vcvarsall.bat 文件，这里我搞了好久，先去下载了wheel，再下载“lxml-3.6.4-cp27-cp27m-win32.whl”，安装。报错unable to find zip file.    
    最后还是想把报错解决掉，到处查找资料。最终在<http://blog.csdn.net/secretx/article/details/17472107>查到最终解决方法。     
    
6.安装Scrapy        
    最后就是激动人心的时刻啦，终于可以享受到胜利的果实啦！        
    执行如下命令: pip install Scrapy        
 
    pip 会另外下载其他依赖的包，这些就不要我们手动安装啦，等待一会，大功告成！    
7.验证安装        
    输入 Scrapy    
    如果提示如下命令，就证明安装成功啦，如果失败了，请检查上述步骤有何疏漏。    
     <img src="/assets/images/Scrapy.jpg" alt=" " class="img-responsive" />      
