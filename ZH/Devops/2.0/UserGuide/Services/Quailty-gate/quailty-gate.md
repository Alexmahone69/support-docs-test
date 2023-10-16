# 质量红线

质量红线的思想起源于丰田精益生产的立即暂停系统（stop-the-line Andon），又称为安灯（Andon）系统。当车间生产流水线上的员工遇到麻烦，立即拉一下信号灯，班组长就会立即跑过来帮助解决，其生产流水线也会停止直到问题解决。这样能够尽早暴露问题，解决问题，而不是把问题流到生产汽车的后续步骤。

同样，在研发过程中，我们也经常会有类似的困惑：
- 确立了团队的编码规范，但还是有不符合规范的代码被合入；
- 拥有自己的转测试标准，但是只能人工跟进，不能落实到自动化流程中；
- 在版本的后期，Bug 数居高不下。但很多问题是可以在前期通过代码检查和单元测试发现的。
- 为了解决上述问题，借鉴丰田精益生产的思想，BK-CI 为大家打造了质量红线 Gate 服务。

![](../../assets/gate/quality-gate.png)

BK-CI 流水线拥有强大的编排能力，支持产品从开发、测试、安全扫描、部署，再到运营的整个生命周期。
而质量红线是指通过设置质量标准，控制流水线的行为，使得每一阶段的入口/出口质量都必须符合质量标准的一种服务。