---
title: md演示
date: 2026-01-16 08:38:59
tags:
---
# 一级标题
## 二级标题
### 三级标题
#### 四级标题
##### 五级标题
###### 六级标题

Markdown是HTML的子集，所有HTML标签都可以在Markdown中直接使用。
是HTML的简化版本

换行要隔开(这个取决于解释器)

## 常见用途

- 项目的 `README.md` 文档 编写 在github gitee等git平台非常常见

- 做笔记

- 编写网页博客文章 如`Hexo`

- AI对话的输出默认使用markdown格式输出

## 特殊字体

**粗体** <b>粗体</b>

*斜体*  <i>斜体</i>

~~删除线~~  <s>删除线</s>

`小代码块` <code>小代码块</code>

<u>下划线</u> 

可以直接使用html标签

<font color="red">颜色</font>
<font size="5">大小</font>

## 引用

> 引用内容

## 链接

[百度](https://www.baidu.com)
<a href="https://www.baidu.com">百度</a>

[百度](https://www.baidu.com "百度")
<a href="https://www.baidu.com" title="百度">百度</a>

[百度链接][百度]

[百度]: https://www.baidu.com
## 图片
![图片](https://www.baidu.com/img/bd_logo1.png)
<img src="https://www.baidu.com/img/bd_logo1.png" alt="图片">

## 列表

### 无序列表
- 列表
- 列表
    - 列表
        - 列表
        - 列表
- 列表

* 列表
* 列表
### 有序列表

1. 列表
2. 列表
    1. 列表
    2. 列表
3. 列表

## 表格
| 表格头 | 表格头 | 表格头 |
| --- | --- | --- |
| 表格体 | 表格体 | 表格体 |
| 表格体 | 表格体 | 表格体 |

## 代码块
```java
public static void main(String[] args) {
    System.out.println("Hello World");
}
```
```c
int main()
{
    printf("Hello World");
    return 0;
}

```
<!-- ## 注释 -->
在不同的解释器中，渲染的样式不同

- 示例：

    [blog(自定义)](https://blog.gldhn.top/2026/01/16/hello_md/)

    [github](https://github.com/Guailoudou/hexo/blob/main/source/_posts/hello_md.md)

## 数学公式

$E=mc^2$

$\frac{n(n+1)(2n+1)}{6}$

$$
\displaystyle \left( \sum_{k=1}^n a_k b_k \right)^2 \leq \left( \sum_{k=1}^n a_k^2 \right) \left( \sum_{k=1}^n b_k^2 \right)
$$

