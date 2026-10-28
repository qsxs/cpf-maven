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
