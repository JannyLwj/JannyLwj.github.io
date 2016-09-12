---
layout: post
category : lessons
tagline: "Supporting tagline"
tags : [Server]
---

#   Python-the first program:  Uninstall CPS(Suthor:Janny)
1.	Copy build from share folder
刚开始学习，首先用了递归考虑文件夹的方法，这种方法稍微比较复杂，要把folder里面的每一级目录循环拷贝,拷贝有几种方式：
流文件的拷贝方式	    
open(targetFile, "wb").write(open(sourceFile, "rb").read())     
单个文件的拷贝方式    
shutil.copy(sourceDir,  targetDir)     
整个目录的拷贝方式，由于CPS的安装文件包含的文件夹比较深，所以该程序用了最方便的树结构的拷贝方式，将整个文件夹及目录用一个方式直接拷贝：    
Shutil.copytree(source_dir, target_dir)    

2.	Prepare uninstall CPS    
由于测试的时候，往往会将CPS处于打开未关闭的状态，卸载的准备活动就需要将已经打开的CPS关闭掉。    
思路：检索任务管理器，获得任务管理器中当前正在运行的任务列表，终止已经打开的CPS的进程。    
打开系统命令：    
Os.system(系统命令)无返回值    
Os.popen(系统命令)有返回值    
在这里由于要检索，任务管理器的任务，所以需要返回值，模块如下：    
def prepare_uninstall():    
    # Kill CPS & RM    
    lst_killprocess=["Motorola.CommonCPS.RadioManagement.Shell.exe",    
                     "mototrbocps.exe"]    

    tasklistrl = os.popen("tasklist").readlines()    
    for task in tasklistrl:    
        for process in lst_killprocess:    
            if len(process) < 29:    
                if process == task[0:len(process)]:    
                    print(process)    
                    pid=int(task[29:34])    
                    print(pid)    
                    try:    
                        handle = win32api.OpenProcess(1, False, pid)    
                        win32api.TerminateProcess(handle, 0)    
                        win32api.CloseHandle(handle)    
                        print("Successfully killed process %s on pid %d." % (task[0:len(process)], pid))    
                    except:    
                        pass    
            else:    
                if process[0:25]==task[0:25]:    
                    print(process)    
                    pid = int(task[29:34])    
                    print(pid)    
                    try:    
                        handle = win32api.OpenProcess(1, False, pid)    
                        win32api.TerminateProcess(handle, 0)    
                        win32api.CloseHandle(handle)    
                        print("Successfully killed process %s on pid %d." % (task[0:len(process)], pid))    
                    except:    
                        pass    

3.	Uninstall CPS    
模块如下：    
def uninstall_cpsrm():    
    #uninstall CPS from machine    
    lst_uninstall = ['Motorola RM Device Programmer',    
                  'Motorola RM Job Processor',    
                  'Motorola RM MOTOTRBO Configuration Client',    
                  'MOTOTRBO Customer Programming Software',    
                  'Motorola RM Updater Service',    
                  'Motorola RM Server']    

    lst_uuid=[]    
    lst_displayname=[]    
    registry_key=win32api.RegOpenKeyEx(win32con.HKEY_LOCAL_MACHINE,'SOFTWARE\\WOW6432Node\\Microsoft\\Windows\\CurrentVersion\\Uninstall',0, win32con.KEY_READ)    
    size=win32api.RegQueryInfoKey(registry_key)[0]    
    for i in range(size):    
        try:    
            display_uuid=win32api.RegEnumKey(registry_key, i)    
            subkey = win32api.RegOpenKeyEx(registry_key, display_uuid, 0, win32con.KEY_READ)    
            display_name, datatype = win32api.RegQueryValueEx(subkey, "DisplayName")    
            if display_name in lst_uninstall:    
                print(display_name)     
                print(display_uuid)        
                lst_displayname.append(display_uuid)                
                lst_uuid.append(display_uuid)           
                system_cmd="MsiExec.exe /X" +display_uuid+ " /quiet"                
                print(system_cmd)             
                os.system(system_cmd)              
                print("uninstall successfully")                
        except:              
            pass                 
    print("End")              

在这个模块中，当检索到注册表的节点后，花了很长的时间来获取uuid和display name，原因是一致没想到还需要subkey =           win32api.RegOpenKeyEx(registry_key, display_uuid, 0, win32con.KEY_READ)，先或侧subkey再在subkey中去找到display name，才能进行卸载
Python提供了_winreg的库来操作注册表，但是由于在本机没找到安装的_winreg库，所以就直接用的win32api来解决注册表问题             

4.	Clean machine           
def clean_machine():          
    # Remove folder            
    remove_folder = r"C:\ProgramData\Motorola"             
    if os.path.exists(remove_folder):           
        motorola_files = os.listdir(remove_folder)            
        # print(motorola_files)           
        for file in motorola_files:           
            remove_folder = r"C:\ProgramData\Motorola"           
            remove_folder = os.path.join(remove_folder, file)               
            remove_cmd = "rmdir \"" + remove_folder + "\" / S / Q"           
            print(remove_cmd)                
            os.system(remove_cmd)               
            print("Remove motorola file successfully")             

    # Run Drop DB          
    try:           
        process="sqlcmd -S .\\MOTORMSVR2 -Q \"IF  EXISTS (SELECT name FROM sys.databases WHERE name = N'RMServer') ALTER DATABASE [RMServer] SET SINGLE_USER WITH ROLLBACK IMMEDIATE\""            
        print(process)            
        os.system(process)          
        process="sqlcmd -S .\\MOTORMSVR2 -Q \"IF  EXISTS (SELECT name FROM sys.databases WHERE name = N'RMServer') drop database [RMServer]\""       
        print(process)             
        os.system(process)            
        process="sqlcmd -S .\\MOTORMSVR2 -Q \"IF  EXISTS (SELECT name FROM sys.databases WHERE name = N'RMAuthorizationStore') ALTER DATABASE [RMAuthorizationStore] SET SINGLE_USER WITH ROLLBACK IMMEDIATE\""             
        print(process)            
        os.system(process)             
        process="sqlcmd -S .\\MOTORMSVR2 -Q \"IF  EXISTS (SELECT name FROM sys.databases WHERE name = N'RMAuthorizationStore') drop database [RMAuthorizationStore]\""            
        print(process)            
        os.system(process)           
    except:          
        pass            

卸载完毕CPS，本地会遗留一些文件和数据库需要清除，该模块删除本地的遗留文件和清除数据库，在这块遇到删除本地遗留文件怎么都删除不了的情况，报错Error 5， access denied, 分析发现是folder是只读属性，直接删不了，用chmod改文件夹的只读属性也改不了，只能改到文件的属性，那么就又需要遍历文件夹，改文件的只读属性，这样操作也比较繁琐，后来采用系统命令来删除，一个命令搞定。                    
