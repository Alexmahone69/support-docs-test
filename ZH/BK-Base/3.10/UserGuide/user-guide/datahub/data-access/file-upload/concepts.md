# 文件上传接入

## 简介

通过上传静态文件接入数据, 目前只支持 Excel、CSV\(支持 RFC4180\)格式的文件，文件需小于等于 10MB .

## 采集原理

通过上传符合标准的文件，解析文件并将文件内的数据接入平台。

## 接入准备

下载文件模板，准备文件数据

## 数据接入

### 数据信息

定义 了源数据的基础信息, 包含业务, 源数据名称等.数据源名称由用户自己定义, 在相同业务中不能重复

### 接入对象

上传指定文件

### 接入方式

采集方式只支持全量

采集周期只支持一次性

### 接入示例

![](../../../../assets/access_file_excample.png)


