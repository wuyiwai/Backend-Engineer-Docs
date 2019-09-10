##### 参考:
- [一千行 MySQL 学习笔记](https://shockerli.net/post/1000-line-mysql-note/)

##### 思考:
- Inodb和MyIsam的区别
- 聚簇索引和非聚簇索引

##### MySQL优化
- 开启慢查询日志
- EXPLAIN
    - **id**：代表优先级  id值越大，越先执行，id值相同，从上往下执行。（比如示例的这条sql的执行计划，就是先执行第一行，再执行第二行）
    - **select_type**：表示select类型 取值如下
        - simple 简单表 即不使用表连接或者子查询
        - primary 包含union或者子查询的主查询 即外层的查询
        - union UNION中的第二个或者后面的查询语句
        - subquery 一般子查询中的子查询被标记为subquery，也就是位于select列表中的查询
        - derived 派生表 该临时表是从子查询派生出来的
    - **type**：表示MySQL在表中查找数据的方式，或者叫访问类型，以下对于type取值的说明 从上往下性能由最差到最好
        - all:全表扫描，MySQL遍历全表来找到匹配的行
        - index：索引全扫描，MySQL遍历挣个索引来查询匹配的行
        - range：索引范围扫描，常见于<、<=、>、>=、between等操作符
        - ref：使用非唯一索引或唯一索引的前缀扫描，返回匹配的单行数据
        - eq_ref：类似ref，区别就在于使用的索引是唯一索引，简单来说，就是多表连接中使用primary key或者unique index作为关联条件。
        - const/system：单表中最多有一个匹配行，查询起来非常迅速，常见于根据primary key或者唯一索引unique index进行的单表查询
        - null：mysql不用访问表或者索引，直接就能够得到查询的结果，例如select 1+2 as result。
    - **possible_keys**：表示查询时可能使用的索引
    - **key**：表示实际使用的索引
    - **key_len**：使用到索引字段的长度
    - **rows**：扫描数量
    - **Extra**：执行情况的说明和描述，包含不适合在其他列中显示但是对执行计划非常重要的额外信息，常用取值如下：
        - Using index：直接访问索引就取到了数据，高性能的表现。
        - Using where：直接在主键索引上过滤数据，必带where子句，而且用不上索引
        - Using index condition：先条件过滤索引，再查数据，
        - Using filesort：使用了外部文件排序 只要见到这个 就要优化掉
        - Using temporary：创建了临时表来处理查询 只要见到这个 也要尽量优化掉
- 关于子查询,尽可能看是否可以用join来优化,具体分析.