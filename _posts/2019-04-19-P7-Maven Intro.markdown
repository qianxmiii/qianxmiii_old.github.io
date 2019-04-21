---
layout: post
title:  "Maven 初识"
date:   2019-04-19 12:10:00 +0800
categories: posts learn maven
header-img: img/post/P7-headimg.jpeg
tags:
    - Maven
pid: P7
---

## Maven 作用
Maven的核心功能 合理叙述项目间的依赖关系。
通俗点讲，就是通过pom.xml文件的配置获取jar包，而不用手动去添加jar包
``` xml
    <modelVersion>4.0.0</modelVersion> <!-- 一般为包名，也就是域名的反写 -->
    <groupId>com.ssm.demo</groupId> <!-- 项目名 -->
    <artifactId>ssm-demo</artifactId>
    <packaging>war</packaging>
    <version>1.19.0-SNAPSHOT</version>
    <name>ssm-demo</name>
```

## Maven 仓库
分为三种：本地仓库、第三方仓库(私服)、中央仓库

### 中央仓库
Maven内置了远程公用仓库：http://repo1.maven.org/maven2，这个公共仓库是由Maven自己维护，里面有大量的常用类库，并包含了世界上大部分流行的开源项目构件。目前是以java为主。

&nbsp;工程依赖的jar包如果本地仓库没有，默认从中央仓库下载。

### 第三方仓库
一般是由公司自己设立的，只为本公司内部共享使用。它既可以作为公司内部构件协作和存档，也可作为公用类库镜像缓存，减少在外部访问和下载的频率。

&nbsp; 私服可以使用的是局域网，中央仓库必须使用外网
也就是一般公司都会创建这种第三方仓库，保证项目开发时，项目所需用的jar都从该仓库中拿，每个人的版本就都一样。

&nbsp; 注意：连接私服，需要单独配置。如果没有配置私服，默认不使用


### 本地仓库
Maven会将工程中依赖的构件(Jar包)从远程下载到本机一个目录下管理，每个电脑默认的仓库是在 $user.home/.m2/repository下

![](/img/post/P7-maven1.png)

**Tips:** 一般使用时会修改本地仓库的位置，自己创建新的文件夹，放入一些常用的jar包，$MAVEN_HOME/conf/setting.xml文件中配置该文件夹的地址，这样每次项目可以直接从本地仓库中取。
![](/img/post/P7-maven2.png)

在setting.xml中配置本地仓库的路径
![](/img/post/P7-maven3.png)

## maven java项目结构

<pre class="prettyprint">
---pom.xml　　　　核心配置，项目根下
---src
　 ---main　　　　　　
　　  ---java　　　　java源码目录
　　  ---resources　  java配置文件目录
　---test
　　　---java　　　　测试源码目录
　　　---resources　  测试配置目录
</pre>

**target** 目录 
src/main/java下的源代码就会编译成.class文件放入target目录中，target就是输出目录　　　　　　　　　　　　　　　　　　　　　

## maven 命令

- **编译** `mvn compile`  

--src/main/java目录java源码编译生成class （target目录下）

- **测试** `mvn test`　　　

--src/test/java 目录编译

- **清理** `mvn clean`　　 

--删除target目录，也就是将class文件等删除

- **打包** `mvn package`  

--生成压缩文件：java项目#jar包；web项目#war包，也是放在target目录下

- **安装**　`mvn install`　

--将压缩文件(jar或者war)上传到本地仓库

- **部署/发布** `mvn deploy`　　

--将压缩文件上传私服

- **maven java或web项目转换Eclipse工程** 

`mvn eclipse:eclipse`

`mvn eclipse:clean`　　清楚eclipse设置信息，从eclipse工程转换为maven原生项目

- **maven java或web项目转换Idea工程** 　　　　

`mvn idea:idea`

`mvn idea:clean`　　


## Maven 生命周期
当执行生命周期后面命令时，前面步骤的命令自动执行

![](/img/post/P7-maven4.png)