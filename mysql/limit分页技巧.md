# 分页技巧

是否最后一页 = 当前查询列表的数量 < 每页数量 

PS：注意如果最后一页列表数量和每页数量刚好一致将导致结果不正确。



## offset + size 方式分页

limit offset, size 方式依赖顺序，下一页offset等于 offset + size 或 offset + len(list)

id < offset order by id desc limit size 方式依赖顺序，下一页offset等于查询list最后一条记录 = 最小id

id > offset order by id asc limit size 方式依赖顺序，下一页offset等于查询list最后一条记录 = 最大id

**last_id** **这种方式适合移动端滚动分页，不适合****PC****端跳页**



## page + size 方式分页

offset = （page - 1）* size

limit offset, size 传统分页方式 当offset很大时，查询性能会变差， 可以返回last_id带入where条件减少扫表来优化 如 id > last_id order by id asc limit offset, size



## 分页优化

**如果主键id有序，可以使用子查询优化**

```mysql
SELECT * FROM user WHERE user_id >= (select user_id from user limit 800000, 1) limit 20
```



**如果主键id无序，可以使用inner join优化**

```mysql
SELECT a.* FROM user a JOIN (select user_id from user limit 800000, 20) b ON a.user_id = b.user_id
```

