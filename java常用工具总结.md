#JAVA常用工具总结(大纲版)
目前只是把工具名称列在下面，之后我会把一些我遇到的坑，写在对应的工具下

> 最近深感后端要学的东西太多了，为了不至于拣了芝麻丢了西瓜，同时与大家分享下知道的一些东西，所以写了这篇文章

[一些Java有用的链接](https://github.com/Vedenin/useful-java-links)

## 框架
这里就不根据三层架构来细分了

1. SSM([SpringMVC]()+[Spring]()+[Mybatis]())
   
   > 就不介绍 SSH(Struts2 + Spring + Hibernate) 了 , 有兴趣自己搜索
   
   目前最常见的java web 开发框架，配合Maven管理项目能够快速搭建出一个高效的Java项目。
   
   > 这里安利一下 [IntelliJ IDEA](https://www.jetbrains.com/idea/),具体原因可以看[你认为IntelliJ IDEA是最智能的IDE吗？](https://www.zhihu.com/question/19690559)事实上这是我用过最舒服的IDE。
   
   >IntelliJ IDEA 企业版是收费的（社区版阉割的太多），但可以通过[lanyus](http://idea.lanyus.com)来获取注册码。
   

2. [Spring Boot](http://projects.spring.io/spring-boot) 
	
	Spring全家桶，从前端模板都数据库连接都已集成，只需要一段Maven/Gradle代码（或者Intellij 勾选几个要用的组件）就可以自定义出一个你自己的Java项目。
	

3. [jFinal](http://www.jfinal.com)
 
	国产。。用起来感觉有点像Spring Boot，但挺不错的

> 其他框架诸如Jersay,Nutz,Resty就不介绍了，有兴趣的可以自己搜索，如果用于生产，建议使用上面3种框架。

## 代码/项目管理

1. Git

	如果你是在github上看到本文的，应该就不需要介绍了

2. [Maven](http://maven.apache.org) 
	
	项目管理工具，从项目的创建、添加jar包，到打包、部署你都可以使用maven命令来完成。当然我主要用它管理依赖包。
	
	一般公司都会有自己的私人仓库，通常使用[Sonatype Nexus](http://www.sonatype.org)来搭建，具体教程自己搜索，这里就不赘述了。

3. [Gradle](https://gradle.org)

	谷歌的项目管理工具，目前很多Android项目都是使用它来管理的，而它也可以用于后台

## Apache Commons工具包

Apache Commons是一个非常有用的工具包，虽然它提供的大部分功能现在都有更优秀的选择，这里我只讲几个常用的以及其替代品，具体信息可以参考[Apache Commons 工具包](http://langgufu.iteye.com/blog/1913579)

1. BeanUtils

	最常用的情况就是查数据库一个bean，前端展示另一个bean，如果一个个去get/set会很冗余，于是就采用BeanUtils.copyProperties 来复制相同名字的字段。
	
	> 如果相同名称字段类型不同，会报错
	
2. Codec

	加密/哈希，url解析，生产二维码，图片转Base64等都可能用到。不过这些现在网上都有封装好的方法，所以一般不需要直接使用这个方法。
	
3. Collections

	Java Collection框架的扩展，比如通过value获得key，删除一个集合里的元素并返回删除的元素等。
	
4. Configuration

	Commons-Configuration 可以帮助处理配置文件的，如读写.properties、.xml文件等
	
5. FileUpload

	FileUpload 就是上传文件了，不过现在有很多云存储，可以选择上传到云上

6. HttpClient

	模拟http请求，我原来就是用这个做爬虫的，只不过WebMagic封装了它，所以现在使用webMagic更好

7. IO

	IO 是一个 I/O 工具集

8. Lang

	java.lang的拓展工具集

9. Math

	Math 是一个轻量的，自包含的数学和统计组件，解决了许多非常通用但没有及时出现在Java标准语言中的实践问题.


##Google Guava包

[Guava](https://github.com/google/guava) 是一个 Google 的基于java1.6的类库集合的扩展项目，包括 collections, caching, primitives support, concurrency libraries, common annotations, string processing, I/O, 等等. 

> 如果英语不好，可以看看[Google Guava官方教程（中文版）](http://ifeve.com/google-guava)

## 注解
> 感觉挺有用的，但又不知道怎么给他分类

## 分布式工具

1. [Duddo](http://dubbo.io)
   

2. [Zookeeper](http://zookeeper.apache.org)

## J.U.C并发框架
> 本来想把redis加锁放在这里的，现在只能放到别的地方了

1. Atomic包
	
2. 锁
	>Java 有着synchronized、wait、notify/notifyAll内部锁，但J.U.C也提供了Lock、Condition，[这里](http://blog.csdn.net/chengguotao/article/details/50498090)主要列举下2种锁的优缺点。

3. 线程池

	*  ThreadPoolExecutor
	*  Executors
	*  Future，FutureTask
	*  Fork/Join

4. 线程安全的集合

	顾名思义,就是多线程访问时不会出现数据不一致或者数据污染，这里有一个[例子](http://blog.csdn.net/nx188/article/details/50988037)。
	
	最常用的应该是 ConcurrentHashMap ，其他的详见[这篇文章](http://www.cnblogs.com/ijavanese/p/3778688.html)。

## 文件处理

1. [POI](http://poi.apache.org/)

	Apache 出品的 Java 操作 Microsoft Office 的工具

2. 	[Thumbnailator](https://github.com/coobird/thumbnailator)
	
	图片处理工具

3. [顽兔](http://wantu.taobao.com/mediaportal/index.htm)
	
	阿里云提供的文件存储云，有着很赞的文件处理api，另外七牛云也不错。	

## 消息队列

1. [RabbitMQ](http://www.rabbitmq.com/)

	RabbitMQ是一个在AMQP基础上完整的，可复用的企业消息系统

2. [Kafka](http://kafka.apache.org)
	
	不知道是不是错觉，看到好几家公司用这个做日志系统

3. [RocketMQ](https://github.com/alibaba/RocketMQ)
	
	阿里开源的消息中间件

4. [ONS](https://www.aliyun.com/product/ons)
	
	> 阿里云提供的消息队列服务(据说用的就是RocketMQ?)
	
> 貌似有些人也用redis的 pub/sub来做消息队列，我只能说，redis是内存数据库！！！

## 数据库
> 这里不单指传统的数据库，也包括NoSql和内存数据库

1. [Mysql](http://www.mysql.com)/[MariaDB](https://mariadb.org)

2. [PostgreSQL](https://www.postgresql.org)

3. [Alisql](https://github.com/alibaba/AliSQL)

	AliSQL是阿里巴巴基于于MySQL官方版本的一个分支，性能较MySQL有较大提升。

4. [Mongodb](https://www.mongodb.com)

5. [Redis](http://redis.io)
	
	虽然redis也会在硬盘上读写，然而大部分时候它是存在内存里的，所以一宕机就可能找不回来，所以要慎用。

6. [HBase](http://hbase.apache.org)

> 以上数据库均推荐使用阿里云，因为它提供了容灾、备份、恢复、监控、迁移等方面的全套解决方案，目前来看，价格也可接受。

## 搜索

1. [Solr](http://lucene.apache.org/solr)

	Solr是一个基于Lucene的Java搜索引擎服务器。

2. [ElasticSearch](https://www.elastic.co/products/elasticsearch)
	
	ElasticSearch是一个基于Lucene的分布式搜索服务器
	
> [搜索引擎选择：Solr与ElasticSearch](http://www.cnblogs.com/chowmin/articles/4629220.html)

3. [OpenSearch](https://www.aliyun.com/product/opensearch)

	OpenSearch是一款阿里巴巴自主研发的大规模分布式搜索引擎平台。

## 爬虫

1. [WebMagic](http://webmagic.io)
	
	目前看到的最好用的爬虫框架，现在用Java写爬虫方便多了，我原来都是用httpClient，自己封装方法的啊。。

2. [神箭手](http://www.shenjianshou.cn) 

	这是个爬虫市场，提供了很多免费/收费的爬虫，如果你想省时省力可以尝试在这里找下。
	
## 发送邮件

1. [JavaMail](http://www.oracle.com/technetwork/java/javamail/index.html)

	Oracle 官方提供的邮件发送工具

2. [Simple Java Mail](http://www.simplejavamail.org)

	很好用的邮件发送工具，api简单易用，支持链式语法。

## 前端渲染模板

1. [Velocity](http://velocity.apache.org)

2. [Thymeleaf](http://www.thymeleaf.org)

> 2个都是前端模板，除了语法不同，没啥区别，看个人喜好吧。

## Util工具
从Json到日期的各种Util，想到什么写什么吧

1. [opslabJutil](https://github.com/0opslab/opslabJutil)

	很多常用Java操作方法
	
2. [Fastjson](https://github.com/alibaba/fastjson)
	
	一个很快的json转换工具
	
3. 	[Java-util](https://github.com/jdereg/java-util)
	
	一些复杂的java-util类方法

## 持续集成

> 持续集成是指每次集成都通过**自动化**的构建（包括编译，发布，自动化测试）来验证，从而尽早地发现集成错误。

1. [Jenkins](https://jenkins.io/index.html)

	* 持续的软件版本发布/测试项目。
	* 监控外部调用执行的工作。

## 测试

1. Junit

	Java 自带的包
	
2. [mockito](https://github.com/mockito/mockito)	
	模拟测试框架
	
> [SpringBoot与JUnit+Mockito 单元测试](https://zhuanlan.zhihu.com/p/21444517)
	
## 备注	

> PS1. 可以看出我上面列举的模块，大部分都添加了阿里云或者同类型产品，因为个人认为自己搞这个的成本（这里包括人工、时间、可能遇到无法解决的bug）太高，所以推荐能使用其他人的轮子就使用其他人的轮子吧。

=
> PS2. 目前很多产品的官方文档都写的很完善了，所以我建议学习一个新东西时，先去看官方文档，如果觉得还是不懂，再去看第三方提供的学习资料（包括文章、视频和demo）。对于语言或程序基础，我是很推荐书的，但对于一个具体的工具，我是不推荐看书的，因为：
	1. 语言更新速度太快，书出来的时候，说不定这个东西已经添加很多功能了；	2. 这些书都不是官方写的（官方只会在网站上更新文档），所以出现了偏差，是不负责任的。

=
> PS3. 关于技术选型，我原来很是纠结于此（甚至有点像女生逛商场一样）。后来一位前辈教导我：技术是为了满足业务需求的，所以你在选择技术时，第一步是看他能否承担的起你的业务需求；其次尽量选择稳定、使用者多的技术，不然这个项目负责人一走，别人直接没法维护；最后，再前两者基础上，选择自己最熟悉的技术，这样开发效率能够最高，你就可以拿别人加班的时间来学习新东西。当然在自我成长的时候，还是要多接触新的技术的，学习它的使用方法，学习它的优秀的一些理念。