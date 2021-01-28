## MySQL 学习笔记



**#查看mysql链接列表**

mysqladmin -uroot processlist



**#清空表数据**

truncate table table_name



##### \#插入或替换

**REPLACE** **INTO** students (id, class_id, name, gender, score) **VALUES** (1, 1, '小明', 'F', 99);

\#若id=1的记录不存在，REPLACE语句将插入新记录，否则，当前id=1的记录将被删除，然后再插入新记录。



##### \#插入或更新 

**INSERT** **INTO** students (id, class_id, name, gender, score) **VALUES** (1, 1, '小明', 'F', 99) **ON** DUPLICATE **KEY** **UPDATE** name='小明', gender='F', score=99;

\#若id=1的记录不存在，INSERT语句将插入新记录，否则，当前id=1的记录将被更新，更新的字段由UPDATE指定。

1：ON DUPLICATE KEY UPDATE需要有在INSERT语句中有存在主键或者唯一索引的列，并且对应的数据已经在表中才会执行更新操作。而且如果要更新的字段是主键或者唯一索引，不能和表中已有的数据重复，否则插入更新都失败。

2：不管是更新还是增加语句都不允许将主键或者唯一索引的对应字段的数据变成表中已经存在的数据。



##### \#插入或忽略

**INSERT** IGNORE **INTO** students (id, class_id, name, gender, score) **VALUES** (1, 1, '小明', 'F', 99);

\#若id=1的记录不存在，INSERT语句将插入新记录，否则，不执行任何操作。



##### \#快照

**CREATE** **TABLE** students_of_class1 **SELECT** * **FROM** students **WHERE** class_id=1;

*#对class_id=1的记录进行快照，并存储为新表students_of_class1*



##### **#写入查询结果集**

**INSERT** **INTO** statistics (class_id, average) **SELECT** class_id, AVG(score) **FROM** students **GROUP** **BY** class_id;

确保INSERT语句的列和SELECT语句的列能一一对应，就可以在statistics表中直接保存查询的结果



##### **#新增字段**

ALTER TABLE table add column `event` varchar(100) COLLATE utf8mb4_unicode_ci DEFAULT '' COMMENT '事件' after `action`



##### **#修改字段定义**

ALTER TABLE table modify column `action` varchar(1000) COLLATE utf8mb4_unicode_ci DEFAULT '' COMMENT '操作'



#### [**MySQL：日期函数、时间函数总结**](https://www.cnblogs.com/ggjucheng/p/3352280.html)



##### \#查询事务级别

SELECT @@tx_isolation;



##### \#查询当前正在运行的事务

SELECT * FROM information_schema.innodb_trx;



##### \#显示全部进程

SHOW FULL PROCESSLIST;



##### \#解析SQL 可以用于确认是否走了索引

EXPLAIN SQL



##### \#MySQL5.7关闭严格模式

sql_mode="STRICT_TRANS_TABLES,ERROR_FOR_DIVISION_BY_ZERO,NO_AUTO_CREATE_USER,NO_ENGINE_SUBSTITUTION"