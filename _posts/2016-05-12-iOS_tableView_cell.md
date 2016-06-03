---
layout: post
title: 获取cell中的按钮点击数据
date: 2016-05-12
categories: blog
tags: [tableView,iOS]
description:  
---

## 第一种方式

在tableView返回cell的方法中，将`indexPath.row`的值给`UIButton`的`TAG`。

然后通过`addTarget`方法，可以得知点击的是哪一个按钮。

## 第二种方式

`let cell = btn.superview!.superview as! UITableViewCell`

`typeClickedIndex = tableView.indexPathForCell(cell)!.row`

`typeClickedIndex`即点击`cell`上任意组件返回的`index`

## 可以用来做简单的英文搜索哦

`func searchBar(searchBar: UISearchBar, textDidChange searchText: String) {
        print(searchText)
        // 没有搜索内容时显示全部组件
        if searchText == "" {
            self.ase = self.a
        }
        else { // 匹配用户输入内容的前缀(不区分大小写)
            self.ase = []
            for ctrl in self.a {
                if ctrl.lowercaseString.hasPrefix(searchText.lowercaseString) {
                    self.ase.append(ctrl)
                }
            }
        }
        // 刷新Table View显示
        self.tableView.reloadData()
    }`

## 既然上面提到了addTarget，就记录下今天看的语法糖吧

那就是巧妙的应用枚举型。

1. 对按钮。在每个按钮都有tag的前提下，可以在一个单独函数里面通过switch语句针对不同按钮的tah进行响应。
2. - 对其他。可以通过struct类型下添加不同的selector，注意是完整的selector，即把addTarget里面的action参数替换成可读性更好的。
   - 同样的，可以直接extension Selector，在extension里面定义一个变量来存储#selector......，， 之后可直接使用该变量。

## 类型推荐

原来除了var 可以推， `UIColor.WhiteColor()` 也可以推啊！---> `.WhiteClor()`