## BarKit 1.8.1 (33)

- **内置 provider 声明的上下文窗口统一写成 1,000,000**

  模型目录里 DeepSeek、GLM、Ecarx 这些内置配置的 `context_window` / `max_context_window` 原来是 `1_048_576`（2^20）。"1M 上下文"在语义上就是一百万，DSH 的 provider 配置也写 `1000000`，同一个数在两处出现两种写法没有好处，这里跟着统一。

  这个值只影响 BarKit 自己写进 `models.json` 的内置 provider 条目；本地部署那条路径仍然用你在设置里填的 `--ctx-size`，两者互不影响。需要注意的是 **Codex 按 `context_window` 的 95% 计算提示预算**（`effective_context_window_percent = 95`），所以下次切换 provider 重写模型目录后，声明出来的可用提示空间从 1 048 576 变成 1 000 000——是声明值的统一，不是把某个模型的能力改小了。

- **内部整理**

  `PanelSection` 降为 `private`（它本来就只被 `MenuContentView` 内部使用），随之为它而存在的人工验收渲染工具 `PanelSectionRender` 一并移除——这个工具需要 `BARKIT_RENDER_PANEL=1` 才会运行、且从不断言，`PanelSection` 转为 private 之后它已经看不到目标类型。测试从 309 条（2 条跳过）变为 308 条（1 条跳过），减少的正是这条不参与回归的渲染用例。
