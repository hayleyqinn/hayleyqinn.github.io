---
layout: post
title: 关于navigationController的跳转
date: 2016-05-29
categories: blog
tags: [navigationController,tableview,iOS]
description:  
---

－ 一旦代码跑去appdelegate报错，多半就是故事板和代码没对上，即可能是因为故事板没有某vc，而代码里面调用了。或者故事板里面某个组件还有outlet，但是代码是没有相关内容的。

－ 当设定跳转到另外一个界面的kind为show时，想回到先签的界面，除了滑动，还可以`self.navigationController?.popViewControllerAnimated(true)`

- 不知道返回什么，还可以返回nil嘛  - -！

－ tableview 每个cell上方的有一个header，head又好像不能被didselected...这种方法所调用，如果想做到普通cell右边有个小箭头，并且cell可被点击怎么办呢？

在header新建并添加一个cell，cell设置好右方的小箭头，怎么点击呢？用一个和cell等宽的透明（`UIColor.ClearColor()`）按钮就行了呀蛤蛤蛤