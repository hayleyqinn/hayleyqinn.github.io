---
layout: post
title: 关于cell遇到的问题
date: 2016-06-21
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

> 当然了，原文链接附上(http://swift.gg/2016/06/02/swift-selector-syntax-sugar/#more)

### 实现tableview

- 其中一种方法是直接拖入一个tableview controller，此时类也继承一个tableview controller，但不能同时继承多个控制器。事实上控制器已经自动实现了数据源以及相应的代理。

- 第二种是在已有view controller里面拖进一个table view。接下来就是要手动实现委托和数据源了，首先将tableview outlet到view controller，指定好委托对象和数据源对象。

当然，该方法想要实现数据源，也可以在此文件的view controller类外面extension 该控制器，即`extension viewController: UITableViewDataSource{//func tableview(numberOfInSectin....)}`

在跳转传值时可以在prepareForSegue()里面 通过`let vc = segue.destinationViewController as! XXXXController`获得某个控制器。
此外，如果访问的另外一个控制器的组件是通过故事板拖进来，则不能直接在上一个控制器设置下一个控制器这个组件的值，因为后一个view只有在访问时才被创建，会出现空值的情况。

### 实现自定义cell 

- 可以通过代码创建，然后addsubview

- 通过故事板。即在故事板拖入的imageview是不能直接拖进vc的，要单独建立一个基层tableview cell的类，把cell里面的组件和该类绑定，才能往这里outlet。

`let cell = tableview.dequeueReusableCellWithIdentifier("cell") as! "CustomCellClass"`，在vc里面通过这样的强制转换可“识别”到上新建的类。


