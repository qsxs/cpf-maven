# CPF OHOS 临时 Maven 验收仓

公开 Maven 根：[https://qsxs.github.io/cpf-maven/](https://qsxs.github.io/cpf-maven/)。本仓仅作迁仓期间临时匿名验收，不是长期发行承诺，也不表示主应用已切换依赖。Pages 实际发布分支为 `codex/initial-maven`，由用户手动启用。

已验根坐标：

```text
com.github.qsxs.gridlayout-compose:grid:2.8.0-cpf11-preview-ed3472803fdb-40432726650-1
```

[Grid source `ed3472803fdb`](https://github.com/qsxs/gridlayout-compose/commit/ed3472803fdb637d601391f62f43aba1bfea551f) 经 [producer 40432726650/1](https://github.com/qsxs/cpf-port-tooling/actions/runs/40432726650/attempts/1) 八阶段与完整 Verify，通过 [Maven 制品提交 `7aeb4841317a`](https://github.com/qsxs/cpf-maven/commit/7aeb4841317a4db677a365bab458c5b281a31915) 一次发布完整 root/双 leaf 图。115 文件、474253B 与 staging 逐字节一致，匿名 HTTP 全量核验通过；后续 README 提交不改变该制品身份。

[consumer 40440852307/1](https://github.com/qsxs/cpf-port-tooling/actions/runs/40440852307/attempts/1) 已从匿名 Pages 重新解析根 GAV，经 GMM 选择两 Native leaf，核 root metadata/双 Klib 字节与实际编译输入，并通过标准 metadata、OHOS x64/arm64 三项真实编译。只依赖根 `grid`，不要绕过 GMM 直引 leaf；完整独立 OHOS 配置见 [Grid OHOS 文档](https://github.com/qsxs/gridlayout-compose/blob/codex/ohos-kotlin-2.4/ohos/README.md)。

验收边界：producer 全18份原源整体编译发布；consumer 只有一个现有用法编译探针。link/runtime、设备及 Android/iOS 回归均未运行，不称全部 API 已运行。临时 GAV 仅供独立 OHOS，其他平台保持原上游坐标/SDK；App 引用等 CPF 整体适配完成后另行切换。

所有来源与各自原许可证保留在对应 Fork 和附带制品中。新增版本须保留 POM/GMM/双 ABI Klib/sources/license/校验文件的完整原字节，不覆盖已验版本；工作流只交 staging/evidence，由 Root 核对后手动发布。官方制品替换需真实坐标、完整双 ABI/API、届时工具链兼容及独立消费验证后另行决定，不预填官方 GAV。

Windows urllib 对十个大文件曾固定截断6890B，curl原件全匹配；云端 consumer 匿名 HTTP 完整成功进一步区分了本机传输观察，不能归因库损坏。Grid 文档提交发布后安全暂停，不在本批启动其他库。
