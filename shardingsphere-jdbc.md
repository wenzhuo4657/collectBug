

# Insert statement does not support sharding table routing to multiple data nodes.

![image-20250313161639115](https://blog.wenzhuo4657.org/img/image-20250313161639115.png)

```
        <dependency>
            <groupId>org.apache.shardingsphere</groupId>
            <artifactId>shardingsphere-jdbc-core-spring-boot-starter</artifactId>
            <version>5.1.1</version>
        </dependency>
```



这个版本不支持数据库自增作为分片列，请在java中手动填充。





# 归并引擎

```
25-03-14.11:10:31.255 [http-nio-8091-exec-2] INFO  ShardingSphere-SQL     - Actual SQL: db01 ::: select  IFNULL(MAX(id), 0)
        from user_credit_order_000 UNION ALL select  IFNULL(MAX(id), 0)
        from user_credit_order_001 UNION ALL select  IFNULL(MAX(id), 0)
        from user_credit_order_002 UNION ALL select  IFNULL(MAX(id), 0)
        from user_credit_order_003
25-03-14.11:10:31.256 [http-nio-8091-exec-2] INFO  ShardingSphere-SQL     - Actual SQL: db02 ::: select  IFNULL(MAX(id), 0)
        from user_credit_order_000 UNION ALL select  IFNULL(MAX(id), 0)
        from user_credit_order_001 UNION ALL select  IFNULL(MAX(id), 0)
        from user_credit_order_002 UNION ALL select  IFNULL(MAX(id), 0)
        from user_credit_order_003
<==    Columns: IFNULL(MAX(id), 0)
<==        Row: 0
<==        Row: 0
<==        Row: 0
<==        Row: 0
<==        Row: 0
<==        Row: 0
<==        Row: 0
<==        Row: 3
<==      Total: 8
Releasing transactional SqlSession [org.apache.ibatis.session.defaults.DefaultSqlSession@1643b70]

```



        <dependency>
            <groupId>org.apache.shardingsphere</groupId>
            <artifactId>shardingsphere-jdbc-core-spring-boot-starter</artifactId>
            <version>5.1.1</version>
        </dependency>
        


该版本默认使用UNION ALL 合并结果集，查询官网概念知道了归并引擎，待解决。

（目前可以使用查询所有结果集，然后在java代码中整理。）