---
title: XPath 学习
date: 2021-01-21 17:00:28
tags:
	- 网页
---

## 说在前头

在学习 XPath 前， 您应该对 HTML XML 有基本的认识

## 什么是 XPath 

XPath 是 XML路径语言 (XML Path Language)  

可扩展标记语言 路径语言

## XPath有何作用

可以使用简单的表达式以查找 XML HTML 文档中的节点，节点集

一般在爬虫中使用较多

**例：**

使用selenium进行爬虫

``` python
browser.find_element_by_xpath('/html/body/article[5]/aside[1]/div[1]/div/div[2]/i').click()
time.sleep(1)
browser.find_element_by_xpath('/html/body/article[5]/aside[1]/div[2]/div[2]/div[2]/div[2]/ul/li[11]/span[1]').click()
time.sleep(0.5)
browser.find_element_by_xpath(
    '/html/body/article[5]/aside[1]/div[2]/div[2]/div[2]/div[2]/div/div[11]/div[2]/h5').click()
time.sleep(5)
num = browser.window_handles
browser.switch_to.window(num[1])
browser.find_element_by_xpath('//*[@id="ui-accordion-1-header-4"]').click()
time.sleep(0.5)
browser.find_element_by_xpath('/html/body/div[3]/div[1]/div/div[5]/ul/li[2]/a').click()
time.sleep(3)
browser.find_element_by_xpath("/html/body/div[2]/div[2]/div[2]/div[2]/div[1]/div[2]").click()
time.sleep(1)
```

这是我的朋友 (蔡师傅) 直接在 HTML copy 下来的 XPath

**例：**

![image-20210121172935013](C:\Users\Ryuu\AppData\Roaming\Typora\typora-user-images\image-20210121172935013.png)

![image-20210121173022688](C:\Users\Ryuu\AppData\Roaming\Typora\typora-user-images\image-20210121173022688.png)

这样复制下来的 XPath 就能直接找到该节点

**/html/body/div[4]/div[2]/div/div[2]/dl[1]/dd/a[3]/em**

但是缺点也很明显 可读性太差了

较好的处理是通过其中 class 属性 的值来进行查找

**//em [@class="cmn-icon wiki-lemma-icons wiki-lemma-icons_discussion-solid"]**

![image-20210121173426571](C:\Users\Ryuu\AppData\Roaming\Typora\typora-user-images\image-20210121173426571.png)

这样可读性就提高了 并且 通过了相对查找, XPath 经过的结点也就大大的减少了 仅剩一个

**解释：

**//** 相对查找

**x**  匹配 x **元素节点**

**@x**  匹配 x **属性节点**

//x[@y]  匹配 x **元素节点** 且 该元素有 y **属性**

//x[@y="z"] 匹配 x **元素节点** 且 该元素有 y **属性 ** 其值为 z