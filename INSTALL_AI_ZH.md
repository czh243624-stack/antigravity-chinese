# 让 AI 助手安装 Antigravity 中文界面

复制下面这句话给有本机文件和命令行权限的 AI 助手：

> 请按 https://github.com/czh243624-stack/antigravity-chinese/blob/main/INSTALL_AI_ZH.md 给我的 Windows Antigravity 客户端安装中文界面。先确认实际安装路径和版本，正常退出客户端，备份原版，再从这个仓库的源码构建补丁并安装；重启后检查界面是否显示中文。不要下载旧版本的 `app.asar` 直接覆盖，也不要修改我的登录资料、项目或对话。

## 给执行安装的助手

1. 确认用户使用的是 **Antigravity 桌面客户端**，而非独立的 Antigravity IDE。这个仓库的桌面补丁以 `resources/app.asar` 为目标。
2. 检查客户端版本和 `app.asar` 路径。默认安装位置通常在 `%LOCALAPPDATA%\Programs\Antigravity`；非默认安装位置需显式传 `--path`，例如 `E:\Antigravity\resources\app.asar`。
3. 检查 [上游项目](https://github.com/yiheng8023/antigravity-chinese) 的最新适配范围。若客户端更新，先在原版 `app.asar` 的副本上试装并验证，不要拿其他版本的预制 `app.asar` 覆盖。此 Fork 曾在 Windows x64 的 Antigravity **2.35.0** 上完成本机安装与主界面检查；这不保证以后版本或其他机器完全兼容。
4. 克隆本仓库，要求 Node.js 18 或更新版本。在仓库目录运行 `npm install --ignore-scripts --no-audit --no-fund`。先让客户端正常退出，确认无 Antigravity 进程，再运行：

   ```powershell
   node cli.js install --path 'E:\Antigravity\resources\app.asar'
   ```

   把示例路径换成实际路径。安装器会在 `resources` 下保留 `app.asar.bak`。记录备份文件和原版 SHA-256；安装失败时不要反复覆盖或强制结束进程。
5. 重新打开客户端，实际查看菜单、设置和会话界面。部分新文案、第三方插件内容或英文产品名可能仍显示英文。命令成功不等于界面验收通过。
6. 如需恢复英文，正常退出客户端后在仓库目录运行：

   ```powershell
   node cli.js restore --path 'E:\Antigravity\resources\app.asar'
   ```

   恢复前确认 `app.asar.bak` 属于当前安装版本，不要拿旧版本备份覆盖升级后的客户端。

本仓库是 [原项目](https://github.com/yiheng8023/antigravity-chinese) 的 Fork，使用 MIT 许可；它不是 Google 官方语言包。请保留原仓库的许可与署名。
