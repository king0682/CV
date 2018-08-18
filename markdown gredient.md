# 一级标题
## 二级标题
### 三级标题
#### 四级标题
##### 五级标题
###### 六级标题


一级标题（=个数不限）
========

二级标题（-个数不限）
--------

***

## 无序列表
- 文本1
- 文本2

## 无序列表
* 文本1
* 文本2

## 无序列表
+ 文本1
+ 文本2

## 有序列表
1. 文本1
2. 文本2

***

## 插入链接
### 行内式
* 绝对路径
[谷歌](http://google.cn)

* 相对路径
[About](/about/)

### 参考式
这是[谷歌][1];  
这是[百度][A];  
这是[雅虎][.];  
这是[必应][];  

[1]:https://www.google.hk/  "title"  
[a]:https://www.baidu.com/   "莆田欢迎您"
[.]:https://www.yahoo.com/  "你们还记得我么"
[必应]:https://www.bing.com  "没有谷歌还可以搜我啊"

  
[huihut][Z]

[Z]: https://huihut.github.io/


[Google][]

[Google]: http://google.com/

***


## 插入图片
* 绝对路径(行内式)  
![简书](https://cdn2.jianshu.io/assets/web/nav-logo-4c7bbafe27adc892f3046e6978459bac.png)

* 绝对路径(参考式)  
![Google][v]

[v]:https://cdn2.jianshu.io/assets/web/nav-logo-4c7bbafe27adc892f3046e6978459bac.png

* 相对路径  
![这里没有图](a.png)

* 指定图片宽高  
<img src="https://cdn2.jianshu.io/assets/web/nav-logo-4c7bbafe27adc892f3046e6978459bac.png" width = "100" height = "100" alt="title" align=center />

* 指定居中
<div  align="center">    
<img src="https://cdn2.jianshu.io/assets/web/nav-logo-4c7bbafe27adc892f3046e6978459bac.png" width = "100" height = "100" alt="title" align=center />
</div>

***

## 引用
> 一盏灯， 一片昏黄； 一简书， 一杯淡茶。 守着那一份淡定， 品读属于自己的寂寞。 保持淡定， 才能欣赏到最美丽的风景！ 保持淡定， 人生从此不再寂寞。

## 诗歌的引用？？？怎么换行
> 朝辞白帝彩云间  
> 千里江陵一日还  
> 两岸猿声啼不住  
> 轻舟已过万重山

## 多引用
>> hello
>>> hello
>>>> hello
>>>>> hello
>>>>>> hello
>>>>>>> hello
>>>>>>>> hello
>>>>>>>>> hello
>>>>>>>>>> hello
>>>>>>>>>>> hello
>>>>>>>>>>>> hello
>>>>>>>>>>>>> hello
>>>>>>>>>>>>>> hello
>>>>>>>>>>>>>>> hello000
>>>>>>>>>>>>>>>> hello000

***

## 粗体和斜体
-总结起来

1.*斜体*
1._这是斜体_

2.**加粗**
2.__这是粗体__

3.***斜体加粗***

* 以下是例句

*一盏灯*， **一片昏黄**；***一简书***， 一杯淡茶。 守着那一份淡定， 品读属于自己的寂寞。 保持淡定， 才能欣赏到最美丽的风景！ 保持淡定， 人生从此不再寂寞。

***

## 代码引用
`hello world！`

## 多行代码引用
```
hello world1!
hello world2!
hello world3!
```

## 行内代码块
这一块我们可以用`print("hello world")`  

这行代码有\`字符，需要用双引号``圈住，如 
``print(`)``

## 段落代码块
### 第一个

    public static void main(String[] args)
    {
        System.out.println("hello!");
    }

### 第二个
```
int main()
{
    printf("我又被放鸽子了");
    return 0;
}
```

### 第三个

* 列表下的代码块需要两次Tab缩进才会显示

        int main()
        {
            printf("我又被放鸽子了");
            return 0;
        }

***
# 表格

#### 表格1:左对齐，居中，右对齐
|Tables         |Are            |Cool   |
|---------------:|:-------------:|------:|
|col 3 is       |right-aligned  |$1600  |
|col 2 is       |centered       |$12    |
|zebra stripes  |are neat       |$1     |

#### 表格2
dog     |   bird    |   cat
----    |   -----   |   ----
foo     |   foo     |   foo
bar     |   bar     |   bar
baz     |   baz     |   baz

#### 表格3
|   id  |   name    |   score   |
|   --- |   ---     |   ---     |
|   001 |   Mark    |   90      |
|   002 |   Ford    |   80      |
|   003 |   Alan    |   95      |


## 分隔线
* 正确写法

我（三星：粗）
***
是（带空格的三星：粗）
* * *
符（三底线：粗）
___


分（三等号：细）
===
隔（三减号：细）
---

OVER  
OVER  
OVER  

***

## 分段换行
### 方法一：直接敲两个回车
这是第一段


这是第二段
这是第三段
这是第四段

### 方法二：段尾敲两个空格，然后回车
这是第一段  
这是第二段
这是第三段
这是第四段

### 方法三：以\<br/>结尾
这是第一段<br/>
这是第二段

这是第三段<br/>这是第四段

***
## 标签

### 方法一
---
title: Markdown 简易入门教程  
date: 2017-01-25 1:45:50  
tags: Markdown  
categories: 技术  

### 方法二
---
tags:
- Markdown
- 语言  

categories:
- 技术

### 方法三
---
tags: [Markdown,语言]  
categories: [技术]

***
## 目录
### 方法一：目录 + 跳转标题
---
* [概述](#overview)  
    * [简介](#summary) 

* [初级语法](#primary)
    * [链接](#link)
        * [网址链接](#urllink) 
        * [图片链接](#picturelink)
            * [指定图片宽高](#picturelinksize)
            * [用图床获取外链](#picturelinkchain)
---
<h2 id="overview">概述</h2>
<h3 id="summary">简介</h3>
Markdown是一种轻量级标记语言
<h2 id="primary">初级语法</h2>
<h3 id="link">链接</h3>
111
<h4 id="urllink">网址链接</h4>
111
<h5 id="picturelinksize">指定图片宽高</h5>
222
<h6 id="picturelinkchain">用图床获取外链</h6>

<h6 id="catalog">返回</h6>

***
## 方法二：简单粗暴有效，加上TOC之后，自动生成目录，当然下面也可以加。
[TOC]

# 标题一
.......
## 标题二
.......
### 标题三
.......

***
## 公式
#### 方法一：使用Google Chart

<img src="http://chart.googleapis.com/chart?cht=tx&chl=\Large x=\frac{-b\pm\sqrt{b^2-4ac}}{2a}" style="border:none;">

#### 方法二：使用forkosh

<img src="http://chart.googleapis.com/chart?cht=tx&chl=\Large x=\frac{-b\pm\sqrt{b^2-4ac}}{2a}" style="border:none;">

#### 方法三：使用codecogs

<a href="https://www.codecogs.com/eqnedit.php?latex=x=\frac{-b\pm&space;\sqrt{b^{2}-4ac}}{2a}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?x=\frac{-b\pm&space;\sqrt{b^{2}-4ac}}{2a}" title="x=\frac{-b\pm \sqrt{b^{2}-4ac}}{2a}" /></a>

#### 方法四：使用MathJax引擎（先加载脚本<script>，后解析公式）

<script type="text/javascript" src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=default"></script>

$$x=\frac{-b\pm\sqrt{b^2-4ac}}{2a}$$


***
## 脚注 
[^1]: 脚注一  

这是脚注一[^1]  

这是脚注二[^2]  

这是脚注三[^3]  

[^2]: 脚注二  

 ### 其他什么鬼
 
 **这说明`[^1]:脚注一`标签随便放在哪里生成的文档都是放在最后面的！**

[^3]: 脚注三  


***
## 页面内跳转
1. 先定义一个锚(id)

<span id="jump">Hello World</span>

 2. 然后使用markdown的语法:

[XXXX](#jump)