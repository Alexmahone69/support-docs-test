# 日志检索

日志检索主要是用来快速定位问题，避免在服务器端进行日志的查询，优点是性能高效和工具便捷。

## 前置步骤

能够进行日志的检索，需要已经有数据源的接入并且形成**索引集**，才可以用来检索和监控。

![-w2020](media/15774208779344.jpg)

## 功能列表

* 日志检索和展示
* 过滤条件和 IP 快选
* 实时日志滚动
* 上下文
* 字段显示和排序
* 检索收藏

## 功能介绍

### 检索语句

支持 QueryString 语法和正则匹配。具体的查询语法查看[query string 详解](addenda/query_string.md)。

![-w2020](media/16049823794094.jpg)


### 过滤条件

**添加过滤条件**可以更精确的定位到日志内容。****

![-w2020](media/15774202479538.jpg)

### IP 快选

**IP 快选**通过关联 CMDB 的业务拓扑，控制日志检索范围。

![-w2020](media/15774202841325.jpg)



### 实时日志

**实时日志滚动。**

![-w2020](media/15774198565565.jpg)

**上下文查看。**

![-w2020](media/15774198794995.jpg)

### 字段显示和排序 

**字段显示和顺序，还有多列排序功能。**

![-w2020](media/15774197718914.jpg)

### 查询收藏 

![-w2020](media/16044636516379.jpg)

