# DB 接入常见问题解答

### UUID 主键类型的数据库表如何接入 

* 数据库采集中 ID 接入必须是整型类型，否则接入会失败。如果主键是其他字符串类型如 UUID 类型，可以使用时间字段接入。
* 若两种接入都不符合，则需要用户采用[自定义接入](../custom/concepts.md)的方式，使用自己的脚本通过 GSE 上报数据。

### MySQL 类型数据库接入时，为什么会有整数类型的字段被解析成 Bool 类型了

由于 MySQL 中的存储特性，bool 类型字段底层使用 tinyint 存储，因此 tinyint 类型的整数数据也会被解析为 bool 类型，后续在清洗流程中需要注意该字段的清洗规则。


