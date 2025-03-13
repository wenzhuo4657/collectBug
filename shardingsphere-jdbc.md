

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