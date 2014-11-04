#Python\_magic_function
魔法方法是Python里很重要的东西  
在这篇文章中给出常用的魔法方法
##Object creation

###1.\_\_new\_\_
cls()  _\_new\_\_(cls, ....) ==>  **对象构造器**
对象构造器

###2.\_\_init\_\_
\_\_init\_\_(self, ....) ==> **对象初始化器**


##Comparison

###3.\_\_eq\_\_
\_\_eq\_\_(self, other) ==> **==**

###4.\_\_ne\_\_
\_\_ne\_\_(self, other) ==> **!=**

###5.\_\_lt\_\_
\_\_lt\_\_(self, other) ==> **<**

###6.\_\_le\_\_
\_\_le\_\_(self, other) ==> **<=**

###7.\_\_gt\_\_
\_\_gt\_\_(self, other) ==> **>**

###8.\_\_ge\_\_
\_\_ge\_\_(self, other) ==> **>=**

##Miscellaneous methods

###9.\_\_call\_\_
\_\_call\_\_(self, ....) ==> **对象调用的时候**

###10.\_\_hash\_\_
\_\_hash\_\_(self, other) ==> **作为字典键**

###11.\_\_del\_\_
\_\_del\_\_(self, other) ==> **析构函数**

##sequence protocol methods

###11.\_\_iter\_\_
\_\_iter\_\_(self, other) ==> **iter()**

##Attribute access methods

###12.\_\_getattr\_\_
\_\_getattr\_\_(self, name) ==> **对象属性不存在的时候调用**

###12.\_\getattribute\_\_
\_\getattribute\_\_(self, name) ==> **获取对象属性时调用**

http://www.ironpythoninaction.com/magic-methods.html#id19