# Python操作MongoDB

## 安装
`sudo pip3 install pymongo`

## 创建mongo的对象
`conn=MongoClient('localhost',29017)`

## 选择要链接的集合
`db=conn.stu`

## 增
+ insert()
+ insert_many()
+ insert_one()
+ save()