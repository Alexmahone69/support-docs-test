# 数据迁移内容总览

**迁移概览**：

1. 3.x 和 4.x 版本不能共存，可以在部署 4.x 版本后，在界面上进行升级
2. 迁移操作入口：管理 -> V3 迁移，可以根据需要迁移配置和数据


## 迁移说明
1. 请确认需要升级的采集项，并选择采集项对应的数据分类，确认无误后点击批量升级；
2. 如果不需要保留历史数据，请勾选【当前数据可丢弃，跳过数据确认环节直接迁移】，平台在迁移配置后正常使用
3. 如果需要保留历史数据，请确保新旧采集项在同一个 ES 集群，平台在采集项迁移后，将同时维持两份数据的采集。请在数据确认阶段，确认新采集数项的生效日期，确认后确认后平台将停止旧采集项并迁移数据。
 - 建议至少同时维持两天的采集，确保有完整的一天日志对新旧采集项进行比较
 - 对迁移的历史数据，平台会通过新增 index 别名，并修改 mapping 以兼容新版本
4. 历史数据的清理，可以保留 databus 服务进行定时清理，也可以根据 index 规则手动清理。


# 升级迁移细节

## 一、升级的内容

### 1. 采集项

1. 初次进入页面，需要强制升级，以业务为单位
2. 升级页面上，显示待升级的采集项
3. 点击“升级”，去创建新的采集项

### 2. 数据迁移

1. 前提：新老 INDEX 是在同一个 ES 集群

2. 物理索引
   V3（ES-INDEX）2_result_table_20200210

   V4（ES-INDEX）2_bklog_result_table_20200211

3. 迁移方式
   将 2_result_table_2020021001 新增一个别名 2_bklog_result_table_20200210

4. API 访问
   请求时间：20200210 -> 20200211 

   请求的 INDEX 同时访问新旧数据：
   2_bklog_result_table_20200210*，2_bklog_result_table_20200211*

### 3. 监控策略


## 二、升级步骤

以下为单个采集项讨论

### 1. 升级采集项 

- 流程

  1. 根据“采集项迁移细节”执行
  2. 执行部署下发操作
  3. 从日志检索采集项记录表中读取采集项对应的 bk_biz_id 及 dataid，并从数据平台获取采集项配置后，调用 V4 接口创建采集项并按直接入库方式入库
     2. V3 数据表：bk_log_search.home_application_bizdataid
     2. V3 采集项信息：/o/bk_log_search/config/get_deploy_plan_data/?&raw_data_id={data_id}&bk_biz_id={bk_biz_id}

- 问题点

  - 数据分类 需要确定

  - 是否需要自动部署，需要考虑 nodeman 性能压力

     

### 2. 迁移历史数据

- 前提

  - 新老索引必须在同一个 ES 集群

- 流程

  - 从日志检索采集项记录表中读取采集项对应的 bk_biz_id 及 dataid，并从数据平台获取采集项配置信息，对各个 dataid 所属的 ES 索引新增别名(信息与采集项配置一致)

  1. 拉取索引列表
  2. 给对应索引新增别名
  3. 平滑升级：如果需要无缝迁移历史数据，建议在第二天执行，并删除 V4 链路新增的索引，避免数据重复（可以通过 ES HTTP REST API 删除 V4 重复数据的索引）

### 3. 监控策略迁移

- 前提

  - 监控 V3.2 已部署
- 流程
  1. 拉取监控旧版本当前业务下的策略列表

  2. 根据 result_table_id 去过滤当前采集项的策略配置

  3. 调用监控新版本策略接口创建新的监控策略 (新旧策略字段转换待补充)

### 4. 旧采集项停用

- 调用数据平台接口，移除当前采集项 IP 的配置

  

## 三、采集项迁移细节

- 名称	
  - 中文名称
- 备注说明
  - 数据源描述
- 日志类型
  - 行日志文件
- 数据分类 - ？
  - 其他-其他
- 采集目标
  - 动静态混用虽然界面上支持，但是后台不支持
  - 如果混用，报错
- 日志路径
  - Windows 和 Linux 路径直接合并
- 过滤内容
  - 分隔符过滤
- 字段提取
  - 关
- 存储
  - 集群 - 继承
  - 索引名 - 2_bklog_原数据源名称
  - 过期时间 - 继承
- 查看权限
  - 将用户创建为新分组，基于 MD5 复用