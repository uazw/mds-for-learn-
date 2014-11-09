#Spring
spring is a very important in java world.


##Ioc

spring 的IoC分为两个部分:  

1. 注册Bean(加入Spring容器)
2. 依赖注入

####XML

Autowiring modes:  
1. no 需要手动设置property  
2. byName 根据属性名字来  
3. byType 根据属性类型来  
当有多个是同一类型会出现异常 解决方案:  
1. 设置某些同类型bean *autowire-candidate* 为false(false意味着不会被自动注入)  
2. 设置某个同类型的bean *primary* 为true

####annotation

	<context:component-scan>

自动开启  

	<context:annotation-config>

#####装配注解

1. @Autowired byType
2. @Qualifier 用于限定范围(注解在类上)
3. @Resouces 先byName 然后byType

#####注册型注解

1. @Component 一般型构造注解
2. @Repository 数据仓库型注解(DAO层)
3. @Service 服务层注解(Service层)
4. @Controller 表示层注解

####java code

1. @Configuration 用于类上表明这个类是个配置类
2. @Bean 用于方法上表明这个方法将返回一个Bean

####bean scope

1. singleton 单例
2. prototype 任意数目
3. request http **request**
4. session http **session**
5. global session
6. application ServletContext

####bean Lifecycle

1. @PostConstruct or xml init-method
2. @PreDestroy	or xml destroy-method