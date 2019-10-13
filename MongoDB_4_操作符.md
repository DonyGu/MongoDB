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

## 修改器操作符
|序号|符号| 含义|
|--|--|--|
|1|$set|修改数据同时有增加域的作用|
|2|$unset|删除一个域|
|3|$rename|修改一个域的名称|
|4|$inc|对某个域的的值进行加减修改|
|5|$mul|对某个域的的值进行乘法修改|
|6|$min|设定最小值，查询到的域值小于设定值不变，否则设为min值|
|7|$max|设定最大值，查询到的域值大于设定值不变，否则设为max值|

+ e.g.: 删除a的age域 `db.class.update({name:'a'},{$unset:{age:0}})`
+ e.g.: 将文档中的所有的sex域修改为gender `db.class.update({},{$rename:{sex:'gender'}},false,true)`

## 数组修改器操作符
|序号|符号| 含义|
|--|--|--|
|1|$push|向数组中增加一项|
|2|$pushAll|向数组增加多项|
|3|$pull|数组中删除一个元素|
|4|$pullAll|数组中删除多个元素|
|5|$pop|弹出数组两端弹出元素，1最后一个元素，-1第一个元素|
|6|$addToSet|无重复添加元素，push可以添加重复项|

+ e.g. 添加多个hobby `db.class.update({name:'a'},{$pushAll:{hobby:['sing','football']}})`=`db.class.update({name:'a'},{$push:{hobby:{$each:['sing','football']}}})`

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

