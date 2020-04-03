# LMYUN - KMS

## 介绍

* ##### LMYUN-KMS是一款系统软件激活工具，主要使用KMS服务器对Windows和office（Office建议使用正版账号授权，加入LMYUN，免费获取专业增强版Office365）进行许可认证，解锁更多高级功能
* ##### 服务器不挂的话可以一直激活，过期了就再激活一次（服务器挂了还能继续180天，期间早修好啦）
* ##### 源码可见本文档最下方，保证纯净无毒，[网上](https://baijiahao.baidu.com/s?id=1598179499713784138&wfr=spider&for=pc)有说我可以获取你的控制权，如果你不相信，我可以公开KMS服务器端的源码，确保激活的系统的安全和隐私

## 适用对象
* ##### VOL版本的windows和office

## 服务时间
* ##### 24H，极少更新维护

## 安装

* ##### 下载打包过后的ZIP文件之后解压，在压缩包内有.exe可执行文件，双击或回车打开即可

## 用法

> * ###### 1、进入后会先检测与服务器的连接，若无法连接，则退出
> * ###### 2、进入首页后，可输入命令进行操作
> * ###### 3、常用命令：
> * ###### Auto (先激活Windows，再激活office)
> * ###### AWin (只激活Windows)                                       
> * ###### AO (只激活office)                                          
> * ###### Set (设置KMS服务器)                                          
> * ###### List (列出参考的KMS服务器列表)    
> * ###### CW (查看Windows的激活状况)    
> * ###### UseKey (使用自己的密钥激活系统)    
> * ###### RWK (卸载当前已安装的密钥)    

## 更新日志

#### v1.2稳定版更新内容
> * ##### 启动时检测是否为WindowsNT系统内核
> * ##### 可查看系统激活情况
> * ##### 可使用自己的密钥进行激活
> * ##### 可一键卸载当前已安装的密钥
> * ##### 添加了设置，可自定义服务器地址
> * ##### 添加了图标
#### v1.0稳定版内容
> * ##### [基本功能]使用KMS激活计算机上的Windows系统和office办公软件

## 常见问题

> #### 打开后闪退
> * ##### 无法连接KMS服务器会自动退出，请检测网络连接，可以尝试ping服务器
> `ping kms.lmyun.top`
> ##### 若无法ping通，可以尝试使用网络代理后再ping

> #### 无法激活Windows或office
> * ##### 请检查系统版本或office版本，前往[LMYUN-KMS](https://kms.lmyun.top/)查看是否支持此版本
## Support

> * ##### https://www.lmyun.top/
> * ##### QQ：381003647
> * ##### Mail：laomai0222@lmyun.top或381003647@qq.com

## 感谢

> * ##### 感谢所有在网络上提供KMS服务器的站长

## 版权

> * ##### 2019-2020 © LMYUN. All rights reserved
> * ##### 此项目仅允许免费使用、转载，不得用于商业目的，转载请注明本仓库地址，严禁用于违法用途

## 源码
```
@echo off

@chcp 65001

@mode con lines=30 cols=70

cls

title LMYUN - KMS v1.2

echo.        ------------------------------------------------------

echo.        ^|                     LMYUN - KMS                    ^|

echo.        ------------------------------------------------------

echo.

echo.                               By Laomai

echo.                              Version:1.2

echo.

:CheckNet

echo.%date% %time% Connecting to the LMYUN KMS server

ping kms.lmyun.top -n 1 >nul 2>nul

if %errorlevel%==0 (

set kms=kms.lmyun.top

echo ^|--------------------------------------------------------------------^|

echo.%date% %time% Successfully connected to server!

echo.%date% %time% Loading......

if not "%OS%"=="Windows_NT" echo.                 ERROR! This is not a Windows NT system!

set slmgrPath=%SystemRoot%\system32\slmgr.vbs

cls

goto index

) 

(

echo                                   ERROR

echo                     Unable to connect the KMS server

echo                     Trying to reconnect the server...

goto CheckNet

)

:index

echo.----------------------------------------------------------------------

echo.^|                             LMYUN - KMS                        v1.2^|

echo.^|                        https://kms.lmyun.top                       ^|

echo.----------------------------------------------------------------------

echo.^|                              Command                               ^|

echo.^|Auto (After install Office 2019 , activate Windows and office)      ^|

echo.^|AWin (Activate Windows)                                             ^|

echo.^|AO (Activate Office)                                                ^|

echo.^|Set (Set KMS Server)                                                ^|

echo.^|List (List KMS Server)                                              ^|

echo.----------------------------------------------------------------------

echo.                     Server Addr : %kms%

echo.----------------------------------------------------------------------

goto home

:home

set /p cmd=LMYUN - KMS^>

if "%cmd%"=="Auto" goto Auto

if "%cmd%"=="auto" goto Auto

if "%cmd%"=="AWin" goto Activate Windows

if "%cmd%"=="Awin" goto Activate Windows

if "%cmd%"=="awin" goto Activate Windows 

if "%cmd%"=="AO" goto FreeOffice

if "%cmd%"=="Ao" goto FreeOffice

if "%cmd%"=="ao" goto FreeOffice

if "%cmd%"=="CW" goto Check Windows

if "%cmd%"=="Cw" goto Check Windows

if "%cmd%"=="cw" goto Check Windows

if "%cmd%"=="List" goto List

if "%cmd%"=="list" goto List

if "%cmd%"=="Help" goto Index

if "%cmd%"=="help" goto Index

if "%cmd%"=="Set" goto Set

if "%cmd%"=="set" goto Set

if "%cmd%"=="UseKey" goto UseKey

if "%cmd%"=="useKey" goto UseKey

if "%cmd%"=="Usekey" goto UseKey

if "%cmd%"=="usekey" goto UseKey

goto Home

else 

(

goto Home

)

:UseKey

set /p key=Please inter your key:

cscript /nologo %slmgrPath% /ipk %key%

cscript /nologo %slmgrPath% /ato

:Activate Windows

cd /d "%SystemRoot%\system32"

slmgr /skms %kms%

slmgr /ato

slmgr /xpr

cls

echo.

echo.                             Successfully

echo.

goto Index

:Activate Office

:Office14

echo Activating Office14

cd "C:\Program Files\Microsoft Office\Office14"

@cscript ospp.vbs /sethst:%kms% 

@cscript ospp.vbs /act

@cscript ospp.vbs /dstatus

:Office14(32)

echo Activating Office14(32)

@cd "C:\Program Files (x86)\Microsoft Office\Office14"

@cscript ospp.vbs /sethst:%kms% 

@cscript ospp.vbs /act

@cscript ospp.vbs /dstatus

:Office15

echo Activating Office15

@cd "C:\Program Files\Microsoft Office\Office15"

@cscript ospp.vbs /sethst:%kms% 

@cscript ospp.vbs /act

@cscript ospp.vbs /dstatus

:Office15(32)

echo Activating Office15(32)

@cd "C:\Program Files (x86)\Microsoft Office\Office15"

@cscript ospp.vbs /sethst:%kms% 

@cscript ospp.vbs /act

@cscript ospp.vbs /dstatus

:Office16

echo Activating Office16

@cd "C:\Program Files\Microsoft Office\Office16"

@cscript ospp.vbs /sethst:%kms% 

@cscript ospp.vbs /act

@cscript ospp.vbs /dstatus

:Office16(32)

echo Activating Office16(32)

@cd "C:\Program Files (x86)\Microsoft Office\Office16"

@cscript ospp.vbs /sethst:%kms% 

@cscript ospp.vbs /act

@cscript ospp.vbs /dstatus

@goto index

:Check Office

:Check Windows

slmgr.vbs -dlv

slmgr.vbs -xpr

goto Home

:Remove Windows Key

set /p RWK=Do you sure to unpack the Windows key?(Y/N)

if "%RWK%"=="Y" goto Remove Windows Key Y

if "%RWK%"=="N" goto Home

if "%RWK%"=="y" goto Remove Windows Key Y

if "%RWK%"=="n" goto Home

goto Home

else 

(

goto Remove Windows Key

)

:Remove Windows Key Y

cscript /nologo %slmgrPath% /upk

goto Home

:Remove Office Key

:Auto

cd /d "%SystemRoot%\system32"

slmgr /skms %kms%

slmgr /ato

slmgr /xpr

goto FreeOffice

::Office14

echo Activating Office14

cd "C:\Program Files\Microsoft Office\Office14"

@cscript ospp.vbs /sethst:%kms% 

@cscript ospp.vbs /act

@cscript ospp.vbs /dstatus

::Office14(32)

echo Activating Office14(32)

@cd "C:\Program Files (x86)\Microsoft Office\Office14"

@cscript ospp.vbs /sethst:%kms% 

@cscript ospp.vbs /act

@cscript ospp.vbs /dstatus

::Office15

echo Activating Office15

@cd "C:\Program Files\Microsoft Office\Office15"

@cscript ospp.vbs /sethst:%kms% 

@cscript ospp.vbs /act

@cscript ospp.vbs /dstatus

::Office15(32)

echo Activating Office15(32)

@cd "C:\Program Files (x86)\Microsoft Office\Office15"

@cscript ospp.vbs /sethst:%kms% 

@cscript ospp.vbs /act

@cscript ospp.vbs /dstatus

::Office16

echo Activating Office16

@cd "C:\Program Files\Microsoft Office\Office16"

@cscript ospp.vbs /sethst:%kms% 

@cscript ospp.vbs /act

@cscript ospp.vbs /dstatus

::Office16(32)

echo Activating Office16(32)

@cd "C:\Program Files (x86)\Microsoft Office\Office16"

@cscript ospp.vbs /sethst:%kms% 

@cscript ospp.vbs /act

@cscript ospp.vbs /dstatus

cls

echo.

echo.                      Finish to auto LMYUN - KMS!

echo.

@goto Index

:List

echo.----------------------------------------------------------------------

echo.---------------------------LMYUN - KMS Server-------------------------

echo.----------------------------------------------------------------------

echo.                            kms.lmyun.top 

echo.                               lmyun.tk

echo.----------------------------------------------------------------------

echo.                             Other server

echo.----------------------------------------------------------------------

echo.[Never offline]kms.03k.org

echo.[Online]54.223.212.31

echo.[Online]kms.guowaifuli.com

echo.[Online]mhd.kmdns.net

echo.[Online]xykz.f3322.org

echo.[Online]kms.ddz.red

echo.Goto https://github.com/Laomai0222/lmyun-kms and find other KMS server

echo.----------------------------------------------------------------------

goto Home

:Set

set /p kms=Please enter the server :

echo.%time% Server set : %kms%

goto Index

```