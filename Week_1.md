[TOC]

# 第二章
## Day_01
### 2.2读取图片和输出图片
- **读取图片（定义变量f）**
    - 绝对路径：`f = imread('D:\myimages\chestray.png');`
    - 相对路径（在当前目录）：`f = imread('chestxray.jpg);`
    - 相对路径（当前目录在D盘）：`f = imread('.\myimages\chestxray.png');`

***

- **查询图片大小**
    - 用于读取一个图片的行列数：`size(f)`
    - 直接赋值：`[M, N] = size(f);`
    - 显示数组的附加信息：`whos f` [另一个方法](#another)

***
### 2.3显示图片
1. 基本语法`imshow(f, G)`，f是图像数组，G是图像灰度级数
    - 省略G，默认灰度级数为256，即可以写成`imshow(f)`，即可显示原图
2. 将图像数组中，小于等于low的值变成黑色，大于等于low的值变成白色，余下的以默认级数显示为中等亮度值`imshow(f, [low high])`  
    - 如：左侧为原图，有图G取[5 100]，即低于5为黑色，高于100为白色  
<img src="http://jiantuku-imag.oss-cn-beijing.aliyuncs.com/18-8-9/61477306.jpg" width = "256" height = "256" alt="title" align=center />
<img src="http://jiantuku-imag.oss-cn-beijing.aliyuncs.com/18-8-9/35963954.jpg" width = "338" height = "244" alt="title" align=center />  

***

- **对于图像变化范围不大的图片（图像很黑/图像很白）** 或者 **图像既有正值又有负值？？？**，可以使用`imshow(f, [ ])`语法，这样可将low自动设置为数组f的最小值，而将high自动设置为数组f的最大值。左图为很动态范围不大的图片，右面为经过语法修正的图片。  
<img src="http://pd6km3lkh.bkt.clouddn.com/18-8-9/66362438.jpg" width = "256" height = "256" alt="title" align=center />
<img src="http://pd6km3lkh.bkt.clouddn.com/18-8-9/52982688.jpg" width = "256" height = "256" alt="title" align=center />  

    3. 正常情况下，MATLAB只能一次打开一张图片，在打开第一张图的情况下打开第二张图片，则使用`figure, imshow(g)`或者直接使用`imshow(f), figure, imshow(g)`即可

***
    
### 2.4保存图像
    -  <h6>几条语法</h6>
        1. 语法为`imwrite(f, 'x-ray.tif')`。其中包含**变量名，输出文件名，扩展名**，图像可以为jpg，tif，png等格式  
        2. 语法为`imwrite(f, 'x-ray.jpg', 'quality', q)`，此语法**只能生成jpg图片**，而且压缩范围q的大小是0-100，q越小，图像退化失真越严重，文件越小  
        3. 语法为`imwrite(g, 'x-ray.tif', 'compression', 'parameter', 'resolution', [colres rowres])`，此语法**只适用于生成tif图片**，以下是  
            + `parameter`三个参数的解释
                + `none`：无压缩
                + `packbits`：包比特压缩(非二值图像的默认参数)
                + `ccitt`：ccitt压缩(二值图像的默认参数)  
            
            + `[colres rowres]`参数的解释
                + 由每单位(inch)中的点数从而得出列分辨率和行分辨率
                + `colres`：垂直方向上，每英寸中点数/像素数dpi
                + `rowres`：水平方向上，每英寸中点数/像素数dpi  
                
    -   <h6 id="another">获得图像详细信息</h6>  
        - 语法内容：`imfinfo bubble25.jpg`，也可以用`K=imfinfo('bubble25.jpg')`将信息存到K
        - **计算压缩率，如下图所示**
        ![](http://pd6km3lkh.bkt.clouddn.com/18-8-9/45340612.jpg)
            - 压缩率：`原图像的字节数 / FileSize`
            - 原图像的字节数：`(width * Height * BitDepth) / 8`
            - 该图像的压缩率：`(720 * 688 * 8) / (8 * 13354) = 37.09`
            - **压缩后的好处**：  
                1. 节省存储空间
                2. 单位时间传输的数据量是压缩前的37倍

***

### 2.5 数据类
+ 双精度：double-最常用（8字节）
+ 无符号整数：uint8-常用（1字节）（从设备中读图像）
+ 有符号整数：int8（1字节）
+ 字符：char-Unicode（2字节）（一个字符串长度：1*n字符矩阵）
+ 逻辑：logical（1字节）（0/1）（用于逻辑矩阵的创建）

![](http://jiantuku-imag.oss-cn-beijing.aliyuncs.com/18-8-12/12243764.jpg)

* * *

### 2.6 图像类型
**单色图像**
+ 二值图像
+ 亮度图像

**亮度图像**
+ 含义：将亮度图像的数值矩阵归一化取值，表示亮度
+ 亮度图像像素
    + uint8 -- 范围[0,255]
    + uint16 -- 范围[0,65535]
    + double -- 范围[0,1]

**二值图像**
+ 含义：二值函数的取值只有0和1的逻辑数组，而不是取值为0和1的数值数组
+ 数值数组A -> 逻辑数组B   
    `B = logical(A)`  
    **原则：任何数转成logical形式，非0变为1，0仍为0**
+ 判断一个数组是否为逻辑数组，是返回1，不是返回0  
    `islogical(C)`

***

### 2.7 数据类 与 图像类型 转换
1. **数据类之间的转换**  
`B = data_class_name(A)`

- uint8(A) -> double(B)  
`B = double(A)`

* double(C) -> uint8(D) --需要注意范围  
`D = uint(C)`  
    + 如果矩阵值小于0，转换为0  
    + 矩阵值大于255，转换为255  
    + [0,255]之间的数，去小数取整  

---

2. **图像类 与 类型间 的转换**

    ##### 01.转化为整数数组  
* **格式：logical/uint/double -> uint8/uint16** `g = im2uint8(f)`  
【由0/1、25873、1000.50 转化成 0-255 / 0-65536】   
![](http://jiantuku-imag.oss-cn-beijing.aliyuncs.com/18-8-12/39061666.jpg)  
**注意：**  
`im2uint8`这个函数处理double数据时，将小于0的数转为0，大于1的数转为255，其余的数×255  
**（im2uint8四舍五入，但是uint不四舍五入，直接去掉小数部分）**   

---

##### 02.转化为双精度数组  

* **格式一：logical/uint -> double** `g=im2double(f)`  
![](http://jiantuku-imag.oss-cn-beijing.aliyuncs.com/18-8-12/52084173.jpg)

* **格式二：double -> double** `g = mat2gray(A, [Amin, Amax])`**--可自定义范围转换成[0,1]之间的double类**  
    
**注**：Amin是自定义的阈值下限（低于为0）；Amax是自定义的阈值上限（超出为1）；而这两个数之间的数，则需要除以比例，即：符合条件的A矩阵值(0.1961-Amin)/(Amax-Amim)=0.2402。  
![](http://jiantuku-imag.oss-cn-beijing.aliyuncs.com/18-8-12/4615672.jpg)   
*  **也可以用于整数**
![](http://jiantuku-imag.oss-cn-beijing.aliyuncs.com/18-8-12/60180764.jpg)

![](http://jiantuku-imag.oss-cn-beijing.aliyuncs.com/18-8-12/5432226.jpg)

**注：所有logical数组均可由`im2uint8`、`im2uint16`、`im2double`、`mat2gray`转化成数值矩阵**

---
    
##### 03.转化为逻辑数组

* **格式：uint/double -> logical数组 `g = im2bw(f, T)`**
    * 功能：将亮度图像f转换成二值图像g
    * T为阈值，取值范围为[0,1]内。  
    a为亮度图像的像素点
        *  若a < T，则a点在二值图像中值为0(黑色)
        *  若a ≥ T, 则a点在二值图像中值为1(白色)  
    * 若写成`g = im2bw(f)`，则IPT使用T=0.5为默认值
    
    若如果矩阵为如下情况，输入uint8，将每个值除以255，若大于等于0.5，则输出1；若小于0.5，则输出0：
![](http://jiantuku-imag.oss-cn-beijing.aliyuncs.com/18-8-12/95006543.jpg)
* **数值数组 与 二值数组（黑/白） 相互转化的办法**





![](http://jiantuku-imag.oss-cn-beijing.aliyuncs.com/18-8-12/55063465.jpg)