---

title: 几个有趣的Rust特性
date: 2015-02-14 17:24:21
tags: ["语言"]
description: "讲一讲几个好玩的Rust的特性"
keywords: "rust,crate,trait,funcitonal programming,pattern maching,生存期"
---



## 生存期
http://www.reddit.com/r/rust/comments/2aryfm/what_does_the_a_keyword_mean/
http://www.reddit.com/r/rust/comments/26dd52/trying_to_write_a_function_that_returns_a/
http://doc.rust-lang.org/0.12.0/guide-lifetimes.html

## 闭包


## 匹配


## 并行

Rust提供了两个库, `libnative(1:1线程模型)` 和 `libgreen(m:n线程模型)`

**libnative** 是默认的实现,在这种模型下,一个task对应一个操作系统线程,且每一个IO对象
都对应一个唯一文件描述符,也就是说这种情况下,最大的Task数会有限制。

**libgreen** 是基于libuv实现的一个库,M:N线程模型中的M是指当前进程内的操作系统本地线程
个数，N是指Rust任务个数(即绿色线程个数),一般 N >> M
