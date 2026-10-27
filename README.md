# CPF OHOS 临时 Maven 验收仓

此仓只用于迁仓期间的匿名公开制品验收，不是长期发行仓，也不代表主应用已切换依赖。

当前没有通过完整 producer、发布和匿名消费者验收的版本。只有受控远程构建与完整 Maven Verify 通过后，才增加新的不可覆盖版本目录；不以缺件目录或占位 JAR制造可用版本。

所有第三方源码与各自原许可证保留在对应 Fork，制品附带来源与许可。分发目录应保持 POM、Gradle module metadata、两 ABI klib、sources、许可证及校验文件原字节。

拟定公开地址：https://qsxs.github.io/cpf-maven/ 。当前尚未启用 Pages；启用与匿名 HTTP 验收另行记录。

临时仓有容量边界，已验 MaterialIcons 单版本约85MiB；后续长期发布渠道仍需评估。
