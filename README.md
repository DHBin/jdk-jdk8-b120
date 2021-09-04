# openjdk8-b120

## 编译

我的环境是Ubuntu 20，源中已经没有gcc 4.x了，所以需要添加Ubuntu 16的源

```sh
vim /etc/apt/sources.list.d/ubuntu16.list
```

添加以下内容

```
deb http://mirrors.aliyun.com/ubuntu/ xenial main
deb-src http://mirrors.aliyun.com/ubuntu/ xenial main

deb http://mirrors.aliyun.com/ubuntu/ xenial-updates main
deb-src http://mirrors.aliyun.com/ubuntu/ xenial-updates main

deb http://mirrors.aliyun.com/ubuntu/ xenial universe
deb-src http://mirrors.aliyun.com/ubuntu/ xenial universe
deb http://mirrors.aliyun.com/ubuntu/ xenial-updates universe
deb-src http://mirrors.aliyun.com/ubuntu/ xenial-updates universe

deb http://mirrors.aliyun.com/ubuntu/ xenial-security main
deb-src http://mirrors.aliyun.com/ubuntu/ xenial-security main
deb http://mirrors.aliyun.com/ubuntu/ xenial-security universe
deb-src http://mirrors.aliyun.com/ubuntu/ xenial-security universe
```

```shell
sudo apt update
# 安装需要的依赖，如果还是依赖不足会configure的时候会提示安装，复制命令执行就行
sudo apt install gcc-4.9 g++-4.9 zip libx11-dev libxext-dev libxrender-dev libxtst-dev libxt-dev libcups2-dev libfreetype6-dev libasound2-dev
# configure
bash configure --with-target-bits=64 --with-debug-level=slowdebug ZIP_DEBUGINFO_FILES=0 CC=gcc-4.9 CXX=g++-4.9 --with-freetype-lib=/usr/lib/x86_64-linux-gnu --with-freetype-include=/usr/include/freetype2/
# make
make all DISABLE_HOTSPOT_OS_VERSION_CHECK=OK ZIP_DEBUGINFO_FILES=0
```
