title: buld your own cas service 2
date: 2015-01-06 13:21:32
tags: []
---




http://jcbay.iteye.com/blog/860018

单点登录配置，默认的效果是这样的：

1. 就是这样子的。。嗯嗯
2. 我们想做的是 logout之后重定向到登录界面


，那么可以修改cas-servlet.xml文件，在"logoutController"的bean配置中增加属性“followServiceRedirects”，设置为“true”，然后在业务系统的注销连接中加入"service参数",值为业务系统的绝对URL，这样就OK了，如你的业务系统URL为：http://localhost:8080/casClient，那么注销URL就为：http://localhost:8080/cas/logout?service=http://localhost:8080/casClient




关于princple，jasig对此进行了封装

```java
org.jasig.cas.client.authentication.AttributePrincipal

AttributePrincipal attribute = (AttributePrincipal) request.getUserPrincipal();

javaEE中定义的Principal可以转换为  AttributePrincipal

AttributePrincipal.getName()  就是 Resolver中返回的SimplePrincipal名字

AttributePrincipal.getAttributes() 就是Resolver中返回的SinmplePrincipal的attributes

```


http://www.open-open.com/lib/view/open1329744257937.html

注意把serviceRegistryDao全部删掉

