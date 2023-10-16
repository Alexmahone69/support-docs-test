# 接入详情

接入详情页展示了接入状态, 并提供源数据接入的停止启动操作,

## 接入状态

接入状态包括统计总览和各个接入对象的接入状态.

统计总览包含正常, 异常, 运行中和停止状态. 数量都为 1. 点击刷新按钮可以查询最新的状态

![](media/deploy_status_summary.png)

## 启停任务

这里可以停止/启动采集任务. 停止任务后, 数据不再采集.

![](media/control_btn.png)

## 接入对象

接入对象展示了配置的采集 db 域名, 数据库名和表名

![](media/access_object_db.png)



## 接入方式

这里展示配置的接入方式![](media/access_param_db.png)



## 运行日志

运行日志展示每次部署的操作人和运行日志

![](media/access_log_db.png)



## 操作历史

操作历史展示源数据的操作日志. 包含源数据接入, 停止, 启动及源数据相关任务的启停操作等.

![](media/access_history_db.png)

## db 接入举例

Q: 假设在 2020-03-24 14:55 配置的 db 数据源(频率 5min, 数据延迟 1min)，从哪个时刻开始，判断为增量数据？

2020-03-24 15:01 开始拉取 2020-03-24 14:55~2020-03-24 15:00 的数据
2020-03-24 15:06 开始拉取 2020-03-24 15:00~2020-03-24 15:05 的数据


