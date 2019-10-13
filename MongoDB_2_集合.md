# 集合操作
MongoDB集合的概念等同于SQL的表概念。
+ 创建集合
    1. `db.createCollextion()`
    2. 当向一个集合中插入一条文档，如果这个集合不存在，则会自动创建`db.collection_name.insert()`
+ 集合的命名规则
    1. 不能是空字符串
    2. 不能含有'\0'
    3. 不能以system开头，这是系统集合的保留前缀
    4. 集合不要和保留字重名不要包含$
+ 查看数据库中的集合
    + `show tables`或`show collections`
+ 删除集合
    + `db.collection_name.drop()`
+ 修改集合名称
    + `db.collection_name.renameCollection('newName')`
        + e.g. 将class1改名为class0 `db.class1.renameCollection('class0')`
+ 获取集合对象
    + `db.collection_name`
    + `db.getCollection('collection_name')`

