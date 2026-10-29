# CPF OHOS 临时 Maven 验收仓

公开 Maven 根：`https://qsxs.github.io/cpf-maven/`；浏览器可查看 [GitHub 制品仓库](https://github.com/qsxs/cpf-maven)。本仓仅作迁仓期间临时匿名验收，不是长期发行承诺，也不表示主应用已切换依赖。Pages 实际发布分支为 `codex/initial-maven`，由用户手动启用。

已验根坐标：

```text
com.github.qsxs.gridlayout-compose:grid:2.8.0-cpf11-preview-ed3472803fdb-40432726650-1
io.github.qsxs.cpf.poko:poko-annotations:0.23.1-cpf11-preview-cbaa758d0b76-40451679040-1
io.github.qsxs.cpf.colormath:colormath:3.6.1-cpf11-preview-86f87c1c333f-40461897858-1
io.github.qsxs.cpf.materialkolor:material-kolor:5.0.0-cpf11-preview-c5ef77766b60-40672306467-1
io.github.qsxs.cpf.materialkolor:material-color-utilities:5.0.0-cpf11-preview-c5ef77766b60-40672306467-1
io.github.qsxs.cpf.colorpicker:colorpicker-compose:1.2.0-cpf11-preview-779519a9bc21-40674004251-1
io.github.qsxs.cpf.reorderable:reorderable:3.1.0-cpf11-preview-85707894c99f-40715768847-1
```

## Grid

[Grid source `ed3472803fdb`](https://github.com/qsxs/gridlayout-compose/commit/ed3472803fdb637d601391f62f43aba1bfea551f) 经 [producer 40432726650/1](https://github.com/qsxs/cpf-port-tooling/actions/runs/40432726650/attempts/1) 八阶段与完整 Verify，通过 [Maven 制品提交 `7aeb4841317a`](https://github.com/qsxs/cpf-maven/commit/7aeb4841317a4db677a365bab458c5b281a31915) 一次发布完整 root/双 leaf 图。115 文件、474253B 与 staging 逐字节一致，匿名 HTTP 全量核验通过；后续 README 提交不改变该制品身份。

[consumer 40440852307/1](https://github.com/qsxs/cpf-port-tooling/actions/runs/40440852307/attempts/1) 已从匿名 Pages 重新解析根 GAV，经 GMM 选择两 Native leaf，核 root metadata/双 Klib 字节与实际编译输入，并通过标准 metadata、OHOS x64/arm64 三项真实编译。只依赖根 `grid`，不要绕过 GMM 直引 leaf；完整独立 OHOS 配置见 [Grid OHOS 文档](https://github.com/qsxs/gridlayout-compose/blob/codex/ohos-kotlin-2.4/ohos/README.md)。

验收边界：producer 全18份原源整体编译发布；consumer 只有一个现有用法编译探针。link/runtime、设备及 Android/iOS 回归均未运行，不称全部 API 已运行。临时 GAV 仅供独立 OHOS，其他平台保持原上游坐标/SDK；App 引用等 CPF 整体适配完成后另行切换。

所有来源与各自原许可证保留在对应 Fork 和附带制品中。新增版本须保留 POM/GMM/双 ABI Klib/sources/license/校验文件的完整原字节，不覆盖已验版本；工作流只交 staging/evidence，由 Root 核对后手动发布。官方制品替换需真实坐标、完整双 ABI/API、届时工具链兼容及独立消费验证后另行决定，不预填官方 GAV。

Windows urllib 对十个大文件曾固定截断 6890B，curl 原件全匹配；云端 consumer 匿名 HTTP 完整成功进一步区分了本机传输观察，不能归因库损坏。

## Poko annotations

[Poko Fork source `cbaa758d0b76`](https://github.com/qsxs/Poko/commit/cbaa758d0b7610e0e445b8fd50739aa05afaea6e) 的 [producer 40451679040/1](https://github.com/qsxs/cpf-port-tooling/actions/runs/40451679040/attempts/1) 已完成 metadata、双 Native 生产及完整 staging Verify。[Pages 制品提交 `7c7abe30bb95`](https://github.com/qsxs/cpf-maven/commit/7c7abe30bb9510d0290794522471cb99469f6dac) 的 110 个文件、158468 字节与 staging 匿名逐字节对齐，既有 Grid 版本未被覆盖。

[consumer 第 1 次](https://github.com/qsxs/cpf-port-tooling/actions/runs/40457201932/attempts/1)的 Gradle 8.11.1 job 和[第 2 次](https://github.com/qsxs/cpf-port-tooling/actions/runs/40457201932/attempts/2)的 Gradle 9.5 job 分别从公开根 GAV 完成 metadata、OHOS x64 和 arm64 编译。Gradle 8 未加载 Poko 插件；Gradle 9 使用 0.23.2 插件，检查自有 probe 的三个生成声明签名和双 Native 非空 IR。第 2 次两个 job 均报告成功，详细证据分别采用 Gradle 8 第 1 次和 Gradle 9 第 2 次。

第 1 次 Gradle 9 因官方 sysroot 下载超时失败，随后第 2 次成功；第 1 次整体不能称为成功。未检查生成方法体，link、runtime、设备和 Android/iOS 回归均未验证。Pages 为临时验收仓，App 引用尚未切换。

## Colormath

上游 [ajalt/colormath 3.6.1](https://github.com/ajalt/colormath/commit/5e776b66ea6ffc5dc5dc360ab88ca5aefbd2a310) 的 45 份原源与 MIT 许可证由 [Fork source `86f87c1c333f`](https://github.com/qsxs/colormath/commit/86f87c1c333f0eb68af52afc88b73d82a536d6cf) 保留；[producer 40461897858/1](https://github.com/qsxs/cpf-port-tooling/actions/runs/40461897858/attempts/1) 的工作流提交为 `49d54d239482838dc187ba6b1ce8c9f8cd8231c0`，共享工具内容锁为 `d0cff88fd1ea2e4f08bb4409f1c802cca0c7f285`。

[Pages 制品提交 `8b5e6932bb24`](https://github.com/qsxs/cpf-maven/commit/8b5e6932bb2490bca64f40e29e1f113090628274) 的 125 个文件、1,106,922 字节与 staging 经匿名 HTTP 逐字节对齐；[根 POM](https://qsxs.github.io/cpf-maven/io/github/qsxs/cpf/colormath/colormath/3.6.1-cpf11-preview-86f87c1c333f-40461897858-1/colormath-3.6.1-cpf11-preview-86f87c1c333f-40461897858-1.pom)对应上面列出的根 GAV。未覆盖先前版本。

[consumer 40668960640/1](https://github.com/qsxs/cpf-port-tooling/actions/runs/40668960640/attempts/1) 使用工作流提交 `b606affac816befd3b33269e57d9b79b89c31b0f` 和 Gradle 9.5.0，从匿名根 GAV 经 GMM 完成 common metadata、OHOS x64 与 arm64 编译，`Color.toHSL()` 探针及 9 个公开 HTTP 对象核验通过。只验证 Gradle 9.5.0，未单独验证 Gradle 8.11.1；链接、运行时、设备与 Android/iOS 回归未运行。App 尚未切换，不能据此认定 MaterialKolor 整体已完成。

## MaterialKolor 两模块

上游 [jordond/MaterialKolor 5.0.0](https://github.com/jordond/MaterialKolor/commit/13c67cfa5a724cb6dca7d15674b3ad2acf894853) 的主模块 23 份和 MCI 42 份原源由 [Fork source `c5ef77766b60`](https://github.com/qsxs/MaterialKolor/commit/c5ef77766b6098677d541e82f362b666a8a0fff2) 保留；[producer 40672306467/1](https://github.com/qsxs/cpf-port-tooling/actions/runs/40672306467/attempts/1) 的工作流提交为 `b606affac816befd3b33269e57d9b79b89c31b0f`，共享工具内容锁 A 为 `d0cff88fd1ea2e4f08bb4409f1c802cca0c7f285`。

[Pages 制品提交 `b2652094e033`](https://github.com/qsxs/cpf-maven/commit/b2652094e03379619138c7ec83ff614d5863a2a1) 的 280 个文件、1,994,693 字节与 staging 经匿名 HTTP 逐字节对齐；对应 [material-kolor 根 POM](https://qsxs.github.io/cpf-maven/io/github/qsxs/cpf/materialkolor/material-kolor/5.0.0-cpf11-preview-c5ef77766b60-40672306467-1/material-kolor-5.0.0-cpf11-preview-c5ef77766b60-40672306467-1.pom) 和 [MCI 根 POM](https://qsxs.github.io/cpf-maven/io/github/qsxs/cpf/materialkolor/material-color-utilities/5.0.0-cpf11-preview-c5ef77766b60-40672306467-1/material-color-utilities-5.0.0-cpf11-preview-c5ef77766b60-40672306467-1.pom)。

[consumer 40675388144/1](https://github.com/qsxs/cpf-port-tooling/actions/runs/40675388144/attempts/1) 使用工作流 `abadbfb0b5c33b35dfafdb966e8e759276c5de45` 和 Gradle 9.5.0，只直接依赖主模块根 GAV，经 GMM 传递解析 MCI、Poko、Colormath，并完成真实主题 API 的 metadata、OHOS x64、arm64 编译；39 条公开 HTTP 记录（38 个不同 URL）与各自 staging 记录对齐。Producer 和 consumer 各检查 54 项，即 6 个 MCI 类的三个生成方法在三个目标的 metadata 声明与签名；双 Native 另检查 IR 签名及非空 IR。

许可事实分别为：上游仓库根 LICENSE 和主模块发布 POM 为 MIT；MCI sources JAR 内 LICENSE 为 Apache-2.0，但 MCI 上游 POM 标注 MIT，现 CPF MCI POM 沿用旧 OHOS 配置标注 Apache-2.0。原始 POM 与 LICENSE 保留，不推断双许可。

未检查生成方法体，未单独验证 Gradle 8.11.1 消费；link、runtime、设备和 Android/iOS 回归未运行，App 引用尚未切换。

## ColorPicker Compose

上游 [skydoves/colorpicker-compose 1.2.0](https://github.com/skydoves/colorpicker-compose/commit/85f81afbccaf5c0837e402686b8db9d67cc74c59) 的 21 份原始 common 源与 Apache-2.0 许可证由 [Fork source `779519a9bc21`](https://github.com/qsxs/colorpicker-compose/commit/779519a9bc21278c9496a11c43828dc194cbe64c) 保留。[producer 40674004251/1](https://github.com/qsxs/cpf-port-tooling/actions/runs/40674004251/attempts/1) 与 [consumer 40676245219/1](https://github.com/qsxs/cpf-port-tooling/actions/runs/40676245219/attempts/1) 的实际工作流提交 B 均为 `abadbfb0b5c33b35dfafdb966e8e759276c5de45`，共享工具内容锁 A 为 `d0cff88fd1ea2e4f08bb4409f1c802cca0c7f285`。

[Pages 制品提交 `af5af74fb640`](https://github.com/qsxs/cpf-maven/commit/af5af74fb6409cb9d2bc165253594e583ac8c4c2) 的 140 个文件、606,736 字节与 staging 经匿名 HTTP 逐字节对齐；对应上面列出的 [ColorPicker 根 POM](https://qsxs.github.io/cpf-maven/io/github/qsxs/cpf/colorpicker/colorpicker-compose/1.2.0-cpf11-preview-779519a9bc21-40674004251-1/colorpicker-compose-1.2.0-cpf11-preview-779519a9bc21-40674004251-1.pom)。Producer 的 x64/arm64 各核验 53 个不同 API 名称，Native metadata 签名核查 50 个名称并另查 8 个枚举生成成员的 Native IR 签名；三个目标均验证 Compose 和 serialization 两个原有 `.08` 编译器插件，Compose runtime/foundation/ui 库依赖仍为 `implementation`。

Consumer 仅用一个探针覆盖 `HsvColorPicker` 的 `initialColor`/`onColorChanged`、`BrightnessSlider`、`ColorEnvelope.color` 和 `selectByColor(color, true)`；Gradle 9.5.0 完成 common metadata、OHOS x64、arm64 真实编译，12 个公开对象均首次请求成功且与 staging 对齐。Gradle 8.11.1 消费、link、runtime、设备和 Android/iOS 回归未运行，App 引用尚未切换。

## Koin 四模块

上游 [InsertKoinIO/koin 4.2.2](https://github.com/InsertKoinIO/koin/commit/dc86ef8dd8fbe8564fb7453c03f5b738da3450bb) 的 114 份 common/Native 原源和 Apache-2.0 许可证由 [Fork source `4165003410d7`](https://github.com/qsxs/koin/commit/4165003410d767a5281441312f70d21dea4d6aab) 保留。[producer 40684515113/2](https://github.com/qsxs/cpf-port-tooling/actions/runs/40684515113/attempts/2) 使用工作流提交 B `4d01825448f83e87619888dade7e919562e8ecd4` 和共享工具内容锁 A `d0cff88fd1ea2e4f08bb4409f1c802cca0c7f285`。

四个根 GAV 已生产、发布并完成公开消费编译验证：

```text
io.github.qsxs.cpf.koin:koin-core:4.2.2-cpf11-preview-4165003410d7-40684515113-2
io.github.qsxs.cpf.koin:koin-core-viewmodel:4.2.2-cpf11-preview-4165003410d7-40684515113-2
io.github.qsxs.cpf.koin:koin-compose:4.2.2-cpf11-preview-4165003410d7-40684515113-2
io.github.qsxs.cpf.koin:koin-compose-viewmodel:4.2.2-cpf11-preview-4165003410d7-40684515113-2
```

[Pages 制品提交 `4a430bb48508`](https://github.com/qsxs/cpf-maven/commit/4a430bb48508ba7ac948be3f052499262ce40957) 的 380 个文件、3,455,187 字节与 staging 经匿名 HTTP 逐字节对齐；可查看 [koin-core 根 POM](https://qsxs.github.io/cpf-maven/io/github/qsxs/cpf/koin/koin-core/4.2.2-cpf11-preview-4165003410d7-40684515113-2/koin-core-4.2.2-cpf11-preview-4165003410d7-40684515113-2.pom)。15 条项目边的上传输入与输出记录匹配（7 条 metadata、8 条 Native），但不是重新哈希全部 runner 输入；metadata CLI 参数在 runner 内核验，原始 `producer.json`/`arguments.txt` 未上传，不能独立复核各参数，Native 任务输入也不是完整 argv。

Stately 使用既有匿名 CPF `2.1.0-1.1.0` 制品，15 个对象身份匹配，不表示新构建或普遍 ABI 兼容。[consumer 40703356336/1](https://github.com/qsxs/cpf-port-tooling/actions/runs/40703356336/attempts/1) 在 metadata 阶段下载 sysroot 超时；正常重试的 [/2](https://github.com/qsxs/cpf-port-tooling/actions/runs/40703356336/attempts/2) 使用工作流 `ed0e29a75c6f2a8a31af4a1c0ae68b8e170ffb0d` 和 Gradle 9.5.0，完成 Scope/ViewModel 探针的 common metadata、OHOS x64、arm64 编译。该次使用 K/N 标准按需下载，预填候选未应用。四模块的 48 个公开对象与 staging 对齐，依赖边和三个解析配置已独立核对。转换后的四个 metadata Klib 只保留 runner 路径、大小、SHA 和 metadataTrace，未上传本体，无法在本机独立重算内部成员；Native Klib 完整文件 SHA 可与 staging 对齐。Gradle 8 消费、link、runtime、设备与 Android/iOS 回归未验，App 引用尚未切换。

## Reorderable

上游 [Calvin-LL/Reorderable v3.1.0](https://github.com/Calvin-LL/Reorderable/commit/66de5751227c440bcdbd63acc94999231ed67487) 的 9 份原源与 Apache-2.0 许可由 [Fork source `85707894c99f`](https://github.com/qsxs/Reorderable/commit/85707894c99f8ce4c3fe10a84c870c71cee0b10b) 保留。[producer 40715768847/1](https://github.com/qsxs/cpf-port-tooling/actions/runs/40715768847/attempts/1) 使用工作流 B `8fd0a63cf246b2b8e90132b091506b49c9ebfb26`、共享工具内容锁 A `d0cff88fd1ea2e4f08bb4409f1c802cca0c7f285`，完成 metadata 与双 ABI 生产；每 ABI 核验 43 个 Native metadata 名称和 4 个枚举 IR 签名。Runner 物理输入已清理，记录与来源锁匹配，但不能在本机重新哈希。

已发布根 GAV 为 `io.github.qsxs.cpf.reorderable:reorderable:3.1.0-cpf11-preview-85707894c99f-40715768847-1`（[根 POM](https://qsxs.github.io/cpf-maven/io/github/qsxs/cpf/reorderable/reorderable/3.1.0-cpf11-preview-85707894c99f-40715768847-1/reorderable-3.1.0-cpf11-preview-85707894c99f-40715768847-1.pom)）。[Pages 制品提交 `3d5fe28dcc5b`](https://github.com/qsxs/cpf-maven/commit/3d5fe28dcc5b3a4cf326a8c413e649d7e0e2746a) 的 140 个文件、565,377 字节与 staging 匿名核验全部对齐；期间 15 次传输超时后重试，最终 140/140 匹配。

[consumer 40719398970/1](https://github.com/qsxs/cpf-port-tooling/actions/runs/40719398970/attempts/1) 使用工作流 B `2f30528fb9e0a90164d111788d701fd177897e63` 和 Gradle 9.5.0，完成 1328B LazyList/LazyGrid 状态、item 和两种拖拽 handle 探针的 metadata、OHOS x64、arm64 编译；12 个不同公开对象均首次 HTTP 成功并与 staging 对齐，三配置选择正确 root/leaf，Native Klib SHA 和 IR 已独立核对。Metadata 转换 Klib 原件未上传，不能在本机独立重哈希其内部成员。Gradle 8 消费、link、runtime、设备和 Android/iOS 回归未验，App 引用尚未切换。

## ComposeCharts

[上游 ComposeCharts 1.0.0](https://github.com/ehsannarmani/ComposeCharts/commit/8553b2bdbe209187fbba4fa3b567ce2fb978206a) 的 41 common 和 1 native 源由 [Fork source `bce8769199ad`](https://github.com/qsxs/ComposeCharts/commit/bce8769199ad65d406d0843dd7cc8806c1437b30) 保留；Prepare 校验固定 Git blob 与 sources JAR，避免将 Windows CRLF 工作树误认为 LF 原字节。上游 LICENSE 为 Apache-2.0，原 POM 和模块发布配置声明 MIT；按此前用户决定，CPF 私有 POM 标 Apache-2.0，保留原件且不推断双许可。

[producer 40800613406/1](https://github.com/qsxs/cpf-port-tooling/actions/runs/40800613406/attempts/1) 使用工作流 B `03ca69673f5875030198588b972a9ff21f35732e` 和工具锁 A `d0cff88fd1ea2e4f08bb4409f1c802cca0c7f285`，完成 metadata 和双 ABI 生产；每 ABI 核对 604 个 metadata 名称及 4 个枚举的 16 条生成 IR 签名。Runner 物理输入和原编译输出未保留，不能在本机重新哈希。根 GAV：`io.github.qsxs.cpf.charts:compose-charts:1.0.0-cpf11-preview-bce8769199ad-40800613406-1`（[根 POM](https://qsxs.github.io/cpf-maven/io/github/qsxs/cpf/charts/compose-charts/1.0.0-cpf11-preview-bce8769199ad-40800613406-1/compose-charts-1.0.0-cpf11-preview-bce8769199ad-40800613406-1.pom)）。

[Pages 制品提交 `65b972781ab9`](https://github.com/qsxs/cpf-maven/commit/65b972781ab9f6dd23c613f6c8a04615236d118d) 的 170 文件、1,716,733 字节在修正批次中与 staging 匿名核对 170/170 匹配，该批零重试；此前一次本机 POM 请求超时，上一轮统计汇总无效。Consumer 工作流 B `f06a5b40ce0e6e458ce42c6a9572663502c4ea24` 的 [40802580898/1](https://github.com/qsxs/cpf-port-tooling/actions/runs/40802580898/attempts/1) 核对 13 个公开对象并解析三配置后，在 metadata 准备阶段下载 sysroot 连续 10 次连接超时失败；[/2](https://github.com/qsxs/cpf-port-tooling/actions/runs/40802580898/attempts/2) 和 [/3](https://github.com/qsxs/cpf-port-tooling/actions/runs/40802580898/attempts/3) 同样在该阶段超时失败；[/4](https://github.com/qsxs/cpf-port-tooling/actions/runs/40802580898/attempts/4) 使用 Gradle 9.5.0 完成 metadata、OHOS x64 和 arm64 真实编译。该次标准按需下载在 sysroot 出现 Connect timed out 后继续完成，同 runner 重试提案未应用；该次 13 个不同公开 Maven 对象均首次 HTTP 200，大小与 SHA-256 与 staging 对齐；三配置选择正确 root/leaf，sources JAR 的 41 common+1 native 源及 metadata manifest 与 Git 输入匹配，992B ColumnChart/LineChart/PieChart 探针完成三目标编译，双 Native Klib 输入 SHA 对齐。Metadata JAR 的 43 个成员与匿名 HTTP 和 runner trace 记录匹配；转换后 Klib 及 runner 物理输入未上传，本机不能独立重哈其内部。Gradle 8 消费、link、runtime、设备和 Android/iOS 回归均未验证，App 未切换；历史 Popup 坐标和标签/提示裁切问题仍按用户决定延期。

## Calendar（公开消费编译已验）

[上游 Calendar 2.10.1](https://github.com/kizitonwose/Calendar/commit/0e94f40b5849d92a6f1390b9e39a0d316c7d5408) 的 41 份 common 原源和 MIT 许可由 [Fork source `03ea871e06df`](https://github.com/qsxs/Calendar/commit/03ea871e06df80e2bd96bb11f94c0b389c07be15) 保留，并沿用两份 OHOS actual 和 `calendar_icu.def`。旧 sources JAR 中两份生成源码作为原件保留，不重复编译；Compose Resources 正式生成源码，上游无 `composeResources` 资产。Git blob 身份避免 Windows CRLF 工作树误报原始字节。

[producer 40814095761/1](https://github.com/qsxs/cpf-port-tooling/actions/runs/40814095761/attempts/1) 使用工作流 B `88afbf38d426240bc0923539630a2fb262df695c` 和工具锁 A `d0cff88fd1ea2e4f08bb4409f1c802cca0c7f285`，完成 metadata 和双 ABI 生产；每 ABI 包含主 Klib 与 ICU cinterop Klib，核对 17 个代表性 metadata 名称，不代表完整 API 逐项或运行验证。Runner 物理输入及输出未保留，本机不能重新哈希。根 GAV：`io.github.qsxs.cpf.calendar:compose-multiplatform:2.10.1-cpf11-preview-03ea871e06df-40814095761-1`（[根 POM](https://qsxs.github.io/cpf-maven/io/github/qsxs/cpf/calendar/compose-multiplatform/2.10.1-cpf11-preview-03ea871e06df-40814095761-1/compose-multiplatform-2.10.1-cpf11-preview-03ea871e06df-40814095761-1.pom)）。

[Pages 制品提交 `299a43ce93ad`](https://github.com/qsxs/cpf-maven/commit/299a43ce93ad6786940cb4a89362ae43812f759c) 的 150 文件、1,042,859 字节在修正批次中与 staging 匿名核对 150/150 匹配，该批零重试。此前 consumer 工作流 B `fc8690060ba0d989e51829a07c9201ede67949e4` 的 [40815939032/1](https://github.com/qsxs/cpf-port-tooling/actions/runs/40815939032/attempts/1) 在 Resolve 下载宿主 `org.jetbrains:annotations:23.0.0` 时连接超时；[/2](https://github.com/qsxs/cpf-port-tooling/actions/runs/40815939032/attempts/2) 的 Resolve 成功，但 metadata 准备阶段下载 sysroot 连续 10 次连接超时失败；[/3](https://github.com/qsxs/cpf-port-tooling/actions/runs/40815939032/attempts/3) metadata 任务通过（独立证据复核待完成），NativeX64 因 `skiko-ohosx64-api` 与 `skiko-ohosx64` 的 `unique_name` 相同失败，arm64 未运行；用户批准按 producer 接线，脚本提交 [`04a3f59830287f6180648bf6665ea403d028ae7d`](https://github.com/qsxs/cpf-port-tooling/commit/04a3f59830287f6180648bf6665ea403d028ae7d) 声明并应用 Compose 插件 `1.12.0-0.1.0-11`，沿用 `rendererBackend=skia`；插件含 OHOS 依赖版本对齐及 Skia 模式下 Skiko api/fusionrenderer 请求替换为同 ABI 完整 Skiko 的规则；[新 consumer 40820357469/1](https://github.com/qsxs/cpf-port-tooling/actions/runs/40820357469/attempts/1) 的 Resolve 已将 x64/arm64 的 api/fusionrenderer 请求选为各自完整 Skiko `0.150.1-0.1.0-10`，随后 metadata 因 CPF Maven develop 的 Compose/serialization compiler `.08` POM 连接超时失败；[/2](https://github.com/qsxs/cpf-port-tooling/actions/runs/40820357469/attempts/2) 正常重试以 Gradle 9.5.0 完成月、周日历探针的 metadata、OHOS x64 和 arm64 真实编译。18 个不同匿名对象均首次请求成功并与 staging 对齐，解析到的外部 GAV 均匹配固定 pins；双 ABI 的 Skiko api/fusionrenderer 请求只选中各自完整 Skiko `0.150.1-0.1.0-10`。双 ABI 主 Klib 与 ICU cinterop Klib 的编译输入 SHA-256 均与 staging 一致，cinterop manifest 保留 `-licu`；metadata JAR 的 45 个成员与公开 HTTP 和 runner trace 一致，转换后的 Klib 与 runner 物理输入未上传，无法在本机独立重哈。

CPF `.08` sysroot `26.0.0.38-01` 是已批准并核验的外部 cinterop 输入，`libicu.so` 不打包；DevEco `26.0.0.105` 入口保留，但两者 ICU 库字节不同，完整 ABI 和 runtime 等价性未建立。Gradle 8、link、runtime、设备和 Android/iOS 回归未验，App 未切换，CAL-R1 仍延期。


## Lyricist 与 Lyricist-core

[Fork source `fad3d9091c75`](https://github.com/qsxs/lyricist/commit/fad3d9091c75927320da3511350202e681269b2a) 保留上游 Lyricist 1.8.0 两模块各一份完整 common 原源、MIT 许可与作者；`lyricist` 对 `lyricist-core` 为 `api`，coroutines 为 `implementation`，Compose runtime/ui 为 `compileOnly`；`lyricist-core` 的 coroutines 为 `implementation`，两模块保留 `explicitApi Strict`。

两个根 GAV 为 `io.github.qsxs.cpf.lyricist:lyricist:1.8.0-cpf11-preview-fad3d9091c75-40827525373-1` 和 `io.github.qsxs.cpf.lyricist:lyricist-core:1.8.0-cpf11-preview-fad3d9091c75-40827525373-1`；公开 Maven 根 `https://qsxs.github.io/cpf-maven/`（[lyricist POM](https://qsxs.github.io/cpf-maven/io/github/qsxs/cpf/lyricist/lyricist/1.8.0-cpf11-preview-fad3d9091c75-40827525373-1/lyricist-1.8.0-cpf11-preview-fad3d9091c75-40827525373-1.pom)、[core POM](https://qsxs.github.io/cpf-maven/io/github/qsxs/cpf/lyricist/lyricist-core/1.8.0-cpf11-preview-fad3d9091c75-40827525373-1/lyricist-core-1.8.0-cpf11-preview-fad3d9091c75-40827525373-1.pom)）。

[producer 40827525373/1](https://github.com/qsxs/cpf-port-tooling/actions/runs/40827525373/attempts/1) 使用工作流 `a2e3e537cfeffea4f9e63c70b190e46daddbd1ac`、共享工具锁 `d0cff88fd1ea2e4f08bb4409f1c802cca0c7f285` 完成 metadata 和 OHOS x64/arm64 生产及独立 staging 核验。Metadata 编译器库与 core 输出记录相符；Native 解析配置与 core 输出记录相符，但 Native 编译器 libraries、完整 compiler argv、taskDependencies 和 runner 物理输入未上传，不能在本机确认实际 Native 编译器输入或重哈这些路径。

[Pages 提交 `d4aeac15ad29`](https://github.com/qsxs/cpf-maven/commit/d4aeac15ad29f85497a733b133f12f2164322b44) 的 270 个文件、354,689 字节在修正匿名批次中与 staging 全部对齐，该批 270/270 首次请求成功；首轮将分隔符误计入响应 body，统计无效。 [consumer 40829692921/1](https://github.com/qsxs/cpf-port-tooling/actions/runs/40829692921/attempts/1) 使用工作流 `469293ce18774921a87627e756a617bff115b368` 和 Gradle 9.5.0，完成 `@LyricistStrings`、`rememberStrings`、语言 tag 和 `Lyricist.strings` 探针的 metadata、OHOS x64 与 arm64 真实编译；三个配置中 `lyricist` 通过 `api` 解析 `lyricist-core`，Compose runtime/ui 由 consumer 显式提供，不作为库的传递依赖。44 条公开 HTTP 记录与 staging 对齐，其中仅 38 条响应 body 随证据上传并可在本机复哈；四个 Native Klib 输入记录与 Pages/staging SHA-256 一致。两个 metadata trace 各有三个成员，但转换后的 metadata Klib 与 runner 物理输入未上传，无法本机独立重哈。

Gradle 8 消费、link、runtime、设备和 Android/iOS 回归未验证，App 引用尚未切换。Wheel 的 producer、Pages 及 Gradle 9.5 三目标公开消费编译已验；[consumer 40841841344/1](https://github.com/qsxs/cpf-port-tooling/actions/runs/40841841344/attempts/1) 完成业务探针编译，未获授权移除其 Lyricist 依赖。


## DateTime Wheel Picker

上游 Wheel 1.4.0 的完整 61 份 common 源包含 60 份 Git blob 与 1 份官方 sources JAR 的 KSP 生成 `Strings.kt`；33 语言、Apache-2.0 许可和作者保留，未重跑 Lyricist processor。Wheel 对 runtime、Material3、datetime 与 Lyricist 保持 `implementation`，Lyricist 对同版 core 为 `api`；所有 Wheel sourceSet 保留 `kotlin.time.ExperimentalTime` opt-in。

[producer 40839510773/1](https://github.com/qsxs/cpf-port-tooling/actions/runs/40839510773/attempts/1) 使用 source `18ea344423c94bff10c4bf7c43d1bbd408efafc9` 和 workflow `0862e8096aede7971366ae568f1e53a3dc108b3e`，完成 metadata、OHOS x64/arm64、Publish 和 Verify，staging 已独立核对。根 GAV 为 `io.github.qsxs.cpf.wheel:datetime-wheel-picker:1.4.0-cpf11-preview-18ea344423c9-40839510773-1`（[根 POM](https://qsxs.github.io/cpf-maven/io/github/qsxs/cpf/wheel/datetime-wheel-picker/1.4.0-cpf11-preview-18ea344423c9-40839510773-1/datetime-wheel-picker-1.4.0-cpf11-preview-18ea344423c9-40839510773-1.pom)）；公开 Maven 根为 `https://qsxs.github.io/cpf-maven/`。

[Pages 提交 `b826affc3704`](https://github.com/qsxs/cpf-maven/commit/b826affc370404ecedcd1b5fca418ad5eeae3940) 的 140 个文件、1,246,983 字节与 staging 匿名核对 140/140 一致，零重试。 [consumer 40841841344/1](https://github.com/qsxs/cpf-port-tooling/actions/runs/40841841344/attempts/1) 使用 workflow `0862e8096aede7971366ae568f1e53a3dc108b3e` 和 Gradle 9.5.0，仅直接依赖 Wheel 根，在 metadata、OHOS x64 和 arm64 中传递解析 Wheel→Lyricist→core，并实际编译 `WheelDatePicker`、`WheelDateTimePicker`、`timeFormatter` 与回调探针。66 条匿名 HTTP 记录与 staging 对齐；其中 57 条响应 body 随证据上传并可本机复哈，另 9 条仅保留 runner 记录。

Producer 未记录或上传完整 compiler argv 与 taskDependencies；consumer 转换后的 metadata Klib 和 runner 物理输入未上传，不能在本机独立重哈。Gradle 8 消费、link、runtime、设备及 Android/iOS 回归未验证，App 引用尚未切换；用户未授权移除 Lyricist 依赖。

## FileKit 0.16.0 OHOS（consumer 三目标编译已验）

[producer 40864370116/1](https://github.com/qsxs/cpf-port-tooling/actions/runs/40864370116/attempts/1) 使用 FileKit source `22683094fd5d30ef08441d073c797161804b9dc4` 和工作流 `e0116f36d402498b7a7fa2a6a37397ee5ec5b467`，完成 Metadata、OHOS x64/arm64、Publish 和 Verify；这些结果仅针对该次 producer。Metadata 的 LLVM 下载曾出现 EOF，重试后最终成功，不能将全部构建耗时归因于该下载问题。

两根 GAV 使用同一预览版本：

```text
io.github.qsxs.cpf.filekit:filekit-core:0.16.0-cpf11-preview-22683094fd5d-40864370116-1
io.github.qsxs.cpf.filekit:filekit-dialogs:0.16.0-cpf11-preview-22683094fd5d-40864370116-1
```

[Pages 源提交 `60752c680a23`](https://github.com/qsxs/cpf-maven/commit/60752c680a23322f8af23d9370677cb077011d31) 的 285 个文件、1,464,278 字节经匿名 HTTP 核对 285/285 与 staging 一致。dialogs 根同版 `arkts-sources@zip` 仅含 `FileKitShareFactory.ets`；上游与社区两份 MIT 许可均保留。

[consumer 40881058391/1](https://github.com/qsxs/cpf-port-tooling/actions/runs/40881058391/attempts/1) 已成功，使用 workflow `c4433b0c58150fafaa47696a6a72bc334e1d9d9b`、Gradle 8.11.1、JDK 17 和 Kotlin 2.4.20-0.1.0-08；source、version 与 producer fingerprint `9b6d8d85d7cb6b6ce547b55ae699f5a930433a87ce6e15b66bba96fecc6fb80c` 一致。Metadata、OHOS x64 和 arm64 三个任务实际执行成功；两个 ABI 分别选取对应平台的 core/dialogs KLIB，并核实 dialogs → core 传递边。49 次匿名请求均为 HTTP 200，其中归档的 36 份元数据可独立复核哈希；证据 ZIP 未包含编译输出二进制，不能独立重哈这些输出。

旧 P4 的完整 63 项矩阵、D019 内部短写计数、D022 原子回执及分享 drain、K3、其余 HEIC/图像矩阵和物理 ARM 等仍待验；P6 分享仍暂缓且非 PASS，OHOS 文件业务暂为 UTF-8，GBK 与共享 CSV 模板兼容延期。探针只覆盖 picker/readBytes、三参 init/session、saver、source/sink、两种压缩重载和 shareFile 调用的编译，不证明运行行为。consumer 收据中的 link、runtime、device、armDevice 和 ArkTS 编译均为 NOT_RUN。Android/iOS 平台及主工程 Gradle 门禁本次未验证；Android/iOS 和系统 SDK 不变，App 引用尚未切换。
