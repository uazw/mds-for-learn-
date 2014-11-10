#Spring AOP

AOP即面向切面编程  
在完全不影响原有代码逻辑的情况下  
加入新功能

##AOP concept

1. 连接点 一般是要被添加功能的方法
2. 切点 表示切面发生时间
3. 通知 表示切面发生动作
4. 切面 通知+切点

###编码细节

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