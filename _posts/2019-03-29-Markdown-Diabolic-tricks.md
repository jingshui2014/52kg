---
published: true
layout: post
date: '2019-03-29 08:34:00 +0800'
categories: Blog
tags:
  - Markdown
  - 奇技淫巧
  - 图片居中
  - 视频适配
excerpt: 本篇文章不涉及Markdown的基本用法，主要总结本人在使用Markdown写博客时所用到的奇技淫巧，如有需要，拿走不谢。
title: Markdown用法之-奇技淫巧
---
<div align="center"><img src="https://www.bobinsun.cn/assets/images/logo-top.jpg"/></div>

---

本篇文章不涉及`Markdown`的基本用法，主要总结本人在使用`Markdown`写博客时所用到的奇技淫巧，如有需要，拿走不谢。


## Markdown图片用法

#### 图片居中

```
<div align="center"><img src="https://www.bobinsun.cn/assets/images/logo-top.jpg"/></div>
```

> 效果展示

<div align="center"><img src="https://www.bobinsun.cn/assets/images/logo-top.jpg"/></div>


#### 自定义图片大小与位置

```
<div align="center"><img width="200" height="auto" src="https://www.bobinsun.cn/assets/images/logo-top.jpg"/></div>
```

> 效果展示

<div align="center"><img width="300" height="auto" src="https://www.bobinsun.cn/assets/images/logo-top.jpg"/></div>

---

## Markdown插入视频

#### 视频适配屏幕

```
<video src="http://qiniu.swarma.org/newUser.mp4" controls="controls" width="100%" height="auto"/>

```

```
src：视频地址---http://qiniu.swarma.org/newUser.mp4

controls：显示或隐藏播放器 true/false

width：播放器宽度

height：播放器的高度
```

> 效果展示

<video src="http://qiniu.swarma.org/newUser.mp4" controls="controls" width="100%" height="auto"/>

---

## 插入Emoji表情符号

#### Emoji资源库

- **emoji-cheat-sheet**：

```
https://github.com/ikatyang/emoji-cheat-sheet/blob/master/README.md
```

`资源截图：`

<div align="center"><img width="600" height="auto" src="https://www.bobinsun.cn/assets/images/emoji-01.png"/></div>

<div align="center"><img width="600" height="auto" src="https://www.bobinsun.cn/assets/images/emoji-02.png"/></div>

> 效果展示

:smile: :blush: :sparkling_heart: :cupid: :speech_balloon: :mag_right: :bathtub: :soccer: :gem: :one: :two: 

:bowtie: :money_with_wings: :anguished: :family: :ox: :mega: :bath: :soccer: :watermelon: :bike: :us: :cn: :one: :u5408: :u6709: :do_not_litter: :sos: :x:

---

## 设置文字属性

#### 改变字体颜色

```
<font color="#FF4500">我要变成这个颜色#FF4500</font>
```
> 效果展示

- <font color="#FF45000">我要变成这个颜色#FF4500</font>

- **附**：《[十六进制颜色对照表](http://www.w3school.com.cn/cssref/css_colornames.asp)》


#### 改变文字大小

```
<font size="1">我要变成1号字</font>
<font size="2">我要变成2号字</font>
<font size="3">我要变成3号字</font>
<font size="4">我要变成4号字</font>
<font size="5">我要变成5号字</font>
<font size="6">我要变成6号字</font>
<font size="7">我要变成7号字</font>
```

> 效果展示

- <font size="1">我要变成1号字</font>
- <font size="2">我要变成2号字</font>
- <font size="3">我要变成3号字</font>
- <font size="4">我要变成4号字</font>
- <font size="5">我要变成5号字</font>
- <font size="6">我要变成6号字</font>
- <font size="7">我要变成6号字</font>

#### 改变文字背景颜色

> 示例代码

```
<table><tr><td bgcolor="#7FFF00">我要变成#7FFF00背景色</td></tr></table>
<table><tr><td bgcolor="#D2691E">我要变成#D2691E背景色</td></tr></table>
<table><tr><td bgcolor="#6495ED">我要变成#6495ED背景色</td></tr></table>
<table><tr><td bgcolor="#FFF8DC">我要变成#FFF8DC背景色</td></tr></table>
<table><tr><td bgcolor="#008B8B">我要变成#008B8B背景色</td></tr></table>
<table><tr><td bgcolor="#A9A9A9">我要变成#A9A9A9背景色</td></tr></table>
<table><tr><td bgcolor="#8FBC8F">我要变成#8FBC8F背景色</td></tr></table>
```
> 效果展示

- <table><tr><td bgcolor="#7FFF00">我要变成#7FFF00背景色</td></tr></table>
- <table><tr><td bgcolor="#D2691E">我要变成#D2691E背景色</td></tr></table>
- <table><tr><td bgcolor="#6495ED">我要变成#6495ED背景色</td></tr></table>
- <table><tr><td bgcolor="#FFF8DC">我要变成#FFF8DC背景色</td></tr></table>
- <table><tr><td bgcolor="#008B8B">我要变成#008B8B背景色</td></tr></table>
- <table><tr><td bgcolor="#A9A9A9">我要变成#A9A9A9背景色</td></tr></table>
- <table><tr><td bgcolor="#8FBC8F">我要变成#8FBC8F背景色</td></tr></table>

---

## Jekyll博客中插入PDF预览插件

```
<object data="http://example.com/yourpdf.pdf" type="application/pdf" width="100%" height="700px">
    <embed src="http://example.com/yourpdf.pdf">
        <p>This browser does not support PDFs. Please download the PDF to view it: <a href="http://example.com/yourpdf.pdf">Download PDF</a>.</p>
</object>
```

>效果展示

#### 《基于知识图谱的问答系统关键技术》

<object data="https://www.bobinsun.cn/assets/pdf/Technologies-QA-Based-on-KG.pdf" type="application/pdf" width="100%" height="700px">
    <embed src="https://www.bobinsun.cn/assets/pdf/Technologies-QA-Based-on-KG.pdf">
        <p>您的浏览器不支持<b>PDFs</b>预览. 请下载该<b>PDF</b>后查看 : <a href="https://www.bobinsun.cn/assets/pdf/Technologies-QA-Based-on-KG.pdf">点击下载PDF</a>.</p>
</object>

---