# 公共脚本

公共脚本的功能和业务下的脚本管理是完全相同的，区别只是公共脚本面向的是平台全局的，而业务脚本面向的是单个业务，两者的使用对象维度不同。

![image-20211019161644711](media/image-20211019161644711.png)

功能介绍请参考 [脚本管理](./Scripts.md)

公共脚本提供的使用场景是，针对企业内部需要提炼一些通用的脚本提供给业务直接使用，统一由公共脚本维护者来管理/审核，例如：

- 公司/部门的系统运维组提供一些通用的服务器初始化脚本
- 公司/部门的 DBA 团队提供一些针对数据库通用场景的处理逻辑脚本，如 MySQL 安装、调优等等
- 公司/部门的配置管理岗提供一些通用的业务共性配置逻辑检查流程的脚本
- 诸如此类，等等...