---
layout: post
category : lessons
tagline: "Supporting tagline"
tags : [Server]
---

#   Deploy Server(Author: Janny)            
1.	Buy a server  
        <https://my.vultr.com>      
2.	Link your credit card        
3.	Install OS  
    <img src="/assets/images/ds1.jpg" alt=" " class="img-responsive" />
    <img src="/assets/images/ds2.jpg" alt=" " class="img-responsive" />
    <img src="/assets/images/ds3.jpg" alt=" " class="img-responsive" />
    <img src="/assets/images/ds4.jpg" alt=" " class="img-responsive" />       
4.	Install Tomcat     
    Sudo apt-get install tomcat7    
    Check if serer can be access: http://IP:8080 in your local machine        
5.	Install java       
    Sudo apt-get default-jdk        
6.	Install FTP on server   
  	<http://note.youdao.com/share/?id=16ac099d964a22e1eee7d8360e383aea&type=note#/>        
7.	Update tomcat port       
    Cd /ect/tomcat7/server.xml     
    <img src="/assets/images/ds5.jpg" alt=" " class="img-responsive" />    
8.	Update Tomcat server.xml, add context path to FTP folder    
    Cd /ect/tomcat7/server.xml    
    Vi server.xml    
    Update file as below path:          
           <http://www.360doc.com/content/12/0506/07/3446769_208961129.shtml>    


