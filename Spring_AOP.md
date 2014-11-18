#Spring AOP

AOP即面向切面编程  
在完全不影响原有代码逻辑的情况下  
加入新功能

##AOP concept

1. 连接点 一般是要被添加功能的方法
2. 切点 表示切面发生时间
3. 通知 表示切面发生动作
4. 切面 通知+切点

#### AOP 指示集

1. args() 用于限定通知的参数
2. @args() 用于限定指定注解标注参数的方法
3. execution()  用于匹配执行方法
4. this()
5. target()
6. @target()
7. within() 限定类型或者包
8. @within() 限定匹配类型是标注了指定类型的注解
9. @annotation  限定匹配方法标注了指定类型的注解
10. bean() 用于限定bean名字

#####高效AOP
1. kinded designators  
excution()
2. Scoping designators  
within()
3. Contextual designators  
this target @annotation

所有的切点都应该包括第一二种  
scoping match的时候很快

###编码细节

	execution(modifiers-pattern? ret-type-pattern 
	declaring-type-pattern? name-pattern(param-pattern)
	throws-pattern?)

the execution of any public method:

	execution(public * *(..))

• the execution of any method with a name beginning with "set":  

	execution(* set*(..))

• the execution of any method defined by the AccountService interface:

	execution(* com.xyz.service.AccountService.*(..))

• the execution of any method defined in the service package:

	execution(* com.xyz.service..(..))

• the execution of any method defined in the service package or a sub-package:

	execution(* com.xyz.service...(..))

• any join point (method execution only in Spring AOP) within the service package:

	within(com.xyz.service.*)

• any join point (method execution only in Spring AOP) within the service package or a sub-package:

	within(com.xyz.service..*)

####XML

	<bean id="people"
             class="aop.People"></bean>
    <bean id="aoptalk"
             class="aop.AopTalk"></bean>
    <aop:config>
    	<aop:aspect ref="aoptalk">  <!-切面所需要的实现类--->
        	<aop:pointcut id="talk" <!-- 定义切点-->
            	expression="execution(* aop.People.talk(..))"></aop:pointcut>
            <!-- 定义通知-->
			<aop:before 
                 pointcut-ref="talk"
                 method="beforeTalk" />
            <aop:after method="afterTalk"
                 pointcut-ref="talk" />
       </aop:aspect>
	</aop:config>

####anno

	@Aspect
	public class AopTalk {

    	@Pointcut(value = "execution(* aop.anno.People.talk(..))")
    	public void talk() {

    	}
    	@Before("talk()")
    	public void beforeTalk() {
        	System.out.println("before talk");
    	}
    	@After("talk()")
    	public void afterTalk() {
        	System.out.println("after talk  ");
    	}
	}

@Pointcut注解的方法必须是void  
@Aspect 注解过的bean 仍然是个普通Bean需要手动注册
或者用@Compoent
