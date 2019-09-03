## NoSQL
NoSQL是Not Only SQL的缩写。
提升性能的方式有两种：Scale-up和Scale-out。 Scale-up是购买更高性能硬件，以满足更高性能的数据读写要求。Scale-out是通过扩大规模，使用更多的小性能的硬件，通过一个分布式系统来满足更高性能的数据读写要求 (即：依靠横向扩展，通过不断增加廉价的商用服务器，来增加计算和存储能力)。

NoSQL是适应Scale-out的模式，这种分布式的模式并不能满足关系数据库的数据ACID原则的要求。NoSQL的设计，只能满足CAP（Consistency， Availability, Partition)之中，同时满足两个。

## Gremlin API - graph query language
图论API，针对图论数据库的查询语言。 

图论数据库是用来存储产品之间的相关联程度。比如，产品A和产品B之间是有关系的，他们关系的强弱可以使用一个权重值表示，每次购买产品A的同时也购买了产品B,则他们的权重加1. 使用实例，用来在购物网站做智能推荐。

![示例图](media/graph-example.png)

图论数据库由**结点**(nodes),**关系**(relationships)，以及结点可以有自己的**属性**(attributes)。

操作有创建，匹配(Match)，条件，返回等。比如，以下

```


MATCH (p:Product)
WHERE p.productName IN ['Chocolade','Chai']
RETURN p.productName, p.unitPrice;


```

## Partition key的概念

Partition是数据存储的分类依据，Partition Key相同的文档(documents)存放在同一块区域，使用partition Key来检索数据会获得**很高的性能**和**很少的代价**。

以零售订单为例，在Partition Key的选取时：
- 可以选取商品的ID作为Partition Key, 那么同一个商品的所有销售数据都存放于同一个Partition， 以商品的ID作为查询条件，则性能高，代价小。
- 可以选取顾客的ID作为Partition Key, 那么同一个顾客所购买的历史纪录数据都存放在同一个Partition, 以顾客的ID作为查询条件，则性能高，代价小。

![Partition Key示例图](media/partitionKey.png)

如果把数据存储看做时把鸡蛋放到篮子中，那么：
- 拥有相同Partition Key的所有文档(documents) 会被存放在同一个篮子里。
- 如果查询条件时Partition key, 那么就如同在同一个篮子中找文件，这样查找起来会高效。
- 如果查询条件不是Partition Key, 那么就如同在不同的篮子之间来回查找，则效率低下。

## 数据的分类

不同数据依据用途可以用不同的数据库存储， 数据可以分为：
- 结构化
- 本结构化
- 无结构

![数据的分类](media/data-classification.png)
