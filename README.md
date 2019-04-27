# flash-no-wipe
刷机不双清，我们可以做到的 We can flash rom without wipe.
注意，如果是加密分区的解密，一般需要格式化，不适用本Project

# 基本操作/原理
由于普通应用程序和普通应用程序的数据在理论上是不会干扰新ROM系统的运行的，所以我们只需要把非系统应用留下，删除/data里和系统相关的文件就行了  
<br>
这样我们完全可以做到免双清而刷入任何ROM（包括但不限于跨安卓版本\跨ROM类型）  
<br>  

## 可能用到的操作
在这里我们用!#代表在adb shell下root用户  
*当然这些操作不过是大概的，不具体的，以后我们需要的是更细致的脚本*  
/data/ !# ```rm -r /data/system*```  
/data/ !# ```rm -r /data/data/*android*```  
/data/ !# ```rm -r /data/data/*qualcomm*```  
<br>
一般来说，我们可以删除/data区里非用户程序的东西，只留下用户程序的/data/app /data/data(删除到不含系统数据) /data/app-lib  

