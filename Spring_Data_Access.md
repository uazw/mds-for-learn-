#Spring Data Access
主要讲述如何用Spring与数据库框架或者JBDC集成

##Transaction
事务是个很重要的话题在Hibernate中对应的机制应该是**Session**  
主要讲用注解方式来进行事务  
即 **@Transactaional**  
为激活用注解方式需要

1. 用XML配置  

		<tx:annotation-driven />

2. 用java Code配置

		@EnableTransactionManagement

###事务配置
Spring的事务是可配置的

1. value  
约束需要用到的事务管理器名字
2. [propagation](#propagation)  
指定传播级别
3. readOnly  
是否只是可读
4. timeout  
超时
5. rollbackFor  
回滚的异常   
runtime Excetion 回滚  
必检异常不回滚
6. rollbackForClassName
7. noRollbackFor
8. noRollbackForClassName

<h5 id='propagation'></h5>

####propagation