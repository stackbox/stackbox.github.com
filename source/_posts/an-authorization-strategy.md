title: 一种基于RBAC的授权策略实现
date: 2014-07-03 19:11:32
tags: 
---

##资料尚未整理，未完待续##


数据权限



功能全新： 以flymeal为例，就是某个后台管理员的面板显示哪些功能，不显示哪些功能：

Shiro提供了一套JSP标签库来实现页面级的授权控制。 
在使用Shiro标签库前，首先需要在JSP引入shiro标签： 

<%@ taglib prefix="shiro" uri="http://shiro.apache.org/tags" %>  

hasRole标签 
验证当前用户是否属于该角色

```xml
<shiro:hasRole name="administrator">    
    <a href="admin.jsp">Administer the system</a>    
</shiro:hasRole>    
```


hasPermission标签 
验证当前用户是否拥有制定权限 
```xml
<shiro:hasPermission name="user:create">    
    <a href="createUser.jsp">Create a new User</a>    
</shiro:hasPermission> 
```

ubject：即“当前操作用户”。但是，在Shiro中，Subject这一概念并不仅仅指人，也可以是第三方进程、后台帐户（Daemon Account）或其他类似事物。它仅仅意味着“当前跟软件交互的东西”。但考虑到大多数目的和用途，你可以把它认为是Shiro的“用户”概念。 
Subject代表了当前用户的安全操作，SecurityManager则管理所有用户的安全操作。 

SecurityManager：它是Shiro框架的核心，典型的Facade模式，Shiro通过SecurityManager来管理内部组件实例，并通过它来提供安全管理的各种服务。 

Realm： Realm充当了Shiro与应用安全数据间的“桥梁”或者“连接器”。也就是说，当对用户执行认证（登录）和授权（访问控制）验证时，Shiro会从应用配置的Realm中查找用户及其权限信息。 
从这个意义上讲，Realm实质上是一个安全相关的DAO：它封装了数据源的连接细节，并在需要时将相关数据提供给Shiro。当配置Shiro时，你必须至少指定一个Realm，用于认证和（或）授权。配置多个Realm是可以的，但是至少需要一个。 
Shiro内置了可以连接大量安全数据源（又名目录）的Realm，如LDAP、关系数据库（JDBC）、类似INI的文本配置资源以及属性文件等。如果缺省的Realm不能满足需求，你还可以插入代表自定义数据源的自己的Realm实现。 




权限声明的粒度：

页面级： 通过一些jsp tag显示，隐藏某些元素

controller级：

相关的注解： 
@RequiresAuthentication 
可以用户类/属性/方法，用于表明当前用户需是经过认证的用户。


对象都是对Subject而言的：





数据级权限： 数据级的权限就要通过sql进行实现了，可以通过特殊注解的方式实现，比如mybatis plugin

数据级权限就跟具体的需求严重相关了， 页面级和controller级这种功能权限只是: 要么true要么false

而数据集权限却是从database中 filter一堆符合权限要求的数据，就需要拼接sql语句了，可以通过mybatis

一些手法缩短此过程，具体原理可以参考mybatis的分页插件原理；




权限表达式：




资源：相关的怎么编码






其他： oauth






飞饭的后台产品需求：





关于第三方开放平台：



