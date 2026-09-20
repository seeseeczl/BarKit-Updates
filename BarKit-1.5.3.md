## BarKit 1.5.3 (16)

- 修复 Harness 安装失败：`env: node: No such file or directory`

  1.5.2 里安装 Harness 时会把 `npm` 交给子进程，但没有补 PATH；`npm` 是 `#!/usr/bin/env node` 脚本，而 BarKit 从 Finder/登录项启动时 PATH 很干净，于是找不到 `node`。现在安装与启动都使用补全后的 PATH。

- 搜索路径补充 `~/.hermes/node/bin`、Homebrew 的 `opt/node/bin` 以及 nvm 各版本目录，减少"找不到 node/npm"的情况

系统要求：macOS 13 或更高版本。Harness 安装需要本机有 Node.js / npm。
