# 操作符
## 比较操作符
|序号|符号| 含义|
|--|--|--|
|1|$eq|等于|
|2|$lt|小于|
|3|$lte|小于等于|
|4|$gt|大于|
|5|$gte|大于等于|
|6|$ne|不等于|
|7|$in|包含|
|8|$nin|不包含|

+ e.g. `db.class.find({age:{$eq:22}},{_id:0，name:1})`
+ e.g. `db.class.find({age:{$lt:22}},{_id:0，name:1})`
+ e.g. `db.class.find({age:{$in:[22,23]]}},{_id:0，name:1})`

## 逻辑操作符
|序号|符号| 含义|
|--|--|--|
|1|$and|逻辑与|
|2|$or|逻辑或|
|3|$not|逻辑非|
|4|$nor|既不也不|

+ e.g. `db.class.find({$or:[{age:{$lt:22}},{sex:'w'}]},{_id:0，name:1})`

## 数组查找
|序号|符号| 含义|
|--|--|--|
|1|$all|查找数组中包含多项的文档|
|2|$size|查找数组中项数为指定个数的文档|
|3|$slice|显示数组中的前几项|

+ e.g. 显示第一个 `hobby db.class.find({},{hobby:{$slice:1}})`
+ e.g. 跳过第一项，显示后两项 `hobby db.class.find({},{hobby:{$slice:[1,2]}})`

## 其他
|序号|符号| 含义|
|--|--|--|
|1|$exist|判断一个域是否存在|
|2|$mod|取余|
|3|$type|查找值为指定类型的文档|

+ e.g. 查找存在sex域的文档 `db.class.find({sex:{$exists:true},{_id:0}})`
+ e.g. 查找age能被3整除的文档 `db.class.find({age:{$mod:[3,0]},{_id:0}})`

## 查询常用函数
|序号|符号| 含义|
|--|--|--|
|1|distinct())|查看集合中某个域的值所覆盖的范围|
|2|pretty()|格式化输出|
|3|limit(n)|查询结果显示前n个文档|
|4|skip(n)|跳过前n条文档显示|
|5|count()|计数|
|6|sort()|按指定字段排序|
|5|count()|计数|

