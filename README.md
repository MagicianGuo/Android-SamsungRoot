# 三星Root

此项目主要介绍如何将三星手机Root，以及保存Root所需的关键文件。

**※免责条款：本文仅供参考，刷机不规范导致的问题后果自负。建议刷机前全文看一遍，能够理解的情况下再刷。**

## 一、备份

刷机千万条，备份第一条！刷机忘备份，机主两行泪……

## 二、退出账号

把三星账号、谷歌账号都退出，否则刷机后可能影响开机。

## 三、解锁BL

1、手机打开开发者选项，开启“OEM解锁”；

2、关机，将数据线USB端插入电脑，同时长按手机音量加、音量减，不松手，同时将数据线插入手机，几秒后会显示蓝色界面（三星的刷机模式）；

3、长按音量加，手机会询问是否要解锁BL，再按下音量加确认解锁，之后手机会自动清空数据；

## 四、刷机

### 4.1 刷入最新官方系统

1、使用**Samfirm**（建议用 https://github.com/ivanmeler/SamFirm_Reborn/releases/tag/0.3.6.8 ，这是改版的Samfirm，官方版目前可能无法下载）下载最新的刷机包。地区选CHC（国行），型号和IMEI可以开机自行查看输入；

2、关机，进入前面提到的刷机模式界面，使用**Odin3** （下载地址 https://odindownloader.com/download/odin3-v3-14-4 ）刷机。解压刷机包，将BL、AP、CP正常放入。剩下的两个文件分别是CSC和HOME_CSC，前者刷入后会清空数据而后者不会，选择哪个可根据需要决定。

3、点击确认开始刷机。Odin显示进度条，等到提示“PASS”时代表成功了。

### 4.2 刷入修补后的官方系统

1、开机后，手机下载**三星版面具**（下载地址：https://github.com/fei-ke/Magisk/releases/tag/v26.4-mod 使用此版本是因为国行系统存在验证，用官方版本刷完开机时会卡在激活页面，用此版本可以跳过）。下载后使用此面具修补刷机包的AP文件，修补完成后传回电脑；

2、手机再次进入刷机模式，将刷机包的BL、CP、**修补过的AP**、**HOME_CSC** 刷入手机。

3、刷完后自动开机。开机可能会强制进入recovery模式，点击清空数据即可。

4、开机时如果是激活页面，正常点跳过就行。（如果不能跳过，且toast提示“2002-45”，有可能是因为修补时使用的是官方版面具而不是三星版。不慌，关机重新刷官方系统即可，之后再重新搞）

5、开机后，手机上应该会有个面具，此时手机已经Root了。打开面具，可能提示需要再修复环境，点击修复（如果之后再提示修复那就不用再点了）

6、修复成功，开机后，下载**官方面具**（地址： https://github.com/topjohnwu/Magisk/releases/tag/v27.0 ），替换当前的三星版面具。

7、面具开启Zygisk。

8、如果想要切换德尔塔面具，建议选27001版本，下载完后对其授予Root权限，然后重进，点击面具-直接安装。安装完开机后即可卸载旧的官方面具。

### 4.3 后续系统升级

1、下载新的系统升级包；

2、用手机当前版本的面具修补AP；

3、进入刷机模式，用Odin3将BL、CP、**修补的AP**、**HOME_CSC**刷入手机，这样一来就能在不丢数据的前提下升级系统。（不过在此之前最好还是备份一下，以防万一）

### 4.4 KernelSU方式Root

#### 4.4.1 GKI模式

1、请先用三星版面具刷完Root。

2、刷完之后，到 https://github.com/tiann/KernelSU/releases 页面寻找符合自己内核版本号的文件并下载，格式例如“android13-5.15.123_2023-11-boot.img.gz”。尽量选择版本号一致的，并且安全补丁最接近本机的。

3、下载完解压，里面是镜像文件。使用三星版面具对其修补，修补完重命名为“boot.img”，然后用7zip将其压缩成tar格式，改名为“boot.img.tar”。

4、打开odin3，将tar文件放到AP槽，刷入。

5、刷完后，安装KernelSU管理器，打开后会显示“工作中GKI”，但里面的模块功能无法使用，因为有面具，和它冲突了。此时应当打开面具，卸载里面所有模块，再点击卸载面具-完全卸载，然后会自动重启。

6、重启后，只剩下KernelSU，模块功能可以正常使用了。

#### 4.4.2 LKM模式

注：此模式需要编译内核才能用！还请自行编译或者求助大神……

1、请先将手机刷成KernelSU的GKI模式，方法如上。

2、下载Kernel Flasher。（ https://github.com/capntrips/KernelFlasher/releases/tag/v1.0.0-alpha20 ）

3、对Kernel Flasher授予Root权限，依次点击查看-刷入-刷入AK3压缩包，将编译的内核刷入。注意！刷入完之后，千万别点重启，回到KernelSU，点击直接安装，等安装完再点击重启。

4、重启后，点开KernelSU管理器，会发现已经是LKM模式了。

## 五、常用的模块或应用

1、LSPosed模块（ https://github.com/LSPosed/LSPosed/releases/tag/v1.9.2 ）用于安装常用的Xposed模块功能。下载Zygisk版

2、KnoxPatch模块（ https://github.com/Mesa-Labs-Archive/KnoxPatch/releases/tag/v0.6.8 ）用于让三星软件恢复使用（因为之前解BL锁导致了这些软件无法使用）

3、Shamiko模块（ https://github.com/LSPosed/LSPosed.github.io/releases ）用于对应用隐藏Root（对少数应用无效，例如中国移动）

4、德尔塔（Delta）面具（ https://github.com/HuskyDG/magisk-files/releases ）隐藏Root的能力更强。不过刷此版本时最好选 **R65C33E4F-kitsune (27001)**（ https://github.com/HuskyDG/magisk-files/releases/download/1707294287/app-release.apk ），26.4版本有可能变砖！

5、MiPush模块（指南：https://bzmshang.top/MiPush-Framework_User-Guide ）

6、HMSPush模块（地址： https://github.com/fei-ke/HMSPush/releases/tag/v0.0.27 ）。HMSCore可在酷安或者华为应用商店下载。对应的Magisk模块（ https://github.com/fei-ke/HMSPush/releases/download/v0.0.5/HMSCore-v0.3.zip ）可将HMSCore变为系统应用，效果更强。（补充：HMSCore最高支持版本为6.13.0.322，更高版本无法注册！）