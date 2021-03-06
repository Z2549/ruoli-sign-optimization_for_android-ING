# 在安卓端运行基于若离的仓库发展的今日校园自动签到

------

在安卓端部署基本与本地部署相同

请自行准备ruoli-sign-optimization程序文件

!!!!!!!!!!请注意!!!!!!!!!!

请不要使用已经安装过依赖的程序文件,请务必使用未安装依赖的程序文件

!!!!!!!!!!请注意!!!!!!!!!!

可使用提供的已安装依赖的包(config.yml为空)

-----
[TOC]

  一. 配置脚本环境
 
    1.安装 Termux
    2.前置
    3.复制文件
    4.安装依赖
    5.config配置
  二. 自动执行脚本
  
    1.python 定时脚本实现
    2.tasker 或 MacroDroid 实现自启Termux并执行脚本
    3.Termux 自启脚本
  三. 自动充断电
  
    1.有 root
    2.无 root
-----


## 一 . 配置脚本环境

### 1.安装 Termux

下载地址:  https://f-droid.org/repo/com.termux_118.apk

(**引用自国光 Termux高级终端安装使用配置教程**: https://www.sqlsec.com/2018/05/termux.html)

(lanzou : https://zjyl.lanzoum.com/iIxZq07ajphe

baidu : https://pan.baidu.com/s/1NxsOWcRh2mKRob1q1OF_9A?pwd=jrxy
提取码：jrxy)

### 2.前置

2.1 需要换源在终端中执行：

```bash
sed -i 's@^\(deb.*stable main\)$@#\1\ndeb https://mirrors.tuna.tsinghua.edu.cn/termux/termux-packages-24 stable main@' $PREFIX/etc/apt/sources.list

sed -i 's@^\(deb.*games stable\)$@#\1\ndeb https://mirrors.tuna.tsinghua.edu.cn/termux/game-packages-24 games stable@' $PREFIX/etc/apt/sources.list.d/game.list

sed -i 's@^\(deb.*science stable\)$@#\1\ndeb https://mirrors.tuna.tsinghua.edu.cn/termux/science-packages-24 science stable@' $PREFIX/etc/apt/sources.list.d/science.list

pkg update
```

2.2 本行命令是请求存储权限，请允许。

```bash
termux-setup-storage

```

2.3 安装python3

```bash
pkg install python -y
```

2.4 升级pip

```bash
# 升级 pip3
python -m pip install --upgrade pip -i https://pypi.tuna.tsinghua.edu.cn/simple some-package
```

**(引用自国光Termux安装教程)**

### 3.复制文件

等待执行完毕后，在termux里将下载的程序文件复制到终端的根目录

```bash
cp -r storage/程序目录 ~
```

(storage是存储空间目录)

**(例如: cp -r storage/downloads/ruoli-sign-optimization ~)**

**(在自用时发现如果在存储目录里会有依赖混用的错误--仅测试一次)**

### 4.安装依赖

```
pip3 install -r requirements.txt -t ./ -i https://mirrors.aliyun.com/pypi/simple
```

**(引自若离)**

### 5.config配置

不再赘述，详细前往若离md查看

------

至此若无其他错误，则脚本已可运行，与本地部署运行方式一致

在文件目录下执行 python index.py

-----

## 二. 自动执行脚本

### 1.python 定时脚本实现

### 2.tasker 或 MacroDroid 实现自启Termux并执行脚本

### 3.Termux 自启脚本

```bash
vim ~/.bashrc
```

添加termux开机运行脚本

-----

## 三. 自动充断电

### 1.有 root

可依靠scene之类软件实现

**未测试！**

### 2.未 root

tasker 或 MacroDroid

**未测试！**

-----

