# PCL MC 下载恢复版（第三方修改）

本仓库是 [listenlong/PCL-MC-Download-Restore](https://github.com/listenlong/PCL-MC-Download-Restore)，基于 [Meloong-Git/PCL](https://github.com/Meloong-Git/PCL) 的 `2.99.0.0`（提交 `6b9a50d`）修改而来。

**本仓库与龙腾猫跃（LTCat）及 PCL 官方没有任何隶属或背书关系。**

## 改了什么

PCL 2.99.0.0 通过 `ModSecret.RestrictMcDownload = True` 统一关闭了以下入口：

- 下载页的 Minecraft 原版 / OptiFine / Forge / NeoForge / Fabric / LiteLoader 安装向导；
- 已安装版本的“Minecraft”组件修改卡片；
- 整合包文件导入；
- 资源页中整合包版本的“安装”按钮。

本修改将该常量改为 `False`，从而恢复上述功能；其余下载、安装、启动逻辑保持上游原样。更新日志中的“删除 MC 下载功能”也已改为“恢复 MC 下载功能（第三方修改版）”。

## 为什么官方移除

PCL 官方在 2.99.0.0 的更新日志中写明，移除是“为遵守相关法律法规”的临时措施。本仓库仅用于个人学习、研究与备份，不构成法律意见。

使用或分发本修改版前，请自行确认你所在地区的法律法规、Minecraft EULA 以及 PCL 许可证的要求。请勿将本修改版用于商业倒卖或冒充官方版本。

## 构建

环境：Windows + Visual Studio 2022（MSBuild、.NET Framework 4.8 开发工具）+ .NET SDK（还原 `PCLCS`）。

```powershell
git clone --recurse-submodules https://github.com/listenlong/PCL-MC-Download-Restore.git
cd PCL-MC-Download-Restore
dotnet restore PCLCS\PCLCS.csproj
msbuild "Plain Craft Launcher 2\Plain Craft Launcher 2.vbproj" -p:Configuration=Release
```

产物位于 `Plain Craft Launcher 2\bin\`。仓库自带的 GitHub Actions `Build` 工作流会在 push 后分别构建 Debug 与 Release。

## 许可证与署名

上游代码使用《PCL 分发有限许可》与《PCL 存储库合理使用指南》，原文见 [LICENCE](LICENCE)。本仓库：

- 保留龙腾猫跃的署名、赞助链接与上游许可证；
- 公开全部源代码；
- 保留 Minecraft 正版购买劝导（`McLaunchPrecheck`）；
- 保留蓝色主题，不实现与官方赞助解锁类似的功能；
- 仓库名以 `PCL` 开头并带有明确的第三方修改后缀。

如果你基于本仓库继续分发，请同样遵守上述要求，并明确标注这是第三方修改版。
