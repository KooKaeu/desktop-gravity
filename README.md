# Desktop Gravity / 桌面重力系统

让普通 Windows 应用窗口与桌面图标像现实物体一样下落、碰撞、弹跳并堆叠。

> **安全提示：** 只选择不含未保存重要工作的窗口。任何时候按 `Ctrl + Shift + G`，或点击“停止并恢复”。

## 系统要求

- Windows 10 22H2 或 Windows 11（x64）
- [.NET 8 Desktop Runtime](https://dotnet.microsoft.com/download/dotnet/8.0)

## 构建

```powershell
dotnet restore DesktopGravity.sln
dotnet build DesktopGravity.sln -c Release
dotnet test DesktopGravity.sln -c Release --no-build
dotnet run --project src/DesktopGravity.App/DesktopGravity.App.csproj
```

生成可复制到其他电脑、无需预装 .NET 的 x64 便携版：

```powershell
powershell -ExecutionPolicy Bypass -File scripts/publish-portable.ps1
```

启动入口是发布目录中的 `DesktopGravity.App.exe`。本项目不修改注册表或安装系统服务，因此卸载方式是退出程序后删除发布文件夹；完整说明随便携包提供。

## 三步使用

1. 点击“刷新列表”，勾选一个或多个普通窗口。
2. 调整重力、弹性和刷新率，点击“启动重力”。
3. 点击“停止并恢复”，或按 `Ctrl + Shift + G` 紧急停止。

“桌面图标重力”标签页会保存主显示器图标的原位置与图像，临时隐藏 Explorer 的真实图标，并在独立鼠标穿透覆盖层中以显示器刷新率实时绘制下落、碰撞和堆叠。结束时可以明确选择“停止并恢复原排版”或“一次性提交最终位置并保留堆叠”；紧急快捷键和退出程序仍默认恢复。

程序默认权限运行、不联网、不上传窗口信息，也不会自动控制新出现的窗口。设置位于 `%LOCALAPPDATA%\DesktopGravity\settings.json`，不保存窗口标题。

## 已知限制

- 管理员窗口、系统窗口、最小化窗口和部分特殊窗口会被跳过。
- 某些应用会主动恢复自身位置，可能产生抖动。
- DPI、多显示器切换以及真实窗口拖动仍需在对应 Windows 配置下手工验证。
- 窗口模式仍只有垂直重力；碰撞和水平运动目前只用于桌面图标。
- 图标模式当前只控制主显示器，Explorer 重启等异常情况下需要用户手工重新排列图标。

## 卸载

关闭程序，删除程序目录；如需清除设置，再删除 `%LOCALAPPDATA%\DesktopGravity`。程序不会写入注册表或设置开机启动。

路线图见规格书。发布前请执行 [Windows 手工验收清单](docs/manual-test-checklist.md)。贡献前请阅读 [架构](docs/architecture.md) 与 [安全说明](docs/safety.md)。项目采用 [MIT License](LICENSE)。English documentation: [README.en.md](README.en.md)。
