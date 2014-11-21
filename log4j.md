#Log4j
日志是一个很重要的东西  很多时候我们需要根据日志来判断程序运行效果  
一般使用[log4j.properties](#example)进行配置  

log4j的一般配置如下

	log4j.logger.logger_name=logger_level, special_appender_name
	log4j.appender.special_appender_name=where_to_appender
	log4j.appender.special_appender_name.layout=*Layout
	log4j.appender.special_appender_name.layout.*Pattern=special_pattern

##Logger

+ logger\_name  
由以下代码决定

		public static Logger log = Logger.getLogger(HelloWorld.class.getName());
+ logger\_level  
	
		ALL < DEBUG < INFO < WARN < ERROR < FATAL < OFF.

###rootLogger

rootLogger是所有logger的父类
子类可以覆盖logger\_level 和 special\_appender_name

###category

		log4j.category.special_category_name=logger_level, special_appender_name

当logger_level为ERROR的时候只会显示ERROR FATAL OFF的消息

##Appender

+ where\_to_appender  
ConsoleAppender  控制台  
RollingFileAppender  按照文件大小建立新日志文件  
DailyRollingAppender  每天建立新日志文件

##Layout

+ *Layout  
[PatternLayout](#pl)  
HTMLLayout  
XMLLayout
<h5 id='pl'></h5>
PatternLayout参数如下  
![sdf](/pl.png)
<h5 id='example'></h5>
一个典型的例子如下  

	log4j.logger.HelloWorld=INFO, stdout
	log4j.appender.stdout=org.apache.log4j.ConsoleAppender
	log4j.appender.stdout.layout=org.apache.log4j.PatternLayout
	log4j.appender.stdout.layout.ConversionPattern=%d{yyyy-MM-dd HH:mm:ss} %-5p %c{1}:%L - %m%n
