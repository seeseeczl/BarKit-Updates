## BarKit 1.6.0 (21)

- 固定主工作空间，删除“独享工作空间”开关

  菜单不再需要在“独享/共享工作空间”之间切换。Codex 和 Claude 分别固定使用一套 BarKit 主工作空间，OpenAI、DeepSeek、GLM、Ecarx 之间切换 provider 时只改变模型配置，不改变会话目录。

- 支持把旧工作空间会话导入主工作空间

  设置页新增“导入旧工作空间会话”。旧独享会话会以复制方式导入主工作空间，源目录不会被删除；Codex 会迁移 rollout、`state_5.sqlite` 和 `thread_history_1.sqlite` 会话元数据，Claude 会按账号目录合并。

- Codex 会话导入支持完整元数据和冲突保护

  导入会同时迁移 thread、附件、动态工具、项目、归档和置顶等记录；没有 rollout 的 thread 不会写入目标数据库。文件冲突使用 SHA-256 判断，默认只报告、不覆盖。

- Claude 每个 provider 使用独立 profile，并记住 model/thinking

  shared 主工作空间中切换 DeepSeek、GLM、Ecarx 时会分别保存和恢复各自的模型选择；非活动 profile 中的 API Key 会被脱敏。

- 新增工作空间一致性诊断

  设置页会列出 Codex 与 Claude 在目录归属、模型偏好、skills/plugins、CLI、历史迁移和新装环境方面的实际差异，不再用“工作空间”掩盖两边不同的实现。

系统要求：macOS 13 或更高版本。
