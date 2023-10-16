# TRedis 实时关联数据(不推荐使用)

TRedis 实时关联数据支持一个实时动态数据与一个静态（更新不频繁）的关联计算。

图例，TRedis 实时关联数据

![](../../../../assets/dataflow/components/source/dataflow-tredis-kv-source.png)

#### 实时关联数据的来源
- 数据处理节点若下游接入 Tredis，其产生的结果表可作为关联数据
- 平台自身提供的公共关联数据，例如：cc 转换，ip 转化等
- 可通过平台数据集成中关联数据接入业务自己的关联数据集，具体操作请参照关联数据接入

#### 使用方式
TRedis 实时关联数据是以一个数据节点的方式在数据开发中存在的。将关联数据拖拽到画板上就可以，选择相关的结果表，关联数据的使用规则：

- 使用关联数据节点时画板上一定要有一个 "实时数据" 节点和一个 "实时计算" 节点
- "TRedis 实时关联数据" 节点不可以直接与 "离线计算" 节点关联
- 一个"实时计算"节点可以关联多个"TRedis 实时关联数据"节点

列举一个使用 TRedis 实时关联数据的案例：
![](../../../../assets/dataflow/components/source/dataflow-kv-source-example1.png)

选择 TRedis 实时关联数据节点之后，双击点击编辑，首先选择关联的数据集，如果你没有你想要的数据可以申请数据源。关联数据作为数据开发的开始节点，不存在上游节点。

#### TRedis 实时关联数据可以连接的子节点类型
- 实时计算
