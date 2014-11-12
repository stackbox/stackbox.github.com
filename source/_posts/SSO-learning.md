title: 基于CAS的单点登录学习
date: 2014-11-10 16:11:52
tags: ['CAS','SSO','spring','java']
---

目前一般使用般用jasgi-CAS来实现SSO

具体协议： http://jasig.github.io/cas/4.0.0/protocol/CAS-Protocol.html

分为基础模式和代理模式，代理模式是cas3新增点内容

![](/image/cas/cas-web-flow.png)

![](/image/cas/proxy-web-flow.jpg)


我自己对cas基础模式的实现： https://github.com/superalsrk/EasyCas