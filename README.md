# CPF OHOS 临时 Maven 验收仓

此仓只用于迁仓期间的匿名公开制品验收，不是长期发行仓，也不代表主应用已切换依赖。

当前版本 `com.github.qsxs.gridlayout-compose:grid:2.8.0-cpf11-preview-ed3472803fdb-40432726650-1` 已通过受控 producer `40432726650/1` 八阶段、完整 staging 与发布图核验；source 为 `ed3472803fdb637d601391f62f43aba1bfea551f`，Maven 发布 commit 为 `7aeb4841317a4db677a365bab458c5b281a31915`。115 文件/474253B 已完成匿名 HTTP hash 验收；隔离远程 metadata/双 ABI consumer 尚待实际云编译，不能称全部验收完成。

所有第三方源码与各自原许可证保留在对应 Fork，制品附带来源与许可。分发目录应保持 POM、Gradle module metadata、两 ABI klib、sources、许可证及校验文件原字节。

公开地址：https://qsxs.github.io/cpf-maven/ 。Pages 已由用户手动启用。本机 Python 对十个大文件出现6890B截断，其他105文件匹配；无配置、无 auth/cookie 的原生 curl 已完整复核十个原件一致。该观察不作为制品损坏判断，不覆盖既有 GAV。

临时仓有容量边界，已验 MaterialIcons 单版本约85MiB；后续长期发布渠道仍需评估。
