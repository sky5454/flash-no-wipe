## rm-more-usage
### 结合find命令使用rm
- （排除）删除除制定文件外的所有文件
	- find /data/ | grep -v "data" | xargs rm -f  
(xargs是传递参数的命令，因为rm用法是 rm <文件名>)
	- rm -rf 'ls | grep -v "data"'
