# 系统运维

## 可观测性

GSE系统可观测性基于metric、运营数据、分布式追踪等数据进行度量，以metric看板为例，其可在蓝鲸监控页面进行导入导出，主要关注的核心仪表盘如下:

- 任务服务监控（gse-task）;
- 文件服务监控（gse-file）;
- 数据服务监控（gse-data）;
- 基础平台服务监控（gse-cluster）;
- 服务运营总览(gse-op);
- 可观测性监控(gse-sla);

## 节点失联告警

GSE系统中的基础平台服务（GSE Cluster）基于数据服务（GSE Data）的OPS服务（内部运营数据上报通道），针对管控节点Agent失联事件进行上报。

**告警规则如下：**

- 每60秒作为一个周期将全局所有Agent的心跳记录进行检查；
- Agent的上一次心跳时间距离当前时间超过60秒且不大于24小时，则认为其已经失联执行失联上报，若超过24小时则不在进行告警，即其已处于长时下线状态；

## 系统监控指导建议

根据现网运维经验制定GSE系统运维监控指导说明。

**监控维度:**

| 维度 | 说明 |
| ----- | :---- |
| GSE Server | 针对GSE后台服务模块的监控，保证后台服务异常时可以快速感知 |
| GSE Proxy | 针对GSE Proxy节点上的Proxy Agent和GSE File、GSE Data进行监控，保证指定非直连区域异常时可以快速感知 |
| GSE Agent | 针对GSE管控的所有Agent节点，基于基础平台服务（GSE Cluster）的基础metric和运营指标进行监控，当发送节点大面积暴涨和失联波动时告警，保证系统海量管控节点有异常时能快速感知 |

**监控类型:**

- 进程监控：

| 维度 | 方式 | 作用 |
| ----- | :---- | :---- |
| 进程存活 | PS信息 | 当进程发送重启或退出时告警（需要注意的是，GSE的模块为双进程） |
| Core文件 | Core文件数量 | 当进程异常崩溃产生core文件时告警 |
| CPU | CPU百分比 | 当进程占用CPU过高时告警 |
| 内存 | 内存百分比 | 当进程所在机器内存过高时告警 |
| Load | Load负载值 | 当进程所在机器Load负载过高时告警 |

- 网络监控：

| 维度 | 方式 | 作用 |
| ----- | :---- | :---- |
| 端口存活 | 端口拨测 | 当服务端口没有正常Listen时告警 |
| 端口链接数 | 链接数量 | 当服务端口链接数大幅度波动时告警 |
| 端口链接状态 | 链接状态数量 | 当服务端口TIME_WAIT/CLOSE_WAIT/SYN_SEND等中间状态数量波动时告警 |
| 端口网络队列 | 网络队列挤压数量 | 当服务端口的网络收发队列产生挤压且未能及时消退时告警 |
| 节点网络延迟 | 网络延迟 | 当节点之间网络延迟过大时告警 |
| 链接断开 | 链接断开事件 | 当关键组件链接异常断开时告警 |

- Agent节点的监控：

管控节点数量较大且为用户侧环境，不宜人为定制化加入监控，故此需要基于GSE系统提供的基础监控数据，目前主要提供的监控维度如下：

| 维度 | 方式 | 作用 |
| ----- | :---- | :---- |
| 失联告警 | 由Cluster基础平台服务失联上报 | 当出现管控节点的Agent失联时告警 |

GSE Agent本身针对内存、CPU、网络等做了资源限制，故此在多种维度因素导致Agent重启失联时基础平台服务（GSE Cluster）会进行事件上报，用户可以基于蓝鲸监控进行告警感知。

**说明:** 详细监控配置和使用方式参见蓝鲸监控文档。
