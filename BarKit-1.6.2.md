## BarKit 1.6.2 (23)

- 切换 Codex 模型配置时自动退出并重新打开 Codex

  选择 OpenAI、DeepSeek、GLM 或 Ecarx 后，BarKit 会先写完配置，再退出当前共享 Codex 实例，等待进程完全结束后自动重新打开。切换完成后不再需要手动退出或再次选择配置。

- 首次会话迁移也会自动处理应用退出

  如果首次导入旧会话或恢复项目归属时 Codex 正在运行，BarKit 会先正常退出 Codex，完成迁移后再按选中的模型配置重新打开。

- 恢复失败时不会把 Codex 留在关闭状态

  如果为迁移退出 Codex 后，导入或配置步骤失败，BarKit 会尝试重新打开原来的 Codex 实例，并在界面中报告失败原因。

- 切回官方登录时仍保留第三方 provider 定义

  DeepSeek、GLM、Ecarx 的历史会话在官方登录模式下也能正常恢复，不会再次出现 provider 缺失和闪烁。

系统要求：macOS 13 或更高版本。
