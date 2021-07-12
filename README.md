### ~~说明：本EFI不支持BigSur，因为我个人不喜欢所以未来很长一段时间内都不会支持，望谅解。~~
### 我还是太低估自己了  未来将会专心调试适用于Big Sur的OpenCore。Catalina版本引导可以直接使用Clover，但是由于时代更替（bushi）并且本身不完美，我将不再对它修改。

## 2020.11.14更新
### 除了触摸板高级功能不全以外基本可以满足使用了
* 精简无用驱动，提升开机速度
* 引导参数内屏蔽独立显卡以解决睡眠问题，可以正常响应苹果标志-睡眠以及合上盖子睡眠。
* 重做核芯显卡驱动，正常开启H.264以及HEVC加速



#### 补充说明

如果遇到睡眠重新唤醒后：
1. 蓝牙功能消失，系统报告中显示没有蓝牙设备（仅适用于博通情况）
      理论上这个问题应该是已经解决了的。可尝试关机拔下无线网卡，开机进入Windows，关机装上无线网卡。
2. 扬声器无声/耳机无声/声音设备错误/耳机出现严重电流杂音
      仅在运行Studio One过程中出现过该情况。可尝试拔下耳机，睡眠，再次唤醒。
      
      
      
      

# Clover_EFI-For-DELL-G5-5587-适用于戴尔G5 5587的Hackintosh EFI



### 感谢[Len](http://i.pcbeta.com/space-uid-4532202.html)和[黑果小兵](https://daliansky.net)



## [ENGLISH--HERE](https://github.com/Sosueyakiko/Clover_EFI-For-DELL-G5-5587/blob/master/README-ENG.md)



## 机型配置
* CPU：Intel i5-8300H
* 显卡：Intel UHD630
* 显示屏：1920ｘ1080
* 声卡：ALC256（戴尔定制型号ALC3246）
* 无线网卡：使用博通DW1820A/BCM94356_096JNT（再见了，嘤特尔！）

----



## 说明
#### EFI文件夹基于[Len's Dmg](http://bbs.pcbeta.com/viewthread-1858946-1-1.html)，使用“八代笔记本UHD630”配置文件修改而成。可直接引导mac OS 10.15.7，大苏儿没有测试。



### 声卡
1. 不使用VoodooHDA（内建扬声器正确但耳机插孔触点错误，发声频点混乱）。
2. AppleALC注入ID为97（不是ALC256通行的13/56等等常见值）。使用Clover中属性的方式注入。
3. 已知小问题：开机时接入耳机会导致系统识别不到内建扬声器（耳机孔正常）。开机之前记得拔下来就好了。
   
   
   
### 无线网卡
1. 感谢[黑果小兵的教程](https://blog.daliansky.net/DW1820A_BCM94350ZAE-driver-inserts-the-correct-posture.html)。
2. EFI文件夹内已包含蓝牙模块驱动以及WiFi设置，相同网卡的小伙伴可以直接使用。如果遇到Windows蓝屏可考虑屏蔽针脚（只屏蔽教程中说的“后2”即可）。
3. 隔空投送正常。随航接线正常，无线模式iPad会黑屏，不知道是不是个例。接力未测试，理论正常。



### 一些其他的说明&关于这个EFI怎么来的
1. ACPI Error xxxxx method xxxxx Namespace lookup failure xxxxx诸如此类，config.plist里关掉EC0 to EC、H_EC to EC、ECDV to EC三个补丁（即disabled设定为true）。
2. 上一步过后开机会卡ApplePS2TrakPad，其实不是触摸板驱动的锅。/ACPI/Patched/加入SSDT-EC.aml。
3. Clover Configurator内修改使mac系统信息内显示内存会导致声卡消失，原因未知。
4. 补一句TrackPad：这机子是I2C，别指望PS2了，虽然差不多能凑合（这里EFI内仍然用的是PS2，这也算是已知问题之一吧）。
5. （已修复）休眠不正确，唤醒时会卡一会儿然后直接重启。
6. 明明是希捷机械硬盘但是希捷给的读写NTFS的玩意儿不好用啊为什么嗷



----



## 写在最后
不知道什么时候会更新也不知道会不会解决上面提到的问题，因为我不仅菜而且懒。触控板驱动涉及到DSDT我就没做了……

可能有纰漏，见谅。有什么其他bug或者需要在下做的留言就好。
