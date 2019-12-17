## 【第1周】Python基本语法元素

### 1.0 课程导学

### 1.1 程序设计基本方法

解释和编译：静态语言，脚本语言

编程基本方法IPO：Input，Process，Output

### 1.2 Python开发环境配置

**python有两种编程方式：交互式和文件式**

文件式是编程的主要方式，交互式用于练习。

### 1.3 实例1: 温度转换

**已知：**

- C表示摄氏温度，F表示华氏温度
- C = (F-32)/1.8
- F = C*1.8+32

```python
# -*- coding: utf-8 -*-
#TemConvert.py

TempStr = input("请输入带有符号的温度值，C表示摄氏度，F表示华氏度，如“24C” ：")
if TempStr[-1] in ['F', 'f']:
    C = (eval(TempStr[0:-1]) - 32)/1.8
    print("华氏温度{}，转换为摄氏温度为{:.2f}C".format(TempStr, C))
elif TempStr[-1] in ['C', 'c']:
    F = 1.8*eval(TempStr[0:-1]) + 32
    print("摄氏温度{}，转换为摄氏温度为{:.2f}F".format(TempStr, F))
else:
    print("格式错误")
```



### 1.4 Python程序语法元素分析

缩进结构，注释，字符串，变量命名，赋值语句，分支语句（if else），函数

输入，输出

### 第1周 作业及学习资料



## 【第2周】Python基本图形绘制

### 2.0 课程导学



### 2.1 深入理解Python语言

机器语言，汇编语言，高级语言，超级语言

### 2.2 实例2: Python蟒蛇绘制

```python
# -*- coding: utf-8 -*-
#PythonDraw.py

import turtle
turtle.setup(650, 350, 200, 200)
turtle.penup()
turtle.fd(-250)
turtle.pendown()
turtle.pensize(25)
turtle.pencolor("purple")
turtle.seth(-40)
for i in range(4):
    turtle.circle(40, 80)
    turtle.circle(-40, 80)
turtle.circle(40, 80/2)
turtle.fd(40)
turtle.circle(16, 180)
turtle.fd(40 * 2/3)
turtle.done()
```

### 2.3 模块1: turtle库的使用

https://docs.python.org/3/library/turtle.html?

### 2.4 turtle程序语法元素分析



### 第2周 作业及学习资料



## 【第3周】基本数据类型

### 3.0 课程导学



### 3.1 数字类型及操作

#### 整数int

十进制，二进制(0b)，八进制(0o)，十六进制(0x)

#### 浮点数float

取值范围，精度限制

运算存在不确定尾数，使用round()

科学计数法（3e4）

#### 数值操作

```
加+ 减- 乘* 除/ 整除// 取余% 幂** pow(a,b)
+= *=
```



### 3.2 实例3: 天天向上的力量

while, for, if同时使用

### 3.3 字符串类型及操作

字符串的表示：单引号或双引号表示单行字符串，三单引号或三双引号表示多行字符串

```
'abc'
"abc"
''' a
    b
	c'''
	
""" a
	b
	c"""
```

字符串切片

```
"zifuchuan"[start:end:step]
```

转义符"\"

```
\b回退，\n换行（光标移动到下行首）， \r回车（光标移动到本行首）
```

字符串操作符

```
x + y			# 连接字符串
x * n 或 n * x	# 复制连接字符串
x in y			# 判断字符串的包含关系，返回True or False
```

常用字符串函数

```
len(x)		#字符串长度
str(x)		#任意数据类型转换为字符串
eval(x)		#字符串类型的数据转换为数字类型
oct(x)		#十进制数字的八进制字符串形式
hex(x)		#十进制数字的十六进制字符串形式
chr(u)		#返回unicode编码对应的字符
ord(x)		#返回x字符对应的unicode编码
```

字符串处理方法

```
str.slower, str.upper
str.split(sep=None)
str.count(sub)
str.replace(old, new)
str.center(width[, fillchar])
str.strip(chars)
str.join(iter)
```

"{}".format()方法

| 位置参数 |    ：    |   填充   |     对齐      |   宽度   |  <,><.精度><类型>   |
| :------: | :------: | :------: | :-----------: | :------: | :-----------------: |
| 顺序匹配 | 引导符号 | 单个字符 | <左 >右 ^居中 | 输出宽度 | 逗号”,“指千位分隔符 |

```
"{[位置]:[填充][对齐][宽度][<,><.精度><类型>]}".format(*args)
```

还可以使用关键字参数

```
'{name},{age}'.format(age=18,name='xiaoqiang')
```

老版的%操作符

```
%[(name)][flags][width].[precision]typecode
```



### 3.4 模块2: time库的使用

时间函数

```
time.time()
time.localtime(time.time())
time.ctime()
time.gmtime()
```

时间格式化

```python
strftime(tpl, ts)
>>> time.strftime("%y-%m-%d %H:%M:%S", time.time())
'19-08-05 03:23:54'
>>> t=time.localtime(time.time())
>>> t
time.struct_time(tm_year=2019, tm_mon=8, tm_mday=5, tm_hour=11, tm_min=32, tm_sec=59, tm_wday=0, tm_yday=217, tm_isdst=0)
>>> time.strftime("%y-%m-%d %H:%M:%S", t)
'19-08-05 11:32:59'
>>> time.strftime("%Y-%m-%d %H:%M:%S", t)
'2019-08-05 11:32:59'
```

```
strptime(tpl, ts)
```

引申：datetime库



### 3.5 实例4: 文本进度条

**简单输出文本进度条**

```python
#TextProBarV1.py
import time
scale = 10
print("-----执行开始-----")
for i in range(scale+1):
    a = "*" * i
    b = "." * (scale - i)
    c = (i/scale) * 100
    print("{:^3.0f}%[{}->{}]".format(c,a,b))
    time.sleep(0.1)
print("-----执行结束-----")
```

**单行刷新文本进度条**

Python 3.x的print函数
`\r` 表示将光标的位置回退到本行的开头位置
`\b` 表示将光标的位置回退一位

`end`定义换行符

```python
#TextProBarV2.py
import time
for i in range(101):
    print("\r{:^3.0f}".format(i), end="")
    time.sleep(0.1)
```

**完整版进度条**

```python
#TextProBarV3.py
# coding:utf-8
import time
scale = 100
print("执行开始".center(scale//2, "-"))
start = time.perf_counter()
for i in range(scale+1):
    a = "=" * i
    b = "-" * (scale - i)
    c = i/scale * 100
    dur = time.perf_counter() - start
    print("\r{:^3.0f}%[{}->{}]{:.2f}s".format(c, a, b, dur), end="")
    time.sleep(0.1)
print("\n"+"执行结束".center(scale//2, "-"))
```



### 第3周 作业及学习资料



### 【第4周】程序的控制结构

4.0 课程导学

4.1 程序的分支结构

4.2 实例5: 身体质量指数BMI

4.3 程序的循环结构

**if语句**

**for循环**

**while循环**

**else的使用**

**try...except...else**

4.4 模块3: random库的使用

4.5 实例6: 圆周率的计算

第4周 作业及学习资料

### 【第5周】函数和代码复用

5.0 课程导学

5.1 函数的定义与使用

5.2 实例7: 七段数码管绘制

5.3 代码复用与函数递归

5.4 模块4: PyInstaller库的使用

5.5 实例8: 科赫雪花小包裹

第5周 作业及学习资料

### 【第6周】组合数据类型

6.0 课程导学

6.1 集合类型及操作

6.2 序列类型及操作

6.3 实例9: 基本统计值计算

6.4 字典类型及操作

6.5 模块5: jieba库的使用

6.6 实例10: 文本词频统计

第6周 作业及学习资料

### 【第7周】文件和数据格式化

7.0 课程导学

7.1 文件的使用

7.2 实例11: 自动轨迹绘制

7.3 一维数据的格式化和处理

7.4 二维数据的格式化和处理

7.5 模块6: wordcloud库的使用

7.6 实例12: 政府工作报告词云

第7周 作业及学习资料

### 【第8周】程序设计方法学

8.0 课程导学

8.1 实例13: 体育竞技分析

8.2 Python程序设计思维

8.3 Python第三方库安装

8.4 模块7: os库的使用

8.5 实例14: 第三方库安装脚本

第8周 作业及学习资料

### 【第9周】Python计算生态概览

9.0 课程导学

9.1 从数据处理到人工智能

9.2 实例15: 霍兰德人格分析雷达图

9.3 从Web解析到网络空间

9.4 从人机交互到艺术设计

9.5 实例16: 玫瑰花绘制

第9周 作业及学习资料

全课程总结与学习展望

全课程总结与学习展望