---
layout: post
title: tipsssssss
date: 2016-12-01
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


-  cocoapods 删除了master以后快速恢复方案
切换到 ~/.cocoapods/repos
git clone "https://git.coding.net/hging/Specs.git"
把在“git”改为“master”


-   func clicked(obj: 'AnyObject'){
        var btn = obj
        btn = obj as UIButton
        btn.tag 
	}//报ambiguous use of tag错
	把'AnyObject'改为UIButton即可。


-  no such module "XX"
到"Link Binary with Libraries"把相应的framework加到项目来即可


- “Use Legacy Swift Language Version” (SWIFT_VERSION) is required to be configured correctly for targets which use Swift. Use the [Edit > Convert > To Current Swift Syntax…] menu to choose a Swift version or use the Build Settings editor to configure the build setting directly.”
找到对应的target，找到Swift Compiler - Search Paths 下的 Use Legacy Swift Language Version，改为YES！

- dyld: Library not loaded XXX
 在对应的targets -general- ,Embed bnaries 相关的Frameworks,
 在CLEAN PROJECT后出现问题，需要删掉之前的，再次执行此操作！


- 解析JSON的时候！！有"("，可能就是一个ARRAY（包含了许多了‘{...}’），不能直接的解析出来！！！！