#MongoDB
MongoDB是一个面向**文档**的数据库， 牺牲可用性， 换取一致性，和分区容忍性。  
MongoDB用BSON(Binary JSON)存储数据数据看起来就像如下这样:  
`{'name': 'uaZ'} `  
MongoDB是NO Schema的, 这也就是说一个表中可以存不同数据,但这里叫集合

##CURD(以下例子均在mongo shell中测试通过)
###1.create
	db.blog.insert({'x': 2});
###1.update
	db.blog.update();
###1.delete
	db.blog.delete(Criteria);
###1.find
	db.blog.find();
	db.blog.findOne();

##数据类型
###null
表示空值或者不存在的字段
###布尔
true / flase
###数值类型
mongoDB 默认为64位float
###字符串
如字面意思...
###日期
保存的为毫秒数
###数组
	{x: [1, 2, 3]}
###内嵌文档
	{'x': {'y': 2}}
###正则表达式

##detail in find
find的函数的一般形式为

find({条件}, {其他条件})

	find('x': 2, {'y': 1, 'z':0})

###复杂查询
1.范围查询  
**$lt $lte $gt $gte**

	find('x'：{'$gt': 6, '$lt': 2})  

2.OR查询

**$in $nin $or**

需要强调的是**$in $nin**是对**单**个键  
而 **$or** 是对应多键

	find('x': {'$in': [12, 14, 25]})

	find('$or': [{'x': 1}, {'y': 1}])

3.$not
	find({'$not': {'x': {'$in': [12,14,15]}}})

4.$exists

判断键值是否存在

##detail in update
在不使用修改器的情况下默认是修改整篇文档

	update({'x':1}, {'y':2})
**$set**用于修改键值

**$inc**增加或者减少数字

**push**用于添加数组元素 可与**each**搭配使用一次添加多个

	update(Criteria, '$push': {'key': '$each': [v1, v2, v3]})

##副本集
由一个主服务器， 和多个备份服务器组成。主服务器用于处理客户端请求。

###选举机制
* 对于主节点来说数据必须是最新的
* 对于数据来说写的时候写入大多数就是一致的
* 副本集必须在大多数的前提下才能选举主节点

###同步 & 跟新 & 回滚
* oplog节点所有操作都会记录在这个集合里面
* 备份节点会从同步源那里更新数据(oplog)

##分片
mongos
配置服务器
数据分片
片键
