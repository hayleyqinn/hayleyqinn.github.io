---
layout: post
title: 如何获取tableView中cell中的按钮点击数据
date: 2016-05-12
categories: blog
tags: [tableView][iOS]
description:  
---

在tableView返回cell的方法中，将'indexPath.row'的值给'UIButton'的'TAG'

然后通过'addTarget'方法，可以得知点击的是哪一个按钮。