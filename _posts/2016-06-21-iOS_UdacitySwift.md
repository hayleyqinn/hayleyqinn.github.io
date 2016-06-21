---
layout: post
title: Udacity_Swift语法学习笔记
date: 2016-06-21
categories: blog
tags: [iOS]
description:  
---

- 函数中的参数使用**inout**关键字来按引用传递值，需要配合使用& 

- **位运算符**：
	~: not，逆转 位的顺序

	&: and，比较每个位是否相同，最后输出结果（长度不变，用每个位的比较结果0或1表示）

	|: or ，原理同上

	^: xor，每个位相等为0，不相等为1。 

- **空和**：?? ，解包可选值，如果其并非零值，则使用该值。否则，使用指定的“默认”值

- swift当前的数组和字典类型**不支持直接从 URL 加载数据**，但是这种情况可能很快就会改变。同时，现在必须以“NSArray”或“NSDictionary”开始，然后将其转换为合适的 Swift 类型。

- mutating

- **map()和reduce()**。它们是 Swift 的 SequenceType 协议的一个函数，通常被数组和字典调用
	
	```//本示例理解为遍历并可处理每个数据，还可自定义返回值。
	let tripContributions = ["Andy": 25, "Kathleen": 45, "Janhavi": 50, "Sebastian": 10, "Chrisna": 50]
 	let averageTripCost = (25 + 50 + 45 + 10 + 50)/5
 	
 	let tripDebts = tripContributions.map({ (key, value) -> String in
	    let amountOwed = averageTripCost - value
	    if amountOwed > 0 {
	        return "\(key) owes $\(amountOwed)"
	    } else {
	        return "\(key) is owed $\(-amountOwed)"
	    }
	})//也可以把此右圆括号放在左圆括号后，拖尾闭包。
	//["Sebastian owes $26", "Chrisna is owed $14", "Andy owes $11", "Janhavi is owed $9", "Kathleen is owed $14"]
 要知道，闭合类型，包括参数和返回的类型，in 和 return都可以被推断出来，而使用$0 可以显示第一个被输入的参数。
```
 	
 	```//0为初时值，currentMax是当前结果，number数组元素
 	let numbers = [7, 89, 48, 20, 38, 89, 29]
	let highestNumber = numbers.reduce(0, combine: {(currentMax, number) -> Int in
    	return max(currentMax, number)
	})
	//89

	//运用简写
	let maxNumber = numbers.reduce(0, combine:{
    	max($0, $1)
	})

	//对于拖尾闭包，它的形式类似于：
	let maximum = numbers.reduce(0) {
    	max($0, $1)
	}```

- 子类init里面也可以调用父类的init，即复用super.init

- 结构体和类有重合的地方，但是一个是值类型，一个可以是引用。

- 高级结构体
  在定义扑克牌的结构体后，使用。
 let s = suitcard(suit: .hearts , value .ace)来初始化。
 ```struct SuitedCard {
	    enum Suit {
	        case Hearts
	        case Spades
	        case Diamonds
	        case Clubs
	    }

	    enum Value {
	        case Two
	        case Three
	        case Four
	        case Five
	        case Six
	        case Seven
	        case Eight
	        case Nine
	        case Ten
	        case Jack
	        case Queen
	        case King
	        case Ace
	    }

	    let suit: Suit
	    let value: Value
	}```

