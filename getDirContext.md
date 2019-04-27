## 从手机获得目录下的所有文件， 并推送到电脑
!#表示在adb shell下
 $表示PC端普通Linux用户
```adb
!# tar -cvf /data/system/data-sys.tar /data/system
 $ adb pull /data/system/data-sys.tar ./Documents/

```

