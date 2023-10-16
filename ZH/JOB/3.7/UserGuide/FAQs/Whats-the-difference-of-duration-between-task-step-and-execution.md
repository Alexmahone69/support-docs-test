# 任务耗时、步骤耗时和执行耗时，各代表什么含义

作业平台的一个任务内包含 3 种不同含义的耗时时间，分别为 `任务耗时` `步骤耗时` 和 `执行耗时，`三者之间的关系是 “任务耗时 包含 步骤耗时 包含 执行耗时”。

本章节将为大家说明这三种耗时时间所代表的具体含义：

### 1. 任务耗时

“任务耗时” 指的是一个完整的快速执行或作业任务的执行总耗时时长，是由作业平台的 任务执行引擎 计算产生的，计算方式是：`任务内所有相关的步骤处理时长总和 + 引擎自身的运行逻辑耗时`。

```text
特殊说明：在 "人工确认" 步骤停滞的时间也会算到任务耗时内
```

![image-20201015143725300](media/image-20201015143725300.png)

### 2. 步骤耗时

“步骤耗时” 指的是作业任务内单个步骤的执行耗时时长，是由作业平台的 任务执行引擎 计算产生的；因为单个步骤内可能会有多台执行主机，所以步骤耗时的计算方式是：`引擎自身的运行逻辑耗时 + (步骤内所有主机执行的最早开始时间 - 最晚结束时间)` 。

![image-20201015144027743](media/image-20201015144027743.png)

### 3. 执行耗时

“执行耗时” 指的是单个步骤内，具体某一台目标服务器的实际执行耗时，由于命令执行或文件分发最终是由 GSE 实施，所以该耗时取值来自于 GSE Server 执行完任务后返回的 startTime 和 endTime 差值。

![image-20201015144145804](media/image-20201015144145804.png)
