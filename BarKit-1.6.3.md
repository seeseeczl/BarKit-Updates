## BarKit 1.6.3 (24)

- 完成全项目对抗性审计后的第一批修复

  Codex 配置切换现在按事务处理 `config.toml`、`models.json` 和状态文件；任一步失败都会回滚并尝试恢复旧 Codex。

- 损坏的 Codex 全局状态不再被空对象覆盖

  项目、会话归属和 Electron 状态文件损坏时会 fail closed，并保留原文件等待修复。

- Codex/Claude 自动重启更安全

  进程查询失败不再当作“没有实例”；user-data 参数、bundle 和进程身份会严格校验。Claude 迁移和 provider 切换也改为自动退出、准备、重启。

- 模型目录按当前 provider 重新生成

  不再把旧 provider 的 instructions、messages、context 或 tool 元数据复制到 GLM/Ecarx/OpenAI。

- 备份、Harness 和迁移冲突加固

  Codex 备份会递归脱敏嵌套密钥；Harness 固定到已审核版本并校验安装摘要；Claude 同名会话冲突会进入报告而不再静默跳过。

系统要求：macOS 13 或更高版本。
