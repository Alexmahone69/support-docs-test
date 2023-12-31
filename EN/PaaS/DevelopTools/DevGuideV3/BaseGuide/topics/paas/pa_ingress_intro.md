# 数据统计 - 访问日志统计简介

## 简介

“访问日志统计”是蓝鲸 PaaS 平台提供的一个应用数据统计功能。

该功能通过分析应用在平台上的访问日志（access log），提供其在不同时间段的汇总访问概况。所有平台应用默认都会打开这个功能，暂时不提供关闭选项。

> 注：如果你的应用创建于 2020 年 3 月 13 日前，那你可能需要重新部署应用，或者在“访问日志统计”页面点击“手动打开”按钮来使其生效。

- 该功能目前仅支持内部版蓝鲸应用使用
- 该功能暂不支持通过“子路径”模式访问的应用，如需开启，请先在 “应用引擎” -> “访问入口” 处切换访问方式

### “访问日志统计”与“网站浏览统计” 有什么区别

“访问日志统计”与“网站浏览统计”是数据统计的两个不同的功能分支。二者的主要区别在于：

- 网站浏览统计的数据来源于 JavaScript 脚本收集，所以只适用于用户使用浏览器访问的情况
- 网站浏览统计的 UV 计算基于 Cookie，数据可能更准确
- 网站浏览统计不会统计无关的 Ajax 请求或静态文件请求
- 访问日志统计的数据来源于 access log，所以应用接到的所有请求都会被统计到

### 访问日志统计的 UV 是怎么计算的

如果有多个请求（PV）满足以下条件，那么访问日志统计就认为它们来自同一个独立用户：

- 请求发生在同一天内
- 请求的 User-Agent 头信息一样
- 请求的来源 IP 一致

同一个独立用户会重复记录多次 PV，但是只会被记录成一次 UV。

### 为什么总 UV 数和“按用户维度”详细数据不一致

在使用访问日志统计功能时，你可能会发现总 UV 数与“按用户维度”区分的详细数据并不一致。最常见的情况是前者远大于“按用户维度”数据的总条数。

比如 UV 数为 50，但是“按用户维度”的详细数据里，只记录到了 3 个用户。这一般是由于以下几种原因造成的：

- **匿名用户请求**：未登录用户的请求里没有用户信息。 按照规则，这些访问量会被算入总 UV，但不会出现在“按用户维度”拆分的详细数据中
- **用户网络环境变化**：某用户在统计时间段内，IP 或者 User-Agent 发生了变化。根据上面的算法，请求会被算作多次 UV，但只会产生一条用户维度数据
- **统计数据延时**：按用户维度拆分的详情数据有一定时间的延时 *（通常为 15 分钟左右）*，而总 UV 数没有延时。这也可能导致二者不一致。

综上，为了获得比较准确的用户维度访问数据，建议接入“网站访问统计”功能。后者基于 Cookie 实现，可以提供更精确的用户统计。