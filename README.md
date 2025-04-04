# <center>LiClock 墨水屏天气时钟
###  **使用烧录工具烧录发行版固件时不要勾选DoNotChgBin选项,可能会导致程序不运行,使用烧录工具烧录后需要按下复位键** 
###  **关于此固件的反馈渠道** 
- QQ群号1040386994
- 在交流群中@我，发送串口报错信息和log.txt文件
- 发送串口报错信息和log.txt文件我的邮箱，jiangzihan192959@outlook.com或本人的邮箱QQ邮箱
###  **关于发行版** 
- 基于2.0.10修改，兼容新旧版硬件，群主原工程地址[https://github.com/diylxy/LiClock](https://github.com/diylxy/LiClock)
- 网页固件烧录地址[https://kanfandelong.github.io/liclock-web-flash/](https://kanfandelong.github.io/liclock-web-flash/)
- 程序中有一个名为F_LOG的宏定义用于将部分日志信息写入日志文件，不需要的可删除后自行重新编译
-  **关于GUI交互的修改**
-  增加英文输入的GUI，englishInput（）函数，及其的依赖函数drawKeyboard（）函数
-  增加drawBMP（）函数，支持BMP文件的绘制（彩色图片使用抖动算法绘制），不支持色彩模式为32位的BMP图片。
-  调整fileDialog（）函数，以便于对文件后缀名的过滤和筛选，
-  **与原版的对比** 
1. 对于电子书，在硬件为新版时，允许使用中键唤醒ESP32并打开菜单，并保留原有的按键逻辑
2. 取消BMP280，AHT20，天气预警，电源，误差补偿，的隐藏
3. 增加了贪吃蛇，文件管理，APP
4. 对设置APP进行了优化，改变了闹钟设定响铃日期的输入方式，编写了关于，在网络设置中新增搜索周围的WIFI，其他设置增加CPU频率设置，SD卡时钟频率设定，长按判断时间设定，以及休眠电压设定（电量不足自动休眠，避免触发电池保护板的保护，导致系统断电，导致DS3231丢失时间），电池电压校准（分为外部仪表校准和芯片eFuse的ADC校准数据），TF加载方式（TF卡的电源供给方式，若使用了TF卡：1.与系统休眠一同断电。2.卸载TF卡（APP不再请求TF的使用）才断电）
5. 优化文件管理，查看文件大小不需要点击（文件大小），改为直接显示在菜单列表中，并在其后增加一个文件最后修改时间，
-  **关于文件管理** 
- 关于退出，随意选择一个文件，在弹出的选项列表中选择退出
- 关于重命名，举例，SD卡的根目录有一个文件a.txt，若要改为b.txt,实际要输入/b.txt,实际修改时有提示（将会考虑修改）
- 关于复制，选择文件夹时，默认就是选择/userdat，（将会考虑根目录的问题），不支持文件系统内复制，仅支持littlefs<-->TF卡（FAT16/FAT32），在littlefs-->TF卡时暂时不考虑剩余空间是否足够的问题（TF卡-->littlefs时会考虑）
-  **关于贪吃蛇** 
- 左键是蛇头逆时针旋转，右键顺时针
- 中键为菜单
- 提高CPU频率会提高运行速度 
### <center>一种兼具易用性与扩展性的多功能墨水屏天气时钟 
![封面](images/封面.png)
## <center>硬件购买注意事项
屏幕型号：`E029A01`  
ESP32：wroom或者其它封装和引脚兼容的模组，建议Flash选大一点  
### **尽量不要买esp32-solo-1，虽然能用，但价格没有任何优势，除非用拆机件**  
其它照着BOM买就行，买之前请认真阅读开源平台下面的DIY注意事项  
### 元器件购买相关说明[请看Wiki](https://github.com/diylxy/LiClock/wiki/%E5%85%83%E5%99%A8%E4%BB%B6%E8%B4%AD%E4%B9%B0)
---
## <center>软件使用说明

### 程序烧录[请看Wiki](https://github.com/diylxy/LiClock/wiki/%E5%9B%BA%E4%BB%B6%E7%83%A7%E5%BD%95)  

### 手动编译固件[请看Wiki](https://github.com/diylxy/LiClock/wiki/%E6%89%8B%E5%8A%A8%E7%BC%96%E8%AF%91%E5%9B%BA%E4%BB%B6)  

---
### 拨轮开关使用说明
|  按键   | 短按功能  | 长按功能 |
|  ----  | ----  | ---- |
| 左键  | 输入数字/时间：当前位-1 | 返回上个App<br/>输入数字/时间：光标左移<br/>电子书：上一页 |
| 右键  | 输入数字/时间：当前位+1 | 输入数字/时间：光标右移<br/>电子书：下一页|
| 中键  | 确认 | 重置输入为默认值 |
---
### 点此查看[Lua App编写规范](src/lua/README.md)  

## <center>Blockly
~~因为现在的Lua语言与Blockly并未完全适配，有些“积木”后续会进行修改，其中包括：~~  

### Blockly使用教程  
暂无，挂一张照片在这吧  
![封面](images/Blockly屏幕截图.png)

## <center>其它
### midi转buz[请看Wiki](https://github.com/diylxy/LiClock/wiki/midi%E8%BD%ACbuz)  

### 图像转lbm[请看Wiki](https://github.com/diylxy/LiClock/wiki/%E5%9B%BE%E5%83%8F%E8%BD%AClbm)  

## <center> 开源协议
### 因为用了彩云天气的API，仅供学习研究，如果需要商用，则不得包含此源代码或由其产生的二进制文件  
源代码开源协议为**GPL-3.0**，允许开源情况下商用，但请标明原作者和工程链接，不得售卖源代码或作为闭源项目发布  
另外，按照GPL-3.0协议要求，由此项目衍生出的代码也需要以GPL3.0开源  
此处的开源指使任何人可以自由且免费地获得、修改**源代码**和（或）**硬件工程源文件**  
