---
layout: post
category : Study
tagline: "Supporting tagline"
tags : [Server]
---

1.	Buy a server
    https://my.vultr.com
2.	Link your credit card 
3.	Install OS
4.	Install Tomcat
    Sudo apt-get install tomcat7
    Check if serer can be access: Http://IP:8080 in your local machine
5.	Install java
    Sudo apt-get default-jkd
6.	Install FTP on server:
    http://note.youdao.com/share/?id=16ac099d964a22e1eee7d8360e383aea&type=note#/
7.	Update tomcat port
    Cd /ect/tomcat7/server.xml
8.	update Tomcat server.xml, add context path to FTP folder
    Cd /ect/tomcat7/server.xml
    Vi server.xml
    Update file as below path:
    http://www.360doc.com/content/12/0506/07/3446769_208961129.shtml
