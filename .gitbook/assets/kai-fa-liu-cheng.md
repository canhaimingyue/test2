## 开发流程

```sequence
participant 产品经理/业务负责人 as pdm
participant 项目经理/系统负责人 as pm
participant 开发人员 as re 
participant 测试人员 as qa
pdm->pm: 禅道提需求
note right of pdm:提供详细的需求文档
pm->pm: 和开发讨论需求的可行性
pm-->pdm: 需求不通过
note left of pm: 禅道反馈不通过原因
pm->re: 讨论通过
re->re: 编写设计文档
re-->pm: 设计评审
pm->pm: 召集需求相关人员评审需求
note right of pm: 讨论需求设计方案
pm->re: 确定研发排期以及上线计划
re->qa: 确定测试排期
re->re: 需求开发
note right of re: 开发结束需要有完整的单元测试案例
re-->pm: 需求分支提PR给系统负责人review
note left of re: PR链接复制到禅道上
pm->re: 反馈reivew结果
re->re: review过程中有问题则修改，重新提PR
re->qa: 修改项目状态，提交测试
qa->qa: 编写测试案例并测试
qa-->re: 禅道反馈测试结果
note left of qa: 反馈内容包括，测试案例以及测试bug
re->re: 评审测试案例或者修复bug
re->qa: 反馈评审结果
qa-->pm: 更新需求状态，禅道提交测试负责人评审
pm->re: 评审通过，代码合并到本次上线plan分支
re->re: 禅道创建发布任务
note right of re: 1.关联发布需求
note right of re: 2.[phantom]plan分支合并到master
note right of re: 3.[quickpay]plan分支合并到release
note right of re: 4.发送变更通知邮件
pm->qa: 测试负责人安排回归测试
qa->qa: 回归
qa-->pm: 回归测试提交测试负责人评审
note left of qa: 评审内容：回归测试报告
pm->qa: 反馈评审结果
note right of pm: 回归遗漏的地方要补充测试
qa-->re: 通知研发回归结束
re->re: 禅道创建发布需求
note right of re: 1.禅道上传变更单，变更方案
re-->pdm: 业务负责人变更审核
pdm->re: 签字通过
re-->qa: 测试人员测试审核
qa->re: 签字通过
re-->pm: 系统负责人变更审核
pm->re: 签字通过
re->re: 生产验证
note right of re: 验证本次需求功能以及存量业务
re-->pdm: 通知需求方生产验收
pdm->pdm: 生产验收
pdm->re: 反馈验收结果
note right of pdm: 验收结果需要禅道备注

```



