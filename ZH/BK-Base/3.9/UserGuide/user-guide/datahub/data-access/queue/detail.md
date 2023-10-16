# 接入详情

接入详情页展示了接入状态, 并提供源数据接入的停止启动操作,

## 接入状态

接入状态包括统计总览和各个接入对象的接入状态.

统计总览包含正常, 异常, 运行中和停止状态. 数量都为 1. 点击刷新按钮可以查询最新的状态

![](../../../../assets/deploy_status_summary.png)

## 启停任务

这里可以停止/启动采集任务. 停止任务后, 数据不再采集.

![](../../../../assets/control_btn.png)

## 接入对象

接入对象展示了配置的采集 broker 、消费组、消费 Topic、最大并发度、加密方式等信息

![](../../../../assets/access_param_queue.png)



## 接入方式

这里展示配置的接入方式, 采集器为实时采集，暂时不可配置。

![](../../../../assets/access_method_http.png)


## 运行日志

运行日志展示每次部署的操作人和运行日志

![](../../../../assets/access_log_http.png)



## 操作历史

操作历史展示源数据的操作日志. 包含源数据接入, 停止, 启动及源数据相关任务的启停操作等.

![](../../../../assets/access_history_http.png)


