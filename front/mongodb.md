### MongoDB基本语法
- 创建数据库且进入数据库
use database_name

- 查看所有数据库
show dbs

- 在当前数据库中插入表和内容
db.collection_name.insert({"name":"admin","password":"123"})

- 查看当前数据库
db

- 删除当前数据库(use 进入当前数据库后)
db.dropDatabase()

- 删除集合
db.collection_name.drop()

- 插入文档
db.collection_name.insert(document_value)

- 定义变量+插入变量
doucment_name=document_value
db.collection_name.insert(document_name)

- 更新文档
    - update()方法
db.collection_name.update(
  <query>,//查询条件
  <update>,//更新的对象和更新的操作符
  {//可选部分
    upsert: <boolean>,//如果不存在更新的内容是否插入，默认false
    multi: <boolean>,//是否只更新查询到的第一条记录,默认false
    writeConcern: <document>//抛出异常的级别
  }
)
    - save()方法
通过传入文档的方式来覆盖更新相同id的文档数据
db.collection_name.save(
  collection_value
)

    - 只更新第一条记录：
        - db.collection_name l.update( { "count" : { $gt : 1 } } , { $set : { "test2" : "OK"} } );

    - 全部更新：
        - db.collection_name .update( { "count" : { $gt : 3 } } , { $set : { "test2" : "OK"} },false,true );

    - 只添加第一条：
        - db.collection_name .update( { "count" : { $gt : 4 } } , { $set : { "test5" : "OK"} },true,false );

    - 全部添加加进去:
        - db.collection_name .update( { "count" : { $gt : 5 } } , { $set : { "test5" : "OK"} },true,true );

    - 全部更新：
        - db.collection_name .update( { "count" : { $gt : 15 } } , { $inc : { "count" : 1} },false,true );

    - 只更新第一条记录：
        - db.collection_name .update( { "count" : { $gt : 10 } } , { $inc : { "count" : 1} },false,false );

- 删除文档
db.collection_name.remove(
<query>,//删除文档的条件
{
  justOne: <boolean>,//设置为true或1，则只删除一个文档  加入时可以不写{ }大括号，直接在逗号后添加配置即可
  writeConcern: <document>//抛出异常的级别
}
)

- 删除集合中的所有文档
db.collection_name.remove({})

- 查询文档
db.collection_name.find().pretty() 格式化方式显示所有文档
db.collection_name.findOne()方法，只返回一个文档

- 操作
格式
范例
RDBMS中的类似语句
等于
{<key>:<value>}

- db.col.find({"by":"菜鸟教程"}).pretty()
where by = '菜鸟教程'
小于
{<key>:{$lt:<value>}}
db.col.find({"likes":{$lt:50}}).pretty()
where likes < 50
小于或等于
{<key>:{$lte:<value>}}
db.col.find({"likes":{$lte:50}}).pretty()
where likes <= 50
大于
{<key>:{$gt:<value>}}
db.col.find({"likes":{$gt:50}}).pretty()
where likes > 50
大于或等于
{<key>:{$gte:<value>}}
db.col.find({"likes":{$gte:50}}).pretty()
where likes >= 50
不等于
{<key>:{$ne:<value>}}
db.col.find({"likes":{$ne:50}}).pretty()
where likes != 50

- and条件查询
db.collection_name.find({key1:value1, key2:value2}).pretty()
- or条件查询
db.collection_name.find({$or:[{"key1":"value1"},  {"key2":"value2"}]})
- and和or联合查询
db.collection_name.find({"likes": {$gt:50}, $or: [{"by": "菜鸟教程"},{"title": "MongoDB 教程"}]}).pretty()
- $type操作符
db.collection_name.find({"name":{$type:2}}
类型
数字
备注
Double
1


String
2


Object
3


Array
4


Binary data
5


Undefined
6
已废弃。
Object id
7


Boolean
8


Date
9


Null
10


Regular Expression
11


JavaScript
13


Symbol
14


JavaScript (with scope)
15


32-bit integer
16


Timestamp
17


64-bit integer
18


Min key
255
Query with -1.

- Max key
127


- 读取指定数量的记录Limit()
db.collection_name.find().limit(number)

- 跳过指定数量的数据Skip()   默认参数为0
db.collection_name.find().limit(number).skip(number)

- 排序 sort()
key为1是升序排列，key为2是降序排列
db.collection_name.find().sort({key:number})

- 索引
索引是一种特殊的数据结构，储存在一个易于遍历读取的数据集合中，索引是对数据库表一列或多列的值进行排序的一种结构。索引也可以是多个字段构成的。
索引的创建
db.collection_name.ensureIndex({key:1});//1是按升序创建索引，-1是按降序创建索引
Parameter
Type
Description
background
Boolean
建索引过程会阻塞其它数据库操作，background可指定以后台方式创建索引，即增加 "background" 可选参数。 "background" 默认值为false。

- unique
Boolean
建立的索引是否唯一。指定为true创建唯一索引。默认值为false.

- name
string
索引的名称。如果未指定，MongoDB的通过连接索引的字段名和排序顺序生成一个索引名称。
dropDups
Boolean
在建立唯一索引时是否删除重复记录,指定 true 创建唯一索引。默认值为 false.

- sparse
Boolean
对文档中不存在的字段数据不启用索引；这个参数需要特别注意，如果设置为true的话，在索引字段中不会查询出不包含对应字段的文档.。默认值为 false.

- expireAfterSeconds
integer
指定一个以秒为单位的数值，完成 TTL设定，设定集合的生存时间。
v
index version
索引的版本号。默认的索引版本取决于mongod创建索引时运行的版本。
weights
document
索引权重值，数值在 1 到 99,999 之间，表示该索引相对于其他索引字段的得分权重。
default_language
string
对于文本索引，该参数决定了停用词及词干和词器的规则的列表。 默认为英语
language_override
string
对于文本索引，该参数指定了包含在文档中的字段名，语言覆盖默认的language，默认值为 language.

- 聚合
用于处理数据，如平均值，求和等。并返回计算后的结果。
db.collection_name.aggregate(aggregate_opration)
db.mycol.aggregate(  [
  {  $group :
    {  _id : "$by_user", num_tutorial :   {  $sum : 1  } }
  }
]  )

- 管道的概念
管道在Unix和Linux中将当前命令的输出结果作为下一个命令的参数。
MongoDB的聚合管道将MongoDB文档在一个管道处理完毕后将结果传递给下一个管道处理。操作管道还是可以重复的。
表达式：处理输入文档并输出。表达式是无状态的，只能用于计算当前聚合管道的文档，不能处理其他文档。

- 聚合框架中常用的几个操作
$project：修改输入文档的结构。用来重命名，增加或者删除域，也可以用于计算结果以及嵌套文档。
$match：用于过滤数据，只输出符合条件的文档。$match使用MongoDB的标准查询操作。
$limit：用来限制MongoDB聚合管道返回的文档数。
$unwind：将文档中的某一个数组类型字段拆分成多条，每条包含数组中的一个值。
$grounp：将集合中的文档分组，可用于统计结果
$sort：将文档排序后输出
$geoNear：输出接近某一地理位置的有序文档
