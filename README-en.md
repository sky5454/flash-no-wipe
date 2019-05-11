# Flash-no-wipe (currently in the Beta phase)
- "flash rom but not wipe"  
- Note that in the case of decryption of encrypted partitions, it is generally necessary to format and not apply to this Project  

- You are very welcome to submit each ROM app package name, which is very conducive to the next content of the precise adaptation  
- AEX-p-data-system Directory shows: AEX Android P Data/system Package Management Profile Example Description  

## Current Issues

Package Management configuration Issues  
Project Still being tested, and the project is progressing very slowly because the author has only one mobile phone (daily use + test and it make me uncomfortabled)  

### Directories that should be retained under /data/
| DIR       | Describe                                  |
|-----------|:-----------------------------------------:|
| Media     |  built-in storage (sdcard) Real location  |
| Data      |  App's data                               |
| System    |  Package Management Location              |

### Directories that should be deleted under /data/data/, with parentheses for uncertainty
Qualcom
Google
Xiaomi
Miui
Android
(Goodix)
(QTI)

## Main ideas
RM drop unwanted files under the data partition and keep only the files you need (  
-	  /Data/app/Non-system applications  
-	  /Data/data/Non-system data  
-	  /Data/app-lib/Non-system part  
-     /Data/system/removal system applications, retaining only the Package Management Section  
Other pending submission

）

## Principle

Since the normal application and its data do not theoretically interfere with the operation of the new ROM system, we just need to leave the non-system application behind and delete the/data and system-related files.  
This way we can do it completely free of shuangqing and swipe into any ROM (including but not limited to cross-Android versions  cross-ROM types)

## Experimental results (successful, but still losing some data, Beta phase)
Theoretically, only/data/data/non-system data is retained, which can be achieved:  
AEX (Android P) brushes to MIUI10 (Android P)  

Contacts and other backups, using: ZTE Backup Assistant  


## Actions that may be used
Additional reference methods are provided in other documents under this item
Here we use it! #代表在adb Shell down root user
Of course, these operations are only approximate, not specific, and what we need later is a more detailed script.
Modify Package Management configuration file
!# ```Rm-r/data/data/*android*```
!# ```Rm-r/data/data/*qualcomm*```
In general, we can selectively delete things from non-user programs in the/data area, leaving only the/data/app/data/data of the user program (deleted to do not contain system data)/data/app-lib  

Ps./data/system/for system settings and other records, including package management required configuration files, do not easily delete, please see "file" entry for details  

## File
List of directory files See FileList.md  
/Data/system/system configuration files (such as Android settings, implicit or explicit settings: such as installed apps, configuration files, and so on) include package management information in this directory, see: https://www.jianshu.com/p/f47e45602ad2  
/Data/misc/Most of WiFI/WLAN VPN information  

## Use tips to help improve this project
For example, you can copy and paste the results performed by the terminal/CMD command into log.txt

And extract the commands you've entered.
### Linux
$ cat log.txt | grep "#" >> command.txt  
$ cat command.txt  

### Windows
type log.txt | findstr "#" >> command.txt 
