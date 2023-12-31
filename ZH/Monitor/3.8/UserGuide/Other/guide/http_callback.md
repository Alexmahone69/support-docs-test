# 如何设置告警回调

为了方便其他应用接入告警消息，告警通知提供回调功能，用户可以在告警组中注册一个回调地址，每次告警通知都会调用这个地址，发送相应通知消息。

## 功能说明

### 设置入口

位置：导航  →  监控配置  →  告警组  →  回调地址

![告警组设置截图](media/15833979854386.jpg)

### 回调确认

为了保证接收方接收到了通知消息，我们要求请求的返回值是 200，否则认为请求失败。

### 消息重试

为了接收方不会因为短暂的网络波动而收不到消息，我们有重试机制。有两次重试的机会，每次的时间间隔加大。

1. 第一次请求失败后，隔 5 秒重试
2. 第二次请求失败后，隔 10 秒重试
3. 第三次请求失败后，不再重试

### 超时

为了保证不会因为接收方的异常而导致回调处理进程被阻塞，回调请求显示了请求时间，超时请求一律认为请求失败。

超时时间由全局变量 **Webhook 超时时间** 控制，默认为 3 秒。

### 回调消息

POST 消息

```json
{
  "bk_biz_id": 2, # 业务ID
  "bk_biz_name": "蓝鲸", # 业务名称
  "latest_anomaly_record":{ # 最新异常点信息
    "origin_alarm":{
      "anomaly":{ # 异常信息
        "1":{ # 告警级别
          "anomaly_message":"avg(使用率) >= 0.0, 当前值46.17", # 异常消息
          "anomaly_time":"2020-03-03 04:10:02", # 异常产生事件
          "anomaly_id":"48af047a4251b9f49b7cdbc66579c23a.1583208540.144.147.1" # 异常数据ID
        }
      },
      "data":{ # 数据信息
        "record_id":"48af047a4251b9f49b7cdbc66579c23a.1583208540", # 数据ID
        "values":{	# 数据值
          "usage":46.17,
          "time":1583208540
        },
        "dimensions":{ # 数据维度
          "bk_topo_node":[
            "module|6"
          ],
          "bk_target_ip":"10.0.0.1",
          "bk_target_cloud_id":"0"
        },
        "value":46.17,	# 指标值
        "time":1583208540 # 时间
      }
    },
    "create_time":"2020-03-03 04:10:02", # 产生事件
    "source_time":"2020-03-03 04:09:00", # 数据事件
    "anomaly_id":6211913 # 异常ID
  },
  "type":"ANOMALY_NOTICE", # 通知类型 ANOMALY_NOTICE异常通知，RECOVERY_NOTICE恢复通知
  "event":{ # 事件信息
    "create_time":"2020-03-03 03:09:54", # 产生时间
    "end_time":"2020-03-03 04:19:00", # 结束时间
    "begin_time":"2020-03-03 03:08:00", # 开始时间
    "event_id":"48af047a4251b9f49b7cdbc66579c23a.1583204880.144.147.1",
    "level":1, # 告警级别
    "level_name": "致命", # 级别名称
    "id":8817 # 事件ID
  },
  "strategy":{
        "item_list":[
            {
                "metric_field_name":"使用率", # 指标名称
                "metric_field":"usage" # 指标
            }
        ],
        "id":144, # 策略ID
        "name":"测试策略" # 策略名称
    }
}
```

