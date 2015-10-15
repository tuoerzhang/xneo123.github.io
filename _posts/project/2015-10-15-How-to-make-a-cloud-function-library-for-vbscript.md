---
layout: post
title: How-to-make-a-cloud-function-library-for-vbscript
category: project
description: Function library from github
---

# How to make a cloud function library for vbscript

##You need a github storage
###my location is http://github.com/xneo123
##Put your library scripts in github and get raw URL
###enter your script page and click Raw button
![raw-button](https://raw.githubusercontent.com/xneo123/EffecientWork/master/KnowledgeTree/images/raw-button.png)
###Note your raw URL
![raw-URL](https://raw.githubusercontent.com/xneo123/EffecientWork/master/KnowledgeTree/images/raw-URL.png)
##Write your client script and use the function library
    
###Get Function library from Step 2

    'create xml object
    Set xml=CreateObject("MSXML2.XMLHTTP")    
    'get function library from github
    xml.open "GET","https://raw.githubusercontent.com/xneo123/EffecientWork/master/checkIPAddress-functionlib.vbs",false 
    'send the request
    xml.send
    'what you get is the whole function library as a long string
    strInternetText=xml.responseText    

###Make it as a temp vbs file

    CreateFile(strInternetText)
    Function CreateFile(strText)    
    	Set fso = CreateObject("scripting.filesystemobject")
    	strFolderPath=left(wscript.scriptfullname,instrrev(wscript.scriptfullname,"\")-1) 
    	Set myfile=fso.CreateTextFile(strFolderPath&"\Temp.vbs",True,false)
    	myfile.Write strText	
    	myfile.Close
    	Set fso=nothing
    End Function 


###Execute this temp vbs
    
    Set fso = CreateObject("scripting.filesystemobject")
    strFolderPath=left(wscript.scriptfullname,instrrev(wscript.scriptfullname,"\")-1)     
    ExecuteGlobal CreateObject("Scripting.FileSystemObject").OpenTextFile(strFolderPath&"\temp.vbs",1).ReadAll

###Now you can Use function what you need in function library you just load from github
I have 2 functions need to use, what I need is very simple to use
    checkself
    checkEachOther("chenaib2")
    
    
If you have any problem you can click read the original below
You can also find the demo scripts from [EffecientWork](https://github.com/xneo123/EffecientWork)