# Python.h：没有那个文件或目录

netifaces.c:1:20: 致命错误：Python.h：没有那个文件或目录

include <Python.h>

​				^

编译中断。

error: command 'gcc' failed with exit status 1



解决办法：安装Python的头文件和静态库包

$ yum install python-devel

$ apt-get install python-dev