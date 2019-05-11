# flash-no-wipe 本项目目前在实验阶段，请勿作死尝试
刷机不双清，我们可以做到的 We can flash rom without wipe.  
注意，如果是加密分区的解密，一般需要格式化，不适用本Project  
非常欢迎各位把各ROM的app包名提交上来，这非常有利于下一步内容的精准适配  
AEX-p-data-system目录下展示了：AEX安卓p的data/system包管理配置文件例子说明

## 目前问题
不小心删除了data目录内容...  
包管理配置问题  
这个问题还在测试，由于作者只有一台手机（日常使用+测试及其难受），所以项目进度非常缓慢

# /data/下应该保留的目录
media    内置储存(sdcard)真实位置  
data     数据/App  
system   包管理位置  

# /data/data/下应该删除的目录，括号为不确定
  - qualcom
  - google
  - xiaomi
  - miui
  - android
  - (goodix)
  - (qti)

## 主要思路
rm掉data分区下不需要的文件，仅<b>保留</b>需要的文件（
-	  /data/app/  非系统应用  
-	  /data/data/ 非系统数据  
-	  /data/app-lib/  非系统部分  
-	  /data/system/  剔除系统应用，仅保留包管理部分  
-         其他待提交  
）

## 原理
由于普通应用程序及其数据在理论上是不会干扰新ROM系统的运行的，所以我们只需要把非系统应用留下，删除/data里和系统相关的文件就行了  
<br>
这样我们完全可以做到免双清而刷入任何ROM（包括但不限于跨安卓版本\跨ROM类型）  
<br>  

# 实验结果（成功，但仍然丢失一些数据，Beta阶段）
理论上 仅保留/data/data/下非系统数据，可以实现:   
AEX(安卓P)刷到MIUI10(安卓P)  
通讯录等备份，使用：中兴的备份助手  

## 可能用到的操作
另外参考方法见本项目下其他文件  
在这里我们用!#代表在adb shell下root用户  
*当然这些操作不过是大概的，不具体的，以后我们需要的是更细致的脚本*  
修改包管理配置文件  
!# ```rm -r /data/data/*android*```  
!# ```rm -r /data/data/*qualcomm*```  
<br>
一般来说，我们可以选择性删除/data区里非用户程序的东西，只留下用户程序的/data/app /data/data(删除到不含系统数据) /data/app-lib  
Ps. /data/system/ 下为系统设置等记录，包含了包管理所需的配置文件，请勿轻易删除，详情请看“文件”条目  

## 文件
目录文件列表请看	`FileList.md`  
/data/system/	 系统配置文件（如安卓里的设置，隐性或显性的设置：如已安装的应用、配置文件等等）该目录下含包管理信息，参见：https://www.jianshu.com/p/f47e45602ad2  
/data/misc/	大部分的WiFI/WLAN VPN信息  

## 使用技巧来帮助改进这个项目
例如：可以把终端/CMD命令执行的结果复制粘贴到log.txt  
然后提取你输入过的命令  
### Linux
$ cat log.txt | grep "#" >> command.txt  
$ cat command.txt  
### Windows
type log.txt | findstr "#" >> command.txt  
