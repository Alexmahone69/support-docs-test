## 为什么要挂载 NFS

为了确保系统多实例部署时，每个实例一致性地访问到同一个文件，就必须为多个实例提供文件共享的机制，目前 NFS 成本最低，后期可以考虑接入其他分布式文件存储服务。

## 调用 ESB 组件失败

请联系 PAAS 管理员为为该应用添加 ESB 调用白名单。

## 为什么建议升级 Mysql 到 5.7

后期版本会基于 Mysql5.7 进行优化，主要是通过 5.7 版本的新特性来优化系统的性能，所以建议用户提前升级，降低后期数据迁移的成本。