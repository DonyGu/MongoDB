# 聚合
+ 对文档进行整理统计
+ `db.collection_name.aggtrgate()`
    + 功能：聚合函数，配合聚合条件进行数据整理
## 聚合操作符
|操作符|作用|例子|
|--|--|--|
|`$group`|分组|`db.class.aggregate({$group:{_id:'$age',num:{$sum:1}}})`|
|`$sum`|求和|`db.class.aggregate({$group:{_id:'$age',num:{$sum:1}}})`|
|`$avg`|求平均数|`db.class.aggregate({$group:{_id:'$sex',num:{$avg:'$age'}}})`|
|`$min`|求最小值|`db.class.aggregate({$group:{_id:'$sex',num:{$min:'$age'}}})`|
|`$max`|求平均数|`db.class.aggregate({$group:{_id:'$sex',num:{$max:'$age'}}})`|
|`$first`|第一个文档的指定值|`db.class.aggregate({$group:{_id:'$age',name:{$first:'$name'}}})`|
|`$last`|第一个文档的指定值|`db.class.aggregate({$group:{_id:'$age',name:{$last:'$name'}}})`|
|`$project`|用于修饰文档的显示结构，可以改变显示域名|`db.class.aggregate($project:{_id:0,Name:'$name'})`|
|`$match`|过滤数据|`db.class.aggregate($match:{age:{$lt:20}})`|
|`$limit`|显示前几条数据|`db.class.aggregate($limit:3)`|
|`$skip`|跳过几条数据|`db.class.aggregate($skip:3)`|
|`$sort`|排序|`db.class.aggregate($sort:{age:1})`|

## 聚合管道
+ 格式：将多个聚合操作放到一个[]中
+ e.g. `db.class.aggregate([$match:{age:{$lt:20}}，{$sort:{age:1}},{$project:{_id:0,Name:'$name'}}])`

