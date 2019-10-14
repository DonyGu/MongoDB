# 游标

## 作用
1. 防止网络拥塞，造成数据传输满
2. 避免用户解析带来的体验差，可以进行后端解析

## 使用方法
MongoDB支持js

```
var cursor=db.class.find()//创建游标
cur.hasNext()//查看是否有下一条文档
cursor.next()//获取下一条文档内容
```