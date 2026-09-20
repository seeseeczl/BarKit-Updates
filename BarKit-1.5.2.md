## BarKit 1.5.2 (15)

- Harness 改为**应用内自带安装**：本机没有检测到 DeepSeek Harness 时，打开开关会提示「当前没有安装 Harness」并询问是否安装；确认后 BarKit 自己安装官方 npm 包 `@deepseek-ai/dsh` 到 `~/Library/Application Support/BarKit/Harness`，使用独立 npm 缓存，装完自动启动并打开带 token 的页面
- 不再依赖本机脚本与源码仓库：移除了 `start_harness.command` 与 `~/GitHub/deepseek-harness` 的硬编码路径；如果 PATH 上已有 `dsh`，直接复用不重复安装
- Harness 状态新增「未安装 / 安装中」；状态轮询改为 TCP 探测，不再每次启动子进程，菜单更跟手
- 关闭开关时先结束后台进程，再清理 3080 端口上的遗留 Harness 进程

系统要求：macOS 13 或更高版本。Harness 安装需要本机有 Node.js / npm。
