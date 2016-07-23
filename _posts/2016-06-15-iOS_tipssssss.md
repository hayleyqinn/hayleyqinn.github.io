---
layout: post
title: tipsssssss
date: 2016-06-15
categories: blog
tags: [iOS]
description:  
---

- not comform to 代表没有实现委托的方法

- 委托本质就是协议

- oc的协议和swift的协议没有本质区别，都要实现必须的方法。

- 委托成功后，代码一定会自己上来的，没有必要自己去看源文件定义的协议，然后自己改写成swift版，都是错的！！！！（特指实现oc的协议）

- performsegue... 执行后，会马上执行praparesegue....  不要把需要传值的变量写在第一句话后面，否则第第二话得到是nil

- 关于swift项目用到了oc库，用点方法无缝得到xCode已经帮你改好的swift版方法，但是（id）类型需要初始化的不能通过点方法得到，要通过 实例名(指定变量名: 要传入的变量)。这也说明了为什么 CGRect(frame: )为什么是这个形式。

- let view = UIViewXXXX()，每实例化一次，就当与新建了一个view，前面的设置均失效。执行过`let label = UILabel()`后再执行`let label = UILabel(frame: CGRect(x: 0, y: 80, width: screenW, height: 20))`，就当与重置了这个View了。

	