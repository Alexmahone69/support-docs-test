# 数据平台快速接入

通过接入数据平台，快速接入日志平台。（仅限企业版）

## 接入步骤

### 计算平台数据采集

* 通过数据平台完成数据采集

导航路径：计算平台  →  数据集成  →  新接入数据源

![-w2020](media/16049162018738.jpg)

### 计算平台数据清洗

* 采集完成后，进行数据清洗，具体清洗流程根据数据特点，参照数据平台清洗说明进行

![-w2020](./media/bkdata_qingxi.png)

### 数据入库

* 清洗后新建入库，将数据入库到 ES 后，即可在日志平台查询

![-w2020](media/16049162364973.jpg)

入库配置项说明：

分词：一般比较长的文本可以选择，入库时会对文本按 ES 标准分词器进行分词。

聚合：入库 es 时会把 doc_values 设为 true，设置后在日志平台可用来做排序。

json：数据如果是 dict 类型，并且需要对子级进行查询可以选择。

### 日志平台查看计算平台的日志


通过创建索引集就可以满足日志的检索等可视化需求。
![](media/16619461142575.jpg)


