# 告警源接入说明




集成指的是数据接入和周边服务接入，包含的内容有：

* 各种插件的制作
* 数据采集
* 采集的状态管理
* 依赖的服务对接
* 模版的制作

![](media/16613264026662.jpg)


## 通用能力


基于插件有各种分类和查询，快速找到对应的插件

插件的卡片模式，展示的内容有：

* 插件的LOGO
* 插件的名称
* 来源： 蓝鲸智云/部门/人
* 热度： 根据被业务应用的进行计数
* 已安装： 是属于本业务/可见范围的业务/全局
* 可用： 属于公共市场的资源


## 集成-事件插件


集成内的事件插件，主要是用于故障自愈获取第三方的告警事件，获取告警事件有很多种方式。

事件插件主要分为这几部分：

插件的基本信息

* 概述：主要是简单描述该插件的功能
* 配置：具体的配置和使用方法
    * 配置的地址信息
    * 接入的流程说明
    * 标准化事件-字段映射的规则
    * 告警名称列表，是用户通过工作台额外增加的内容
    * 数据状态：展示最近获取的原始数据情况

## 集成主流监控产品

告警源集成蓝鲸监控、4 款主流开源监控产品

* Zabbix
* Open-Falcon
* Prometheus
* 腾讯云监控


## 可自定义告警源





