#Python_装饰器
python中的装饰器类似于JAVA中的AOP编程  
在不改变原本代码的情况下增加功能  
或者将与逻辑无关的代码（例如计时）与逻辑隔离  
装饰器可以由函数实现也可以由类实现  
装饰器本质是返回一个**可调用对象**

##1.函数装饰器

函数装饰器一般等价于

	foo(func)=>wrapper(func_args)
	A__init__(func).__call__(*args)

###1.函数实现

####1.无参实现
	def foo(func):
		def wrapper(*args):
			func(*args)
		return wrapper

	@foo
	def boo():
		print 'aaa'

####2.有参实现
	def d1(a, b):
		def d2(func):
			print a, b
			def wrapper(*args):
				func(*args)
			return wrapper
		return d2

	def b1(a, b):
		class wrapper(object):
			def __init__(self, func):
				super(wrapper, self).__init__()
				self.func = func
			def __call__(self, *args):
				print a, b
				self.func(*args)
		return wrapper
@b1(1, 2)
def bcc():
	print 'aa'
由以上可以看书有参比无参多一层调用

####2.类实现

	class A:
		def __init__(self, func):
			self.func = func
		def __call__(self, *args):
			func(*args)
	@A
	def book():
		print 'bbbb'


##2.方法装饰器

##3.类装饰器
类装饰器本质和函数装饰器没有不同  
但是需要注意的是第一层可调用的对象是  
传入的类

>类自动地传递给装饰器函数，并且装饰器的结果返回来分配给类名  
>直接的效果就是，随后调用类名会创建一个实例，该实例会触发装饰器所返回的可调用
对象，而不是调用最初的类自身