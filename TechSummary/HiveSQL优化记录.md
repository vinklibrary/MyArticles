## 引言
最近工作中会使用HiveSQL，作为Hadoop中的数据仓库，在公司里会大规模地使用到。熟练掌握HiveSQL优化的技巧，并且能够熟练地应用到工作中去是有必要的。本文将从常用手段以及后续的原理，以及上层地优化思想来详细介绍HiveSQL的优化。

## 软优化和硬优化


## MapReduce实现基本SQL操作的原理
在学习具体的HiveSQL优化之前，我们有必要学习下MapReduce实现基本SQL操作的原理，知其所以然后方能更好地理解优化过程。

### Join的实现原理
select u.name,o.orderid from oder o join user u on u.uid = o.uid
在map的输出value中为不同表的数据打上tag标记，key值为on后面的条件值。shuffle sort阶段就可以对key值排序分配，然后reduce阶段根据tag判断数据来源。Mapreduce的过程如下。

### GroupBy实现原理
select rank, isonline, count(*) from city group by rank, isonline;
在

## 常用的手段
### Join连接时的优化
1. 当三个或者多个以上的表进行join操作时，如果每个on使用相同的字段的字段连接时只会产生一个mapreduce。
2. 当进行多表查询的时候，从左到右表的大小顺序应该是从小到大。原因：hive在对每行记录进行操作的时候会把其他表先缓存起来，知道扫描最后的表进行计算。
3.

### Where的妙用

## HiveSQL优化背后的原理


## HiveSQL的上层思想


## 参考文献
1. HiveSQL编译过程 - 美团技术点评团队
2. 
