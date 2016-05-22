---
layout: post
title: 代码创建UISearchBar无法使用委托方法的问题
date: 2016-05-22
categories: blog
tags: [UIView,iOS]
description:  
---

在创建UIView的对象时，要避免使用`var search = UISearchBar()`这样的语法来创建对象，而需要使用`var search: UISearchBar?`。

否则，会造成相应的delegate方法无法使用等问题。

具体原因还待深究。

> 关于delegate：

需要先在类后面引用某个delegate，然后通过 `XX.delegate = self`绑定delegate。即可在代码中使用定义好的delegate方法。
