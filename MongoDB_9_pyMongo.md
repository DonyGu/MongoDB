# Python操作MongoDB

## 安装
`sudo pip3 install pymongo`

## 创建mongo的对象
`conn=MongoClient('localhost',29017)`

## 选择要连接的数据库
`db=conn.stu`

## 选择要连接的集合
`my_set=db.class`

## 增
+ `insert()`
+ `insert_many()`
+ `insert_one()`
+ `save()`

## 删
+ 删除匹配到的所有项 `remove({'field_name':'value'})`
+ 删除匹配大的第一项 `remove({},multi=false)`
+ 删除全部数据 `remove()`

## 查
+ `find()`
+ `find_one()`
- 支持mongodb中所有操作符，只是在使用时要通过引号变为字符串形式

## 改
+ `upadte()`
+ `update_one()`
+ `update_many()`

## 文件存储
```

```