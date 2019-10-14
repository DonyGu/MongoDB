# 大文件存储
## 文件的数据库存储
1. 在数据库中以字符串的方式存储文件在本地的路径
    + 优点：节省数据库空间
    + 缺点： 当数据库或者文件位置发生变化时即无法找到文件
2. 将文件以二进制数据的方式存储在数据库中
    + 优点：文件和数据库绑定
    + 缺点：当存储文件大时，空间使用大，提取困难
3. MongoDB中存储大文件
    + GridFS：是MongoDB中存储大文件的一种方案，MongoDB中认为超过16M的文件为大文件
        + 将文件存储在MongoDB中，通过两个集合共同完成该文件的存储
        + `fs.files`:存储文件的相关信息，比如： 文件名fileName 文件类型 content_type
        + `fs.chunks`:实际存储文件内容， 以二进制方式分块存储，将大文件分成多个小块，每个小块占一条文档
        + 存入文件 命令行中`mongofiles -d dbname put filename`
        + 查看文件信息 db.fs.files.find()
        + 查看具体文件内容 
            + `db.fs.chunks.find({files_id:ObjctId('xxxx')})`
            + fs.chunks的域 
                + files_id:值为对应文件子啊fs.files集合中的文档的_id值
                + n:分块信息
                + data:集体文件内容
    + 优点：存储方便，没有文件个数限制，方便移植
    + 缺点：读写效率低，只能整体修改不能分块更新