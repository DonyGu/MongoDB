# 索引
## 概念
+ 建立指定键值及所在文档中的存储位置对照关系清单。使用索引可以方便我们快速查找，减少遍历次数，提高效率。

## 操作
+ 创建索引
    + `db.collection_name.ensureIndex()`
        + 功能：创建索引
        + 参数：提供索引的类别选项
            + 1表示为该域创建正向索引
            + -1表示逆向索引
        + e.g. 根据name域创建索引 `db.class.ensureIndex({'name':1})`
        + e.g. 根据name域,age域创建复合索引 `db.class.ensureIndex({'name':1，age:1})`
        + 系统自动为_id创建索引
+ 查看当前集合的索引
    + `db.collection_name.getIndexs()`
+ 删除索引
    + `db.collection_name.dropIndex()`
        + 功能:删除索引
        + 参数: 索引名称
        + _id 索引不能被删除
        + e.g.:`db.class.dropIndex({'name':1，age:1})`
+ 删除当前集合中除_id外的所有索引
    + `db.collection_name.dropIndexes()`
+ 显示详细的查找操作信息 
    + `explain()`
    + e.g. `db.class.find({age:22}).explain()`

## 索引类型
|类型|作用|例子|
|--|--|--|
|数组索引|如果对某个数组域创建索引，则对数组中的每个值均创建了索引。通过数组中单个值查询也会提高效率|`db.class.ensureIndex({hobby:1})`|
|子文档索引|某个域值为文档，对其子文档创建索引，则加快通过子文档进行查找的查找速度|`db.class.ensureIndex({'parent.child':1})`|
|唯一索引|唯一索引创建时希望索引的域值有不同的值，也可以通过这个方法限制域值|`db.class.ensureIndex({name:1},{'unique':1})`|
|覆盖索引|查找时，只获取索引项的内容，而不去连接其他文档内容。这样从索引表就可以到得到查询结果，提高查询效率|索引为name查找项也只有name `db.class.find({name:'a'},{_id:0,name:1})`|
|稀疏索引(间隙索引)|只针对有指定域的文档创建索引，没有该域的文档不加入索引|`db.class.ensureIndex({age:1},{sparse:true})`|
|文本索引|使用文本索引可以快速进行文本检索，这在较长的字符串搜索中比较有用，可进行多个关键词匹配，以空格隔开，如搜索内容包含空格，空格需要转义字符(\\"keyword\\"),'-'表示不包含|1. 创建文本索引`db.class.ensureIndex({msg:'text',description:'text'})` 2. 搜索文本索引`db.class.find({$text:{$search:"keyword1 keyword2"}})` 3.删除文本索引 通过getIndex()查看索引名，再通过dropIndex()删除|

## 索引约束
1. 影响插入，删除，修改数据的效率。当数据发生修改时，索引必须同步更新。
2. 索引也占有一定的空间，所以当数据量比较小时不适宜创建索引。

## 固定集合
+ MongoDB中可以创建大小固定的集合，称之为固定集合，固定集合性能出色且适用很多场景。如：日志处理，临时缓存
+ 特点：
    1. 插入输入快
    2. 顺序查询速度快
    3. 能够淘汰早期的数据
+ 创建固定集合
    + `db.createCollection('collection_name',{capped:true,size:10000,max:1000})`
        + size: 表示设置的固定集合的大小，单位kb
        + max：表示固定集合中最多存放多少条文档

