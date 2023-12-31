# 全文检索

## 功能介绍

全文检索提供基于 Elasticsearch 的数据查询功能，与 SQL 查询一样首先需要在左侧选择结果数据表，不同于 SQL 查询的是，全文检索不需要显式编写 SQL，只需输入相应检索关键字即可。

全文检索的结果展示比较丰富，不仅有结果数据的表格展示，还有对应数据分布图和关键字高亮，时间跨度支持分钟、小时、天、周和月。

### 全文检索示例如下

- #### 使用默认查询（即不输入关键字、不选择时间范围，此时会展示当天所有的数据）

![](../../../assets/datalab/es_default_query.png)

- #### 输入检索关键字进行检索

![](../../../assets/datalab/es_query.png)
