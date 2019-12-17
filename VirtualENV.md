# virtualenv可以创建一个隔离的Python环境

### 安装

```
pip install virtualenv
```
### 建立一个virtualenv环境，指定环境目录

```
virtualenv /path/to/new/virtual/environment
cd ~/env
```
### 激活virtualenv

```
source bin/activate
source bin/activate.csh
```
### 取消激活

```
deactivate
```
### 删除virtualenv

```
rm -r ~/env
```
### python3.5 以上使用 `venv`
```
python3 -m venv /path/to/new/virtual/environment
```