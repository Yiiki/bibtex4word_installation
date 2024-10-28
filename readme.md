# readme

yjl，yzy @ RenGroup 2023/3/14修改

bibtex4word的官方网站：<http://www.ee.ic.ac.uk/hp/staff/dmb/perl/index.html> 

官方网站上有详细的安装步骤，使用指导等等内容。

安装使用bibtex4word需要三种软件。

第一种是reference manager软件（不必需），作用是用来下载、管理文章及其bibtex格式的引文，最著名的软件应该是endnote，bibtex4word的作者强烈推荐JabRef，可选择性使用。

第二种是文本编辑管理系统软件，以下简称为tex软件（因为这类软件名称中一般带有tex），作者推荐使用Miktex，最新安装包提供在本文件夹中。官网地址：<https://miktex.org/> 

第三种则是bibtex4word。安装包提供在本文件夹中。

## Miktex安装

在官网上下载安装包，<https://miktex.org/> ，运行Miktex安装包，连续点击“下一步”安装即可。

不推荐为全部用户安装此软件，建议只为自己安装此软件。虽然个人电脑一般也不会有其它用户使用，但为全部用户安装可能会出现一些不好解决的问题。

确认隐藏文件夹及文件可见。打开控制面板-在控制面板中搜索“文件资源管理器选项”（或仅搜索“文件”也可），点击“显示隐藏的文件和文件夹”子项目（或者打开“文件资源管理器选项”，进入“查看”选项卡），勾选“显示隐藏的文件、文件夹和驱动器”选项。

打开Miktex Console

检查更新，并对检查出的更新立即更新

可以在宏包选项卡内搜索需要的宏包，在使用各类不常用style时可能需要这一步。另外，下载安装宏包之后，建议在“任务”菜单栏内，“刷新文件名数据库”和“刷新字体映射文件”。

## bibtex4word安装

将bibtex4word压缩包解压。

将文件夹中的bibtex4word.dot文件，复制到microsoft word的启动路径下。一般来说，路径为

C:\\Users\\\*\*\*\*\*\\AppData\\Roaming\\Microsoft\\Word\\STARTUP

在一些版本的windows中，Users文件夹可能被显示为中文“用户”，\*\*\*\*\*为你的用户名。

word的启动路径可以通过，打开word-文件-更多...-选项-高级-常规-文件位置-启动，的方法来找到。

将bibtex4word.dot复制之后，建议右键点击打开属性，确认文件没有被锁定。

## 功能测试

打开上一步中解压缩之后的文件夹，打开Test4w.doc文件。

按照文件中的描述测试bibtex4word的功能。（对应按钮可以在“加载项”中找到）

## bug解决

遇到的bug可以在bibtex4word官网上寻求解决办法。<http://www.ee.ic.ac.uk/hp/staff/dmb/perl/index.html> 

本文档中给出的是官网外的一些问题的补充解决方法。

* bib4word报错解决办法

添加了BIBTEX环境变量到miktex的bib程序下

变量名：BIBTEX

变量值：C:\\Users\\13971\\AppData\\Local\\Programs\\MiKTeX\\miktex\\bin\\x64\\bibtex.exe

参考链接

https\://tex.stackexchange.com/questions/325302/running-bibtex4word-with-office-2016-texlive-2015?newreg=63b1dcf6a5294a5292dba801847f8f4d

这人的回复有用：Similar setup here (Word 2010+TexLive 2016, Win7 64bit). On the first attempt, I got the same error. After executing the same steps you've mentioned, it's working. Well, not exactly the same: I added OPENOUT_ANY = r to C:\\texlive\\2016\\texmf.cnf. Maybe try this!? Btw, does anyone know if the author of Bibtex4Word, Mike Brookes, is here on StackExchange? – rotton Oct 5 '16 at 11:22

综合以上操作解决了问题

* bibtex was unable to find style：xxx 错误

这个错误可能是由于使用多个tex软件时的冲突导致。一种解决方法是卸载之前使用过的tex软件，如texlive等，并删除相关的环境变量。另外也有可能是使用的style所需的宏没有被正确安装，参考官网上的error messages可以解决。

## update in Oct28,2024
添加新样式方法，You can verify that style xxx is visible to MikTex by typing "kpsewhich xxx.bst" from a command window. 该命令行可以直接在MikTeX console客户端界面上找到。

通过运行上述命令获得bst文件存储文件夹，以后直接把找到/编辑好的bst文件拖进来，**然后在客户端“任务”--》“更新文件名数据库” （所有更新字样的都可以点一遍）**，这样就可以告诉MiKTeX你加入了新的样式文件；如果更改内容，则保存后，不用再点更新，直接在word里开用。

除此以外，还可参考下述方法：

Error Messages

Bibtex was unable to find style: xxx (or "Empty BBL file: ...") 

This error may mean that the requested BibTeX style is not installed in MikTex. To install it, see "Error Messages: Bibtex was unable to find style: xxx " above."

The style "xxx" was not available. This means that the style is either (a) spelled incorrectly or else (b) that has not been installed in Miktex. To solve the latter cause, open the MiKTeX package manager (Programs->MiKTeX v.v->Browse Packages), type "xxx.bst" in the "Filename:" box and click "Filter". If the package has not yet been installed, the column headed "Installed on" will be blank; right click the package and select "Install". You may need to select the server to download from by selecting Repository->Change Repository: select "Packages shall be installed from the Internet", click "next" and then select a nearby server. It is possible to set an option so that MiKTeX downloads any missing packages automatically, but I do not recommend this because it will get stuck for ever if the server is not working.

If you create a new style, you need to run texhash from a command window in order to update BibTeX's list of files. You can ulso update it by following: Programs-> MikTex 2.x-> Maintenance(Admin)-> Settings(Admin) and then clicking on "Refresh FNDB".

You can verify that style xxx is visible to MikTex by typing "kpsewhich xxx.bst" from a command window.

## work with .bst file

如果.bst样式不符合要求，可以通过改其内容进行设置。比如在biograph显示article title

``` bst
FUNCTION {format.title}
{ title 
duplicate$ empty$ 'skip$
    { "t" change.case$ }
  if$
%  "title" bibinfo.check
}
```

其中，%表示注释该行。
