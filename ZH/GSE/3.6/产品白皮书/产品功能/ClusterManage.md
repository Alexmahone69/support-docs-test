# 集群管理

蓝鲸管控平台提供了一套有效的集群管理机制，让任务，文件，数据服务的自动服务发现，负载均衡等更加智能。

**自动服务发现**：管控平台同一个集群内的模块均支持自动发现，用户扩缩容任何节点，系统均能实时感知，并调整通讯策略，保证服务的高可用。

**集群负载均衡**：管控平台同一个集群内，支持按照 Agent 链接数，节点服务负载数据等进行负载均衡。

**Agent 状态查询**：管控平台提供接口，查询 Agent 状态。

接口按照实时性分为两类：

一类为实时状态接口，只能查询当前 Agent 是否正常；

二类接口提供 24s 内的状态查询，查询的内容包括 Agent 上次心跳时间、Agent 版本、Agent 使用的 cpu、Agent 使用的 mem。

**Agent 失连告警**：管控平台会监控 Agent 的心跳，心跳失连的 Agent 信息会通过告警的方式及时通知用户。

**多区域负载均衡**：管控平台支持对同一集群进行不同区域的划分，不同区域按照各区域内的负责均衡规则处理；未划分区域的 Agent 按照集群负载均衡策略处理。

