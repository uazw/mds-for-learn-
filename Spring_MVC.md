#Spring MVC
spring mvc 是一个强大并且灵活的web框架

##@MVC
* @Controller  用于注解到类表明是一个Controller
* @RestController 
* [@RequestMapping 用于注解到方法](#rm)
* [@ModelAttribute](#mt)
* @SessionAttributes 用法是将对象放入Model中就可


<h5 id='rm'></h5>
###@RequestMapping(details)
* value 路径
* method (http method)
* consumes 请求中的Content-Type
* produces 请求中的Accept
* params 请求参数对应

####@RequestMapping on method

#####supported arguments
* **ServletRequest** or **HttpServletRequest**  
* **Session** 线程不安全需要设置RequestMappingHandlerAdapters synchronizeOnSession true  
* **org.springframework.web.context.request.WebRequest org.springframework.web.context.request.NativeWebRequest**  
* **java.util.Locale**  
* **java.io.OutputStream or java.io.Writer**  
* **org.springframework.http.HttpMethod**  
* **@PathVariable** 用来注解参数提取URI的参数  
* **@RequestParam** 请求中的参数  
* **@RequestHeaders** HTTP首部  
* **@RequestBody** 请求体  
* **@CookieValue** 获取Cookie中的值
* **@RequestPart** 用来上传文件  
* **@HttpEntity** 用来获取HTTP headers and content  
* **Map** or **Model** or **ModelMap** 用来传输给View层  
* **BindingResult** or **Errors** 获取验证结果  
* **SessionStatus** 用来清除session attrubutes

######supported return types
* ModelAndView
* Model
* Map
* View
* String
* void
* HttpHeaders 返回一个头


<h5 id='mt'></h5>
###@ModelAttribute(details)

####On Method
用来增加Model attibutes  
当该注解标注在方法上表明这个方法在@RequestMapping之前执行(也可以获取到request的参数)

####On arguments
当标注在参数上表明要从其他地方需找这个实例  
1.  @SessionAttributes 用过这个的注解  
2.  @ModelAttributes 在同一个控制器用过这个的方法  
3.  data binding从请求参数中获取 类似于 ModelDriven 

###@ControllerAdvice

* basePackages 包名
* assignableTypes 类名


用该注解标注的类可以有以下方法注解
* @ExceptionHandler
* @InitBinder  
* @ModelAttribute