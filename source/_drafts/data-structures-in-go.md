---

title: Go中的几种数据结构
date: 2015-02-06 11:04:41
tags: ["Golang"]
description: "常用的Golang数据结构"
categories: "Go网络编程"
keywords: "Golang,Golang数据结构"
---

##Array
###创建与初始化

##Slice
###创建与初始化
##Map
###创建与初始化
##Struct

###声明与初始化

###匿名字段

###Tag的使用
<span style="display:none">
http://stackoverflow.com/questions/10858787/what-are-the-uses-for-tags-in-go
</span>
###方法集
在讲struct的方法集之前,我们需要先弄明白golang的`interface`和`receiver`

在官方的specification中,对方法集的定义是这样的:

> A type may have a method set associated with it. The method set of an interface type is its interface. The method set of any other type T consists of all methods declared with receiver type T. The method set of the corresponding pointer type ＊T is the set of all methods declared with receiver ＊T or T (that is, it also contains the method set of T). Further rules apply to structs containing anonymous fields, as described in the section on struct types. Any other type has an empty method set. In a method set, each method must have a unique non-blank method name.

> The method set of a type determines the interfaces that the type implements and the methods that can be called using a receiver of that type.


##Reference
1. [Method sets specification](https://golang.org/ref/spec#Method_sets)
2. [Go学习笔记](https://github.com/qyuhen/book)
3. [array-slice-map-and-set-in-golang](http://se77en.cc/2014/06/30/array-slice-map-and-set-in-golang/)

