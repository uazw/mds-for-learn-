#Spring MVC Config
Mvc config
##继承WebMvcConfigurerAdapter
WebMvcConfigurerAdapter

###Interceptor

org.springframework.web.servlet.HandlerInterceptor
为接口  
org.springframework.web.servlet.handler.HandlerInterceptorAdapter
为默认实现

* boolean **preHandle**(HttpServletRequest request,HttpServletResponse response, Object handler)
返回值true 继续执行
返回值flase 中断执行流程由拦截器负责结果

* void **postHandle**(HttpServletRequest request, HttpServletResponse response, Object handler, ModelAndView modelAndView):

* void **afterCompletion**(HttpServletRequest request, HttpServletResponse response, Object handler, Exception ex)
该方法在视图渲染后执行

####for more detail check me [intercepter]

###Content Negotiation(内容协商)
内容协商是指根据客户端的http request header中的 **Accept-type**  
返回对应的表示

###View Controllers
view Controllers是用于不需要执行一般的Controllers直接调用视图

###View Resolvers
* 视图的类型suffix(.jsp)和 位置prefix(/web-inf/jsp)
* 或者指定默认内容协商的实现**enableContentNegotiation()**

###ResourceHandlers
用于对静态文件的处理可以像Express中一样为资源重定位  
还可以设置缓冲时间  

	registry.addResourceHandler("/resources/**")
	.addResourceLocations("/public-resources/")
	.setCachePeriod(31556926)








[intercepter]: http://www.journaldev.com/2676/spring-mvc-interceptors-example-handlerinterceptor-and-handlerinterceptoradapter