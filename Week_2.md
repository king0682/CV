<span id="catalog"> </span>

[TOC]

尚未解决的问题
1.位操作
2.分号的几个作用：
	1.取消命令行输入？
	2.一行中写入多条命令

[遇到个同样是做了这本书的笔记的人](https://blog.csdn.net/learngis/article/details/4342102)

# 第二章
## Day_03--8.13
### 2.8数组索引

#### 2.8.1向量索引  
##### 1. 定义向量  
行向量 `v = [1 3 5 7 9]` 或者 `v(1:end)` 。
将行向量转为列向量`w = v.'` 或者 `v(:)`

##### 2. 向量元素的提取 / 分向量的产生
* 单个向量 `v(2)`，结果为3
* 取连续的几个元素
	* 取前三个元素：`v(1:3)` -- 1 3 5
	* 取第2-4个元素：`v(2:4)` -- 3 5 7
	* 从某位置取到最后：`v(3:end)` -- 5 7 9
* 取不连续的元素
	* 从第一个元素开始，每两步取一个元素：`v(1:2:end)`
	* 从最后一个元素开始，倒着取，每两步取一个元素：`v(end:-2:1)`
* 使用linspace产生向量
	* `x = linspace(a, b ,n)` 其中起点为a，终点为b，这个区间以相等间隔产生n个数
* 用一个向量作为取另一个向量值的索引
	* v([1 4 5]) -- 1 7 9  
[<返回主目录>](#catalog)


***

#### 2.8.2 矩阵索引
##### 1. 定义矩阵
`A = [1 2 3; 4 5 6; 7 8 9]`  
**结果如下：**  
![](http://jiantuku-imag.oss-cn-beijing.aliyuncs.com/18-8-13/69504509.jpg)  

##### 2. 子矩阵的提取
* 取矩阵元素：
	* 取矩阵的**某个元素**：`A(2, 3) ` ，结果为6

	* 取矩阵**最后一行，最后一列**元素：`A(end, end)`

	* 取矩阵**最后一行，倒数第三列**的元素：`A(end, end - 2)`

* 取矩阵：
	* 取矩阵**第三列的元素**：`A(:,3)`

	* 取矩阵**第二行的元素**：`A(2,:)`

	* 取矩阵**前二行元素**：`A(1:2,1:3)`

	* 让矩阵**第三列变为0**：先拷贝 `B = A;`，再变0 `B(:,3) = 0`

	* 同样也可以**逆序取矩阵**：`A(2:end, end:-2:1)`，结果为  
	![](http://jiantuku-imag.oss-cn-beijing.aliyuncs.com/18-8-13/40653661.jpg)

	* 用向量索引**提取指定位置的元素**：`A([1 3], [2 3])`，结果为  
	![](http://jiantuku-imag.oss-cn-beijing.aliyuncs.com/18-8-13/93381102.jpg)

	* 用**逻辑寻址法按列依次取矩阵**  
	![](http://jiantuku-imag.oss-cn-beijing.aliyuncs.com/18-8-13/38993775.jpg)

* 将矩阵变为列向量`A(:)`

	注意：  
	1. 所有矩阵在MATLAB中都是以列向量的形式存在的
	![](http://jiantuku-imag.oss-cn-beijing.aliyuncs.com/18-8-13/43523319.jpg)
	2. `A(8)`的结果为列向量第8个值，结果为6
	
* sum函数的使用
	* sum(A)能将二维矩阵A变为每一列加和的行向量形式，结果为  
	![](http://jiantuku-imag.oss-cn-beijing.aliyuncs.com/18-8-13/71113724.jpg)

	* 两个计算矩阵加和的方法
		* `sum(A(:))` 先将矩阵拉成列向量，再对列向量求和
		* `sum(sum(A))` 先将矩阵每列的和计算出来组成行向量，再对行向量求和


[<返回主目录>](#catalog)
***
##### 例2.5：将一幅1024*1024的uint8亮度图像f进行如下操作 

* 1.读入图像  
`f = imread('Fig0206(a)(rose-original).tif');`  
![](http://jiantuku-imag.oss-cn-beijing.aliyuncs.com/18-8-13/47183570.jpg)  
* 2.将图像垂直翻转（行倒数，列不变）  
`fp = f(end:-1:1,:);imshow(fp)`  
![](http://jiantuku-imag.oss-cn-beijing.aliyuncs.com/18-8-13/58759595.jpg)  
* 3.将图像水平翻转（列倒数，行不变）  
`fp = f(:,end:-1:1);imshow(fp)`   
![](http://jiantuku-imag.oss-cn-beijing.aliyuncs.com/18-8-13/69993607.jpg)  
* 4.从大图中截取一个小图，大小为512*512  
`fc = f(257:768, 257:768);imshow(fc)`  
![](http://jiantuku-imag.oss-cn-beijing.aliyuncs.com/18-8-13/61789982.jpg)  
* 5.对图片进行**二次取样--大概是压缩空间和不影响显示的一种方法，每两步一取**  
`fs1 = f(1:2:end, 1:2:end);`   
![](http://jiantuku-imag.oss-cn-beijing.aliyuncs.com/18-8-13/1550266.jpg)   
`fs2 = fs1(1:2:end, 1:2:end);`  
![](http://jiantuku-imag.oss-cn-beijing.aliyuncs.com/18-8-13/78386336.jpg)  
`fs3 = fs2(1:2:end, 1:2:end);`  
![](http://jiantuku-imag.oss-cn-beijing.aliyuncs.com/18-8-13/5765614.jpg)  
`fs4 = fs3(1:2:end, 1:2:end);`  
![](http://jiantuku-imag.oss-cn-beijing.aliyuncs.com/18-8-13/32660857.jpg)  
`imshow(fs*)`  
* 6.裁出图像的一条，并画出其水平扫描线的灰度值变化图  
`fz = f(512, :);imshow(fz)` 或者 `fz = plot(f(size(f, 1)/2, : ))` 
![](http://jiantuku-imag.oss-cn-beijing.aliyuncs.com/18-8-13/5371704.jpg)
`plot(fz)`  
![](http://jiantuku-imag.oss-cn-beijing.aliyuncs.com/18-8-13/14416504.jpg)


[<返回主目录>](#catalog)

***
#### 2.8.3 查询数组维数
* 查询数组的行数 `size(A, 1)` 定义：沿着第一个维数（垂直方向），给出A的大小
* 查询数组的列数 `size(A, 2)` 定义：沿着第二个维数（水平方向），给出A的大小
* 上面的是非常常用的方法：以任何一个维度，提取某个数组的分量，处理彩色图像/多谱段图像，需要将图像堆叠到三维/高维
* 查询一个矩阵的维度：`ndims(A)`，标量的维度也是2，认为是1×1的数组

[<返回主目录>](#catalog)



## Day_05--8.15
### 2.9重要的标准数组
* 生成 M×N 的 double 类矩阵
	* 元素均为0 `zeros(M,N)`
	* 元素均为1 `ones(M,N)` `A = 5*ones(3, 3)`
* 生成 M×N 的 logical 类矩阵
	* 元素均为0 `true(M,N)`
	* 元素均为1 `false(M,N)`
* 生成 M×N 的 随机数矩阵
	* 元素在[0,1]之间，服从均匀分布`rand(M,N)`
	* 元素服从正态分布，均值为0，方差为1`randn(M,N)`
* 生成魔术方阵 -- 用于测试（易生成，元素为整数）`Magic(M)`，大小为M*M
	* “每行、每列、主对角线”元素之和相等

### 2.10M函数编程
#### 2.10.1 M文件
##### 1.M文件组成
![](http://jiantuku-imag.oss-cn-beijing.aliyuncs.com/18-8-16/23149408.jpg)

##### 2.M文件组成详解
1. 函数定义行
* `function [output] = name(inputs)`（其中函数名以字母开头，后跟数字，字母，下划线）
* 如有两个输出`function [s, p] = sumprod(f, g)`
* 如有单个变量输出，可以不使用`[ ]`
* 如没有变量输出，则只需要function，不需要括号和等号
* 用法
	* 在命令行处调用`>> [s, p] = sumprod(f, g)`
	* 用做其他函数的元素（子函数）`y = sum(x);`(单输出无括号)

2. H1行
* H1行是第一个文本行，单个注释，为M文件提供重要摘要，应该尽量描述
* 紧跟函数命令行，与H1行无空行/空格
* 格式 `SUMPROD Computes the sum and product of two images.`
* 当输入`help function_name`时，H1行是最先出现的文本
* 当输入`lookfor keyword`时，会显示出所有含有keyword的H1行

3. 帮助文本
* 提供注释/在线帮助
* 紧跟H1行后，两者间无空行
* 作用：用户输入`help function_name`，MATLAB显示**函数定义行**与**第一个非注释行**之间的**全部注释行**，忽略帮助文本块后的任何注释行（后面含有%的注释行，与帮助文本不是同一部分）

4. 函数体
* 包括
	* 所有执行计算，并且给输出变量赋值的MATLAB代码

##### 3.创建M文件
* 传统方法：写.m文件，下拉菜单new一个
* 使用edit函数，输入`edit sumprod`，打开sumprod.m文件并进行编辑/创建该m文件

[<返回主目录>](#catalog)










## Day06--8.16
#### 2.10.2 运算符
##### 分类
    * 算术运算符 -- 数值计算
    * 关系运算符 -- 数量比较操作数
    * 逻辑运算符 -- 函数AND、OR、NOT

##### 算术运算符
###### 1.基本语法说明
	* 如：`A*B`为矩阵乘法，`A.*B`为数组乘法（对应元素相乘）
	* MATLAB中没有复制数据这个功能：`B = A`实际上是使用不同变量存储相同内容，由此可以增强代码的清晰性和可读性。
![](http://jiantuku-imag.oss-cn-beijing.aliyuncs.com/18-8-17/66796440.jpg)
* IPT工具箱支持整型，MATLAB运算符要求输入double类数据
![](http://jiantuku-imag.oss-cn-beijing.aliyuncs.com/18-8-17/44621306.jpg)
* 关于max和min的语法如下
	* 找出矩阵A每一列的最大值--将A作为列向量处理 `C = max(A)`
	* 找出两个矩阵的最大元素--矩阵由两个最大的矩阵矩阵最大的元素构成，大小与A和B相同`C = max(A, B)`
	* 返回矩阵A某列的最大值`C = max(A, [], dim)`，其中dim=1
	* 返回矩阵A某行的最大值`C = max(A, [], dim)`，其中dim=2
	* 按列找出A的最大值和其索引`[C, I] = max(A)`，`[C, I] = max(A,[],1)`，其中C返回的是最大值，I返回的是最大值的索引，
	* 按行找出A的最大值和其索引`[C, I] = max(A,[],2)`

###### 2.代码实例 -- 定义函数 / 算术运算符
* 需求：编写一个M函数，将两幅输入图片相乘，并输出图像成乘积，乘积最大值，最小值，归一化乘积图像（取值范围[0,1]）
* 思路步骤：
1.找到存放目录，文件名为函数名，`edit improd`
2.编辑m文件
```
function [p, pmax, pmin, pn] = improd(f, g)  %函数定义行
%IMPROD 计算两幅图像的乘积 %H1行
%   [P, PMAX, PMIN, PN] = IMPROD(F, G)输入两幅图像乘积，最大值和最小值，一个归一化成绩矩阵，范围[0, 1] %帮助文本
%   输入图像的大小相同，可以为unit8, unit16,或者double类，输出为double类
%以下为函数体
fd = double(f);% 输出使用double而不是im2double转换为double类图像，输入为uint8，使用im2double会转换到[0,1]
gd = double(g);
p = fd.*gd;
pmax = max(p(:));
pmin = min(p(:));
pn = mat2gray(p);
```
3.执行命令
    + 定义数组 `f = [1 2;3 4];g = [1 2;2 1]`
    + 调用函数 `[p, pmax, pmin, pn] = improd(f, g)`
    + 调用帮助文档 `help improd`


##### 关系运算符
###### 1.基本语法说明
* 前提：两个操作数有相同维数，或者至少其中一个是标量，这样输出的逻辑数组才会对应取0或1（两个标量直接输出0或1）
* 如
![](http://jiantuku-imag.oss-cn-beijing.aliyuncs.com/18-8-17/89442424.jpg)

	* `A == B` 生成逻辑数组，两个数组相等输出1，不相等输出0
	* `A >= B` A >= B数的位置输出1，其他位置输出0

![](http://jiantuku-imag.oss-cn-beijing.aliyuncs.com/18-8-17/90505529.jpg)


##### 逻辑运算符
###### 1.基本语法说明
* 既可作用于逻辑数据，也可作用于数值数据
* 逻辑1/非零数值 = true
* 逻辑0/数值0 = false

![](http://jiantuku-imag.oss-cn-beijing.aliyuncs.com/18-8-17/98537216.jpg)
![](http://jiantuku-imag.oss-cn-beijing.aliyuncs.com/18-8-17/97976520.jpg)

###### 2.案例
* 与
![](http://jiantuku-imag.oss-cn-beijing.aliyuncs.com/18-8-17/1230587.jpg)

* xor，any，all
![](http://jiantuku-imag.oss-cn-beijing.aliyuncs.com/18-8-17/54732224.jpg)

###### 3.用于判断的逻辑函数
![](http://jiantuku-imag.oss-cn-beijing.aliyuncs.com/18-8-17/85067782.jpg)
![](http://jiantuku-imag.oss-cn-beijing.aliyuncs.com/18-8-17/55378896.jpg)

* 案例
`A = [1 2;3 1/0]`
`isfinite(A)`
结果返回：`[1 1;1 0]`

###### 4.重要的常量和变量
![](http://jiantuku-imag.oss-cn-beijing.aliyuncs.com/18-8-17/38096651.jpg)

###### 5.MATLAB关于数的表示（虚数，e）
![](http://jiantuku-imag.oss-cn-beijing.aliyuncs.com/18-8-17/6021725.jpg)
[<返回主目录>](#catalog)


#### 2.10.3 控制流
![](http://jiantuku-imag.oss-cn-beijing.aliyuncs.com/18-8-17/50926453.jpg)



##### 1.if / elseif / else语句
###### 1.格式
* 格式1 if
* 说明：如果if false，则执行end后面的内容
![](http://jiantuku-imag.oss-cn-beijing.aliyuncs.com/18-8-17/9150071.jpg)  


* 格式2 if-elseif-else
* 说明：依次执行，直到执行到end语句
![](http://jiantuku-imag.oss-cn-beijing.aliyuncs.com/18-8-17/14684589.jpg)

###### 2.实例
* 需求：计算一幅图像的平均亮度函数（且只能输入一维和二维数组）
* 思路：将二维数组变成列向量，计算元素和与元素个数，从而计算列向量的均值  
* 代码：
```
function av = average(A)
%AVERAGE 计算平均亮度
	%AV = AVERAGE(A)，计算平均亮度，A必须是一维或者二维的
	%需要检查输入的有效性
if ndims(A) > 2
    error('维数不能超出2')
end
%计算平均值
av = sum(A(:))/length(A(:));
```
* 命令
    * 第一种情况
    `A = magic(3)`
    `average(A)`
    * 第二种情况
    `a(:,:,1) = magic(3)`
    `a(:,:,2) = magic(3)`
    `a(:,:,3) = magic(3)`
    `average(a)`

* 注意：
	* 获取数组元素个数的另一个方法：`n = numel(A)`，从而计算平均值的函数也可以定义为`sv = sum(A(:))/numel(A);`
	* length(A)返回的是矩阵长/宽最大的维数，想要知道矩阵数组中元素的个数，则需要将其拉成向量，即length(A(:))
	* 如果执行到了`error('*')`语句，则函数停止执行，并且输出括号内引号中的信息

##### 2.for循环
###### 1.用法
* 单个循环
![](http://jiantuku-imag.oss-cn-beijing.aliyuncs.com/18-8-17/22579005.jpg)

* 嵌套循环
![](http://jiantuku-imag.oss-cn-beijing.aliyuncs.com/18-8-17/43807497.jpg)
注：
	1. 循环增量可正可负
	2. 忽略循环增量，则其默认值为1
	3. for结尾无需打印；
	4. for循环的end是闭区间，结果包含这个数。其中`for k = 0:-1:-10;`和`for k = 0:0.1:1`这两个都是运行11次
	5. 可以用“向量化代码”替代for循环，以提高执行效率
* 例子
	* 需求：使用for循环将图片分为5的整数倍质量写入磁盘
	* 思路：
		1.用for循环取值，控制输出品质
		2.用imwrite函数输出文件
		2.用sprintf函数控制输出文件名
* 代码
`f = imread('Fig0204(a)(bubbles-q-100jpg).tif');`
```
for q = 0:5:100
filename = sprintf('series_%3d.jpg', q);
imwrite(f, filename, 'quality', q);
end
```
* 注意
	* 以5为质量增加因子
	* sprintf的用法`sprintf('characters1%ndcharacters2', q)`，这是一个字符串连接函数，%nd表示n位十进制数，数值由q确定。characters1--series_，character2--.jpg

###### 2.案例
* 需求：从给定的图像提取子图像
* 思路：
	1.明确图像所要提取的尺寸（起点坐标，子图像尺寸）
	2.一列一列将原图像中每个点f按行提取给新图像坐标（使用for循环）
* 步骤：
	1.制作一个与所求子图大小相等的零矩阵
	2.计算出需要采样的step(记得for循环的特性)
	3.通过for循环将新图片的点与原图相对应的点联系起来

* 代码

```
function s = subim(f, m, n, rx, cy)
%SUBIM 从给定图片中抽取小图
%   子图大小为m*n，左上角坐标为(rx, ry)
s = zeros(m, n);
rowhigh = rx + m - 1;
colhigh = cy + n - 1;
xcount = 0;

for r = rx:rowhigh
    xcount = xcount + 1;%需要让s从(1,1)点开始，而for循环是闭区间，因此不能用rowhigh = rx + m作为for循环结尾，而要用rx+m-1作为结尾
    ycount = 0;
    for c = cy:colhigh
        ycount = ycount + 1;%需要让s从(1,1)点开始
        s(xcount, ycount) = f(r, c);
    end
end
```

* 向量化方法:
<span id='example'> </span>
```
rowhigh = rx + m - 1;
colhigh = cy + n - 1;
s = f(rx:rowhigh, cy:colhigh);
```

调用  
`a = subim(f,100,100,300,500);`
`imshow(a)`


##### 3.while循环
###### 1.用法
* 单个循环
![](http://jiantuku-imag.oss-cn-beijing.aliyuncs.com/18-8-17/36946506.jpg)
* 嵌套使用--内外循环条件均为false时停止
![](http://jiantuku-imag.oss-cn-beijing.aliyuncs.com/18-8-17/49690027.jpg)
![](http://jiantuku-imag.oss-cn-beijing.aliyuncs.com/18-8-17/81611185.jpg)

##### 4.break 和 continue
* break和continue都用于循环，如for和while
* break：跳出当前循环，继续循环外运行 / 跳出内层循环到外层
* continue：结束本次循环，开始下次循环

##### 5.switch--广泛使用
###### 1.格式
![](http://jiantuku-imag.oss-cn-beijing.aliyuncs.com/18-8-17/67996631.jpg)
例子
![](http://jiantuku-imag.oss-cn-beijing.aliyuncs.com/18-8-17/72221941.jpg)



#### 2.10.4 优化代码--MATLAB专为数组运算而设计
##### 1.向量化循环
* 原理
	* 将for和while循环转化为等价的向量/矩阵运算
	* 向量化可以加速甲酸，增强代码可读性
	* 图像处理使用向量化形式很直接
* 使用条件
	* 数组的length很大
	* 程序中使用子程序--for嵌套循环，既然最终都是二维的，不如提前生成出来好了
	* 或者需要for循环从a数到b，这样就不用定义2倍变量了[example](#example)
* 关于二维函数的评估 
* 语句
	* `r=[0,1,2] ; c=[0 1]`
	* `[C, R] = meshgrid(c, r)`
* 作用：将向量变成二维数组
* 注意
	* 输出的矩阵C和R均为length(r)×length(c)维矩阵，如C为将向量c纵向列三行，而R为向量r横向列两行
	* MATLAB索引（包括meshgrid生成的网格索引）均从1开始，不能有0索引`h(1,1) = R(1,1)^2 + C(1,1)^2` `h = R.^2 + C.^2`
![](http://jiantuku-imag.oss-cn-beijing.aliyuncs.com/18-8-18/20744296.jpg)

* 例子
* 1.通过一个函数生成图像，对比for与向量化代码实现用时之比![](http://jiantuku-imag.oss-cn-beijing.aliyuncs.com/18-8-18/56442231.jpg)

* 思路
	1.确定参数：A,u0,x,v,y
	2.确定返回值：for图像f,向量化代码图像g，两者用时rt
	3.计时函数tic起始，toc结束（附带时间）
	4.x,y输入取值范围是一个矩形，因此可以按照图像的方法找输出，即按列一行行向前扫描。（如何定义循环，一列一列横着走）
	5.向量化首先生成网格，然后输入网格直接计算
	6.通过计算两者时间比，从而得出效率

```
function [rt, f, g] = twodsin(A, u0, v0, M, N)
%TWODSIN 循环和向量化的对比运算
%   该比较基于执行函数f(x, y) = Asin(u0x + v0y) for x = 0, 1, 2,...,M-1和 y = 0, 1,
%   2,...,N-1，函数输入为M和N
%执行for循环
tic %计时开始
for r = 1:M %循环索引从1开始，其中r和c既作为循环索引，又作为变量取值范围
    u0x = u0*(r-1);
    for c = 1:N
        v0y = v0*(c-1);
        f(r, c) = A*sin(u0x + v0y);
    end
end
t1 = toc;%计时结束

%执行向量化--实质：生成一个网格，直接运算，而不用像for循环那样一个一个往里面输入
tic
r = 0:M - 1;
c = 0:N - 1;
[C, R] = meshgrid(c, r);
g = A*sin(u0*R + v0*C);
t2 = toc

%计算两个时间的比率
rt = t1/(t2 + eps);%eps接近0，不等于0，以防t2为0
```


* 执行运算的命令
`[rt, f, g] = twodsin(1, 1/(4*pi),1/(4*pi),512,512);`
提取`rt`发现相差十几倍
使用`g = mat2gray(g)`将生成的图像转为可视格式

* 正弦图像结果
![](http://jiantuku-imag.oss-cn-beijing.aliyuncs.com/18-8-18/63677546.jpg)


##### 2.预分配数组
* 原理：处理数值/逻辑数组时，创建一个0数组，维数与所要处理数据相同
* 格式：
	* 想处理两幅1024 × 1024像素的图像
	* 预分配：`f = zeros(1024); g = zeros(1024);`
* 作用
	* 处理大数组时：预分配减少DRAM在分配和去分配的时候产生碎片
	* 物理存储器没有足够连续空间容纳一个较大变量，预分配数组就可以提前保留足够存储空间，防止不连续的情况

#### 2.10.5 交互I/O
* 输出语法：`disp(`输出屏幕内容`)`
* 输入语法：`t = input('message')` 输入message，而输出t
	* 其中语法input有以下几种用法
	* 语法`t = input('message')`，输入的常用数据类型：
		* 单个数字
		* 字符串：用\` \`括起来
		* 向量：用[ ]括起，内容用，或者空格分开
		* 矩阵：用[ ]扩起，行与行之间;隔开
    * 语法`t = input('message', 's')`
    	* 注意：这个函数最终输出的是字符串，可以用，或者空格分隔输入
    	* 如果输入的是一个矩阵，则会出现下面的情况
    	![](http://jiantuku-imag.oss-cn-beijing.aliyuncs.com/18-8-18/63491250.jpg)
    	* 通过input输入的数组实则为字符串，若输入一堆数字，则需要将其从字符串转化成数组`n = str2num(t)`
    	* 查看数据类型`class(n)` 查看数据大小`size(n)`
		![](http://jiantuku-imag.oss-cn-beijing.aliyuncs.com/18-8-18/18301920.jpg)
* 混合输入字符串和数值，先全部按照字符串读入，再用strread按照数据类型进行分类
	* 标准函数`[a, b, c, ...] = strread(cstr, 'format', 'param', 'value')`，指定format与param和value
		* 如果要提取数据，则使用format-%f%q%q、param-delimiter、value-,
		![](http://jiantuku-imag.oss-cn-beijing.aliyuncs.com/18-8-18/60914860.jpg)
        * 注意单位数组与字符数组的区别
* 字符串比较函数strcmp()  
`strcmp(‘char1’,‘char2’)`:相同返回1，不同返回0（注意：如果两个字符串大小不一致也会为0）
* 修改字符串大小写的方法
	* `param = lower(param)` 全部变为小写
	* `param = upper(param)` 全部变为大写

#### 2.10.6 单元数组、结构
##### 数组结构
* 混合类变量构成 `c = {'gauss', [1 0; 0 1], 3}`，其中这些变量指向参量的副本，而不是参量本身

* 提取数组元素用`c(n)`
![](http://jiantuku-imag.oss-cn-beijing.aliyuncs.com/18-8-18/86886833.jpg)

##### 结构--用法：函数有多个需要用户解释的输出，增强可读性
* 同样允许混合类，但是结构由域来寻址
* 使用方法
	1. 定义域
	```
    S.char_string = 'gauss';
    S.matrix = [1 0; 0 1];
    S.scalar = 3;
    ```
	2. 提取域
	`S.matrix`


# 第三章
## Day07--8.17

### 3.2 亮度变换函数
#### 3.2.1 imadjust函数
[参考链接]('http://note.youdao.com/noteshare?id=968ee5df454b96ce5e2f89f2d151ec14')
##### 1.基本公式 
`g = imsdjust(f, [low_in high_in], [low_out high_out], gamma)`

1. gamma参数
![](http://jiantuku-imag.oss-cn-beijing.aliyuncs.com/18-8-16/9394790.jpg)

![](http://jiantuku-imag.oss-cn-beijing.aliyuncs.com/18-8-16/3674263.jpg)

![](http://jiantuku-imag.oss-cn-beijing.aliyuncs.com/18-8-16/2538288.jpg)

* 常识：黑色为0，白色为1
* gamma是斜率，关于gamma的取值问题
	* gamma的默认值为1，其为线性映射
	* gamma<1时
		* 整体数值增加，亮度升
		* low_in(靠近0)这端的数值斜率拉升明显，变化范围拉伸（high_in一段变化范围压缩），这个区间元素亮度变化明显
	* gamma>1时
		* 整体数值减小，亮度降
		* high_in(靠近1)这端的数值斜率拉升明显，变化范围拉伸（low_in一段变化范围压缩），这个区间元素亮度变化明显

2. [low_in high_in],[low_out high_out]参数
* 原理：确定一个区间[low_in high_in]，图像中低于low_in的像素在输出时取值low_out；高于high_in的像素输出时取值high_out，其余的保持不变（对应像素是(0,1)*255）
* 使用参数的几种变换
	* 负片变换
		* `g = imadjust(f, [0 1], [1 0]);`
		* 其他负片操作 
			* `g = imcomplement(f)`
			* 自动确定阈值，完成对比度拉伸`g = imadjust（f，stretchlim（f），[ ]）;`
	* 仅变换gamma `g = imadjust(f, [ ], [ ], 0.6);` （注：[ ]代表默认为[0 1]）
	* 降低对比度 `g = imadjust(f, [0 1], [0.3 0.7])`
![](http://jiantuku-imag.oss-cn-beijing.aliyuncs.com/18-8-16/89349114.jpg)
	* 提高对比度 `g = imadjust(f, [0.3 0.6], [0 1])`
![](http://jiantuku-imag.oss-cn-beijing.aliyuncs.com/18-8-16/96609372.jpg)
* 定量总结了一个关于输出亮度的公式（有点乱）
![](http://jiantuku-imag.oss-cn-beijing.aliyuncs.com/18-8-16/66216315.jpg)
[<返回主目录>](#catalog)

