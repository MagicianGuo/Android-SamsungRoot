# 三星Root

此项目主要介绍如何将三星手机Root，以及保存Root所需的关键文件。

（免责条款：本文仅供参考，刷机不规范导致的问题后果自负。）

## 一、备份

刷机千万条，备份第一条！刷机忘备份，机主两行泪……

## 二、退出账号

把三星账号、谷歌账号都退出，否则刷机后可能影响开机。

## 三、解锁BL

1、手机打开开发者选项，开启“OEM解锁”；

2、关机，将数据线USB端插入电脑，同时长按手机音量加、音量减，不松手，同时将数据线插入手机，几秒后会显示蓝色界面（三星的刷机模式）；

3、长按音量加，手机会询问是否要解锁BL，再按下音量加确认解锁，之后手机会自动清空数据；

## 四、刷机（刷入最新官方系统）

1、使用Samfirm（建议用 https://github.com/ivanmeler/SamFirm_Reborn/releases/tag/0.3.6.8 ，这是改版的Samfirm，官方版目前可能无法下载）下载最新的刷机包。地区选CHC（国行），型号和IMEI可以开机自行查看输入；

2、关机，进入前面提到的刷机模式界面，使用Odin3 （下载地址 https://odindownloader.com/download/odin3-v3-14-4 ）刷机。解压刷机包，将BL、AP、CP正常放入。剩下的两个文件分别是CSC和HOME_CSC，前者刷入后会清空数据而后者不会，选择哪个可根据需要决定。

3、点击确认开始刷机。Odin显示进度条，等到提示“PASS”时代表成功了。

4、开机后，手机下载三星版面具（下载地址：https://github.com/fei-ke/Magisk/releases/tag/v26.4-mod 使用此版本是因为国行系统存在验证，用官方版本刷完开机时会卡在激活页面，用此版本可以跳过。）。下载后使用此面具修补刷机包的AP文件，修补完成后传回电脑；

5、手机再次进入刷机模式，将刷机包的BL、CP、**修补过的AP**、**HOME_CSC**刷入手机。

6、刷完后自动开机。开机可能会强制进入recovery模式，点击清空数据即可。

7、开机时如果是激活页面，正常点跳过就行。（如果不能跳过，且toast提示“2002-45”，有可能是因为修补时使用的是官方版面具而不是三星版。不慌，关机重新刷官方系统即可，之后再重新搞）

8、开机后，手机上应该会有个面具，此时手机已经Root了。打开面具，可能提示需要再修复环境，点击修复（如果之后再提示修复那就不用再点了）

9、修复成功，开机后，下载官方面具（地址： https://github.com/topjohnwu/Magisk/releases/tag/v27.0 ），替换当前的三星版面具。

10、面具开启Zygisk。

## 五、常用的模块

1、LSPosed模块（ https://github.com/LSPosed/LSPosed/releases/tag/v1.9.2 ）用于安装常用的Xposed模块功能。下载Zygisk版

2、KnoxPatch模块（ https://github.com/Mesa-Labs-Archive/KnoxPatch/releases/tag/v0.6.8 ）用于让三星软件恢复使用（因为之前解BL锁导致了这些软件无法使用）

3、Shamiko模块（ https://github.com/LSPosed/LSPosed.github.io/releases ）用于对应用隐藏Root（对少数应用无效）