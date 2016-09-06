---
layout: post
category : lessons
tagline: "Supporting tagline"
tags : [Python]
---

#   Python Lesson1(Author: Janny)     
#    os模块概述 
    Python os模块包含普遍的操作系统功能。如果你希望你的程序能够与平台无关的话，这个模块是尤为重要的。(一语中的)
    
#    常用方法  
    
os.name    
    输出字符串指示正在使用的平台。如果是windows 则用'nt'表示，对于Linux/Unix用户，它是'posix'。
    
os.getcwd()    
    函数得到当前工作目录，即当前Python脚本工作的目录路径。
    
os.listdir()       
    返回指定目录下的所有文件和目录名。
    >>> os.listdir(os.getcwd())    
     ['Django', 'DLLs', 'Doc', 'include', 'Lib', 'libs', 'LICENSE.txt', 'MySQL-python-wininst.log', 'NEWS.txt', 'PIL-wininst.log', 'python.exe', 'pythonw.exe', 'README.txt', 'RemoveMySQL-python.exe', 'RemovePIL.exe', 'Removesetuptools.exe', 'Scripts', 'setuptools-wininst.log', 'tcl', 'Tools', 'w9xpopen.exe']     
     >>> 
    
os.remove()    
     删除一个文件。   
    
os.system()    
     运行shell命令。     
     >>> os.system('dir')     
     0     
     >>> os.system('cmd') #启动dos    
    
os.sep 可以取代操作系统特定的路径分割符?    
    
os.linesep字符串给出当前平台使用的行终止符        
    >>> os.linesep    
    '\r\n'            #Windows使用'\r\n'，Linux使用'\n'而Mac使用'\r'。    
    >>> os.sep    
    '\\'                 #Windows        
    >>>   
    
os.path.split()    
    函数返回一个路径的目录名和文件名    
    >>> os.path.split('C:\\Python25\\abc.txt')    
    ('C:\\Python25', 'abc.txt')   
    
os.path.isfile()和os.path.isdir()函数分别检验给出的路径是一个文件还是目录。   
    
os.path.isdir(os.getcwd())    
    True    
    >>> os.path.isfile('a.txt')    
    False  
    
os.path.exists()函数用来检验给出的路径是否真地存在    
    >>> os.path.exists('C:\\Python25\\abc.txt')    
    False    
    >>> os.path.exists('C:\\Python25')    
    True    
    >>>   
    
os.path.abspath(name):获得绝对路径  
    
os.path.normpath(path):规范path字符串形式 
    
os.path.getsize(name):获得文件大小，如果name是目录返回0L    
    
os.path.splitext():分离文件名与扩展名   
    >>> os.path.splitext('a.txt')    
    ('a', '.txt')  
    
os.path.join(path,name):连接目录与文件名或目录    
    >>> os.path.join('c:\\Python','a.txt')    
    'c:\\Python\\a.txt'    
    >>> os.path.join('c:\\Python','f1')    
    'c:\\Python\\f1'    
    >>>  
    
os.path.basename(path):返回文件名   
    
os.path.basename('a.txt')    
    'a.txt'    
    >>> os.path.basename('c:\\Python\\a.txt')    
    'a.txt'    
    >>> 
    
os.path.dirname(path):返回文件路径    
    >>> os.path.dirname('c:\\Python\\a.txt')    
    'c:\\Python'    
 