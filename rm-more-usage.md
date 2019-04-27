## rm-more-usage
### 结合find命令使用rm
- （排除）删除除制定文件外的所有文件
	- ``` find /data/ | grep -v "data" | xargs rm -r  ```  
(xargs是传递参数的命令，因为rm用法是 rm <文件名>)
	- ``` rm -r `ls | grep -v "data"`   ```此处是ESC下的符号，而非单引号

# 尽量避免使用rm命令的”f忽略不存在“的参数
