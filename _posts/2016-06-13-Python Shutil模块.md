---
layout: post
category : lessons
tagline: "Supporting tagline"
tags : [Python]
---

#   Python-Shutil模块(Author:Janny)
在写uninstall CPS的程序中，原本打算用os.copy来copy file，无意中发现了Shutil模块，模块介绍如下:   
    
1. shutil.copyfileobj(fsrc, fdst[, length])    
将类文件对象fsrc 的内容复制到类文件对象fdst。The integer length, if given, is the buffer size.特别地，负length值意味着不会以块的方式循环复制源数据；默认情况下数据是以块的方式读取以避免无节制的内存消耗。请注意，如果fsrc对象的当前文件位置不是0，仅从当前文件位置到文件的结尾的内容将被复制。    
    
2. shutil.copyfile(src, dst)    
复制文件src的内容（不包含元数据）到文件dst。dst 必须是完整的目标文件的名称；shutil.copy()接受目标路径为目录的复制。如果src和dst是相同的文件，则会引发Error。目标位置必须是可写的；否则，将引发异常IOError。如果dst已经存在，它将被替换。特殊文件如字符或块设备和管道无法使用此函数复制。src和dst是以字符串给出的路径名称。        
3. shutil.copymode(src, dst)        
将权限位从src复制到dst。文件内容、 所有者和组不会受到影响。src和dst是作为字符串给出的路径名称。    
    
4. shutil.copystat(src, dst)    
将权限位、 最后存取时间、 最后修改时间和标志从src复制到dst。文件内容、 所有者和组不会受到影响。src和dst是作为字符串给出的路径名称。        
5. shutil.copy(src, dst)    
将文件src复制到文件或目录dst。如果dst是一个目录，将在该指定的目录中创建（或覆盖）一个具有和src相同名称的文件。权限位也被复制。src和dst是作为字符串给出的路径名称。
    
6. shutil.copy2(src, dst)    
类似于shutil.copy()，但元数据也复制 — 事实上，它只是shutil.copy()加上copystat()。这是类似于Unix 的命令cp -p。   
    
7. shutil.ignore_patterns(*patterns)    
此工厂函数创建一个函数，它可以作为可调用用于copytree()的ignore参数，忽略匹配glob风格的模式的文件和目录。请参阅下面的示例。    
2.6 版中新增。    
    
8. shutil.copytree(src, dst, symlinks=False, ignore=None)    
以递归方式复制以src为根的整个目录树。目标目录dst必须不存在；它和父目录将一起创建。复制权限和目录使用copystat()的，单个文件的复制使用shutil.copy2()。
如果syslinks为真，源树中的软链接表示为新树中的软链接，但不复制原始链接的元数据；如果为假或被省略，链接的文件内容和元数据将复制到新树。
如果给定ignore，则它必须是可调用将接收作为其参数由os.listdir()返回后造访了copytree()和其内容的列表的目录。由于copytree()以递归方式调用，ignore可调用对象将对每个复制的目录调用。可调用必须返回一个序列的目录和文件的名称，相对于当前目录 （即第二个参数中的项的子集） ；这些名称将在复制过程中被忽略。 ignore_patterns()可以用来创建这种忽略基于 glob 样式名称的调用。
如果异常发生，将引发一个带有原因列表的Error。    
它的源代码应该只作为实例而不是最终的工具。    
版本 2.3 中的更改：如果复制中发生任何异常，将引发Error而不是打印一条信息。    
2.5 版本中的更改：创建生成dst所需的中间目录，而不是引发错误。复制权限和目录使用copystat()倍。    
2.6 版本中的更改：增加ignore参数以便能够影响复制的内容。    
    
9. shutil.rmtree(path[, ignore_errors[, onerror]])    
删除整个目录树；path必须指向一个目录（不可以是指向目录的软链接）。如果ignore_errors为真，将忽略删除失败产生的错误；如果为假或被省略，这些错误将通过调用onerror指示的处理程序处理，或者如果省略onerror，它们将会引发异常。
如果提供onerror，它必须是一个接受三个参数的可调用对象：function、path和excinfo。第一个参数function是引发异常的函数；它将会是os.path.islink()、os.listdir()、 os.remove()或os.rmdir()。第二个参数path是传递给function的路径名称。第三个参数excinfo是由sys.exc_info()返回的异常信息。onerror抛出的异常不会被捕获。
2.6 版本中的更改：明确检查path是否是一个符号链接，在这种情况下将引发OSError。    
    
10. shutil.move(src, dst)    
以递归方式移动文件或目录（src）到另一个位置（dst）。    
如果目标是一个目录或一个目录的符号链接，那么src被移动到该目录中。    
目标目录必须已经存在。如果目标位置已存在，但不是一个目录，它可能根据os.rename()的语义被覆盖。    
如果目标是在当前的文件系统上，则使用os.rename() 。否则，将src复制到dst（使用shutil.copy2()），然后删除。    
版本2.3中新增。 
    
11. exception shutil.Error    
此异常收集在多文件操作过程中引发的异常。对于copytree()，该异常的参数是一个三元组（srcname, dstname, exception）。    
版本2.3中新增。    

