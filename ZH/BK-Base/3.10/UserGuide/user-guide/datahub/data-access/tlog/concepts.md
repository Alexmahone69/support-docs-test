# TLOG 接入

## 简介

tlog 接入同日志接入类似. 优化了 tlog 日志的接入流程, 默认填充日志路径, 提供 tlog 表供用户选择

## 采集原理

同日志接入

## 接入准备

* job 执行权限. 采集器下发和重启都是依赖 job 来执行, 所以用户需要 job 执行权限

## 数据接入

### 数据信息

定义 了源数据的基础信息, 包含业务, 源数据名称等.数据源名称由用户自己定义, 在相同业务中不能重复

### 接入对象

* 采集范围: 按模块或者 IP 接入

* 日志路径支持通配符

* 操作系统当前支持 Linux 和 Windows

* TLOG 表: 用户选择该业务下的表名

* 首字符是否为分隔符. 若不选择, 则取第二个字段为过滤字段

* 字段分隔符, 可以修改, 默认为竖线\(\|\)

### 接入方式

采集器为实时采集, 暂时不可配置

#### 接入界面示例如下

![](../../../../assets/access_new_tlog.png)



