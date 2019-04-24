---
layout: post
title:  "Spring 入门"
date:   2019-04-23 21:26:00 +0800
categories: posts learn spring
header-img: img/post/P7-headimg.jpeg
tags:
    - Mooc
    - Spring
pid: P8
---

## Java Web发展史
第一阶段：JavaBean + Servlet + JSP

第二阶段：EJB重量级框架

第三阶段：SpringMVC/Struts + Spring + Hibernate/myBatis

第四阶段：SpringBoot 约定大于配置

第五阶段：Dubbo SOP微服务架构体系

第六阶段：SpringCloud微服务框架

## IoC
Inversion of Control, **控制反转、依赖注入**

**控制**
  控制对象的创建及销毁（生命周期）
  
**反转**
  将对象的控制权交给IoC容器


为什么要用Ioc？
   用户需要执行某个操作，需要自己创造一个对象，自己调用方法。`高耦合性`
   将这一切交由IoC容器来处理。。

**约定：**
- 所有Bean的生命周期交由IoC容器管理
- 所有被依赖的Bean通过构造方法执行注入
- 被依赖的Bean需要优先创建

   
   

  
  



参考资料：[Spring框架小白的蜕变][Spring框架小白的蜕变]

[Spring框架小白的蜕变]:https://www.imooc.com/learn/1108
