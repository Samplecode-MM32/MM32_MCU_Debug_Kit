# MM32-MCU-Debug-Kit使用说明

MM32 MCU Debug Kit主要是协助MM32用户解决、分析和追溯定位问题的工具，方便MM32 MCU用户快速定位程序进入Hardfault的原因以及脱离IDE对芯片进行出厂初始化操作等。

# 1.目的

## 1.1 快速追溯芯片版本和出货时间等芯片信息；

1、基本信息：

     内核版本
   
     内核型号
   
     UID
   
2、选项字节：

     RDP
   
     nBOOT1
   
     WRP
   
3、代码区块保护：
 
     区块1、2、3、4
   
4、配置：

     Register0
   
     Register1
   
     Register2
   
5、Triming：

     HSI_3.3V
   
     HSI_5V
   
     Temp
   
     Vref
   
6、ISP:

     ISP_DATA0
   
     ISP_DATA1
     
## 1.2 快速定位MCU进hardfault的原因，跟踪显示内核寄存器状态，方便根据内核信息获取程序运行状态，目前仅支持用户编程文件定位问题，针对用户操作RCC等设置问题暂时还没想到方法支持；

## 1.3 针对芯片进行出厂格式化操作，目前支持对所有的芯片进行出厂格式化操作功能；

# 2. 支持芯片
支持全系列MM32 MCU芯片，包含m / n / o / p / q / s 版。

# 3. 支持工具
支持J-link，后续需MM32-LINK驱动开放可以支持。

# 4. 操作说明
第一步：添加驱动和反汇编文件，进入通用设置界面添加驱动文件和反汇编文件，目前先支持J-Link，后面继续支持其它调试器。

JLinkARM.dll是加载Jlink的驱动文件，默认驱动文件下面已经工具的文件夹中，用户也可以选择自己电脑安装J-link驱动路径下面的JLinkARM.dll文件。

反汇编文件是用来自动定位Hardfault故障函数，如果用户不需要，可以不设置。反汇编文件支持MDK和IAR工程，设置方式如下：

MDK反汇编指令：fromelf --text -a -c -o "$L@L.asm" "#L"

IAR反汇编指令：ielfdumparm --code --source $TARGET_PATH$ -o $TARGET_PATH$.dis

第二步连接J-LINK，需要先接上J-LINK，点击菜单栏的Setting子菜单Connect，连接成功会显示图六，下面的状态栏会显示J-LINK connected success、MCU的连接

状态、内核ID。下面的状态栏会显示绿灯，连接失败会显示红灯。

如果没有连接上MCU会显示如图七, 会显示连接JLINK功能，但是没有连接上MCU。

第三步读取芯片信息。

第四步解析Hardfault，点击栈读取和栈解析，窗口会显示ARM内核寄存器信息以及Hardfault出现问题的函数。

第四步恢复出厂设置，需要选择对应的内核版本才能进行恢复出厂设置。

# 5. 信息另存
用户读取信息后直接Crtl + s另存即可将读取的芯片信息另存在工具的文件夹内，只需提供MM32_MCU_INFO.ini文件即可。




