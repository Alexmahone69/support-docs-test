# 主机-操作系统-系统事件

系统事件，是内置主机操作和进程类的事件判断

### Agent 心跳丢失 

* 含义： 监测 GSE 的 Agent 是否正常
* 采集方法： 
    * gse 每隔 60 秒检查一次 agent 心跳数据。gse 从 agent 最后一次心跳数据更新开始，第 5 分钟、第 10 分钟、第 12 小时各触发一次告警事件。从第 24 小时起，如果心跳依然未更新则重复上述第 5 分钟、第 10 分钟、第 12 小时各触发一次告警事件的过程。
* 依赖： GSE 的服务上报

### 磁盘只读

* 含义： 监测磁盘的只读状态
* 采集方法：Linux
    1. 依赖 bkmonitorbeat 采集器, 在节点管理安装 
    2. 通过对挂载磁盘的文件状态 ro 进行判断，类似 Linux 命令：`fgrep ' ro,' /proc/mounts`

### 磁盘写满

* 含义： 监测磁盘的写满状态
* 采集方法：
     * Linux: 依赖 bkmonitorbeat 采集器, 在节点管理安装

### Corefile 产生

* 含义： 监测 /proc/sys/kernel/core_pattern 中目录内文件的变化
* 采集方法：Linux
     1. 查看 corefile 生成路径：`cat /proc/sys/kernel/core_pattern`，确保在某一个目录下，例如 `/data/corefile/core_%e_%t`
     2. 依赖 exceptionbeat 采集器, 在节点管理安装,会自动根据 core_pattern 监听文件目录

### Ping 不可达

* 含义： 监测管控的服务器 ping 的状况
* 采集方法：
     1. 依赖 bkmonitorproxy 采集器的安装，直连区域请联系管理员进行安装，非直连区域自动安装
     2. 由监控后台 bkmonitorproxy 去探测目标 IP 是否存活
* 支持： 所有被管控的服务器。

### 进程端口

* 含义： 进程端口不通
* 采集方法：
     1. Linux ：  bkmonitorbeat 上报数据匹配产生
     2. Windows： `wmic path win32_process get */value` 和 `netstat -ano`

### 主机重启

* 含义： 监测系统启动异常告警
* 采集方法：Linux
     1. 依赖 bkmonitorbeat 采集器的安装 ，在节点管理进行安装
     2. 检测原理：通过最近 2 次的 uptime 数据对比，满足`cur_uptime < pre_uptime`，则判断为重启


### OOM 告警采集原理说明 

- 说明
    蓝鲸监控中的 OOM 告警信息是由 bkmonitorbeat 采集器负责采集。OOM 告警信息采集会有两个来源：kernel log 及/proc/vmstat 中的 oom_kill 计数器。下面将会分别说明两个来源的采集匹配逻辑

- 采集器原理
    1. kernel log
        - 采集原理  
            exceptionbeat 是通过 Syscall 调用，获取内核当前缓冲区中的日志信息，然后匹配关键字`ut of memory:`。如果有匹配结果，采集器则认为系统发生过 OOM 事件，会将 OOM 告警信息上报。
            
            > 注意：由于内核日志缓冲区是会有清空的情况，因此 dmesg 任意时刻不一定会打印日志内容
        - 等价脚本
          
            ```bash
                dmesg | grep 'ut of memory:'
            ```
    2. oom_kill 计数器
        - 采集原理
            在 linux 4.13+内核版本中，增加了 oom_kill 计数器，该计数器记录了 OOM Killer 被激活的次数。如果发现本次采集 oom_kill 数量较上一周期有增加，则上报 OOM 告警
            
            > 注意：由于是从计数器中感知到 OOM 事件发生，所以产生的 OOM 事件并不能提供具体进程信息，统一会记录为 System 发生 OOM
        - 等价脚本
          
            ```bash
                grep 'oom_kill' /proc/vmstat
            ```
    
- 常见问题
    1.  /proc/vmstat 中没有看到 oom_kill 关键字？
        如上所述，该关键字是在 linux 4.13+中增加，请`uname -a`确认机器内核版本

    2. 两个采集手段的优先级？
        为了尽可能的采集 OOM 的进程信息，bkmonitorbeat 采集器优先会匹配 kernel log 中的关键字。如果 kernel log 中无关键字命中，再检查/prom/vmstat 中的 oom_kill 计数器是否有增加

    3. 采集器的采集周期是多久一次？
        由于内核日志的缓冲区是会存在清空的情况，所以 bkmonitorbeat 默认`每10秒`检查一次 kernel log。如果需要调整该频率，可以通过修改 bkmonitorbeat 采集器配置：
        
        ```yaml
        exceptionbeat:
            check_oom_interval: 10  # 单位秒
        ```



