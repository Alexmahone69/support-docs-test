# TDM 接入

## 简介

TDM 接入同步提供了一种将腾讯数据大师(Tencent Data Master)的数据接入到平台的一种方式

## 采集原理

平台的 TDM 任务从 TDM 拉取数据到平台

## 数据接入

### 数据信息

定义了源数据的基础信息，包含业务，源数据名称等。数据源名称由用户自己定义，在相同业务中不能重复

### 接入对象

* SourceId

* EventName

* 业务特性 ID (选填项)

### 接入方式

接入方式为暂时不可修改，只提供实时增量的采集方式

#### 接入界面示例如下

![](../../../../assets/access_new_tdm.png)



