1. [Ubuntu 以root权限打开文件管理器](#1)
2. [Ubuntu 创建应用启动器](#2)
3. [Ubuntu 修复搜狗拼音](#3)
4. [Ubuntu 清除不用的包](#4)
5. [Ubuntu 自动修复依赖](#5)
6. [Ubuntu 编辑环境变量](#6)
7. [Ubuntu 安装nodejs](#7)
8. [Ubuntu 修复npm全局安装失败](#8)
9. [Ubuntu 修复双系统下导致Windows时间错误](#9)
10. [Ubuntu WPS“系统缺失字体”问题](#10)
11. [Ubuntu 安装shadowsocks-qt5](#11)
12. [Ubuntu 修复sublime无法输入中文](#12)
13. [Ubuntu 修改系统字体](#13)
14. [Ubuntu 配置Android环境](#14)

---
#### <span id="1">以root权限打开文件管理器:</span>

	sudo nautilus
---
#### <span id="2">创建应用启动器:</span>

	cd /usr/share/applications
	sudo gedit xxx.desktop
 在xxx.desktop中输入
 
	[Desktop Entry]
	Version=1.0
	Name=xxx
	Exec=/home/username/xxx.sh（这个是启动程序需要执行的文件路径名）
	Terminal=false
	Icon=/home/username/xxx.png（这个是图标）
	Type=Application
	Categories=Development
---
#### <span id="3">修复搜狗拼音:</span>

	刪除~/.config 文件夾下的關於搜狗的三個文件夾
---
#### <span id="4">清除不用的包:</span>

	sudo apt-get autoclean
---
#### <span id="5">自动修复依赖:</span>

	sudo apt-get install -f
---
#### <span id="6">编辑环境变量:</span>

	sudo gedit /etc/environment
	source /etc/environment
---
#### <span id="7">安装nodejs:</span>
1.下载并解压 node-v-x-linux-x64.tar.xz

	tar -xJf node-v-x-linux-x64.tar.xz
2.移到通用的软件安装目录 /opt/ 

	sudo mv node-v-x-linux-x64 /opt/
3.安装 npm 和 node 命令到系统命令

	sudo ln -s /opt/node-v-x-linux-x64/bin/node /usr/local/bin/node
	sudo ln -s /opt/node-v-x-linux-x64/bin/npm /usr/local/bin/npm
4.验证

	node -v
	npm -v
---
#### <span id="8">修复npm全局安装失败:</span>
1.运行

	npm root -g
期望 "/usr/local" ，否则运行

	npm config set prefix /usr/local
期望 “/usr/local/lib/node_modules”

---
#### <span id="9">修复双系统下导致Windows时间错误:</span>
1.首先在Ubuntu下更新一下时间，保证当前时间是正确的，然后运行一下命令

	sudo apt-get install ntpdate
	sudo ntpdate time.windows.com
2.然后将时间更新到硬件上：

	sudo hwclock --localtime --systohc
---
#### <span id="10">WPS“系统缺失字体”问题:</span>
1.下载缺失的字体文件，然后复制到Linux系统中的/usr/share/fonts文件夹中

国外下载地址：<https://www.dropbox.com/s/lfy4hvq95ilwyw5/wps_symbol_fonts.zip>
	国内下载地址：<https://pan.baidu.com/s/1eS6xIzo>
（上述数据来源网络，侵删）

2.下载完成后，解压得到字体文件
3.在 /usr/share/fonts 中新建文件夹 如：wpsFonts，然后将（2）得到的字体文件拷贝进去：
4.进入 /usr/share/fonts/wpsFonts

	cd /usr/share/fonts/wpsFonts
5.执行以下命令,生成字体的索引信息：

	sudo mkfontscale
	sudo mkfontdir
6.运行fc-cache命令更新字体缓存：

	sudo fc-cache
重启wps即可，字体缺失的提示不再出现。

---
#### <span id="11">安装shadowsocks-qt5:</span>
分别运行以下三行命令：

	sudo add-apt-repository ppa:hzwhuang/ss-qt5
	sudo apt-get update
	sudo apt-get install shadowsocks-qt5
---
#### <span id="12">修复sublime无法输入中文:</span>
<https://jingyan.baidu.com/article/e9fb46e17ba76f7521f766d5.html>
<https://jingyan.baidu.com/article/f3ad7d0ff8731609c3345b3b.html>

---
#### <span id="13">修改系统字体:</span>
<https://my.oschina.net/itblog/blog/278566>

---
#### <a name="14">配置Android环境:</a>
<http://blog.csdn.net/u013068377/article/details/47449955>