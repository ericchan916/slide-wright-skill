# 来源与许可 · Sources

来源日期：2026-11-06（Asia/Shanghai）。

- 上游仓库：[arifszn/slide-wright](https://github.com/arifszn/slide-wright)（~67★）
- 上游入口：[SKILL.md](https://github.com/arifszn/slide-wright/blob/main/SKILL.md)
- 上游提交：`a751585b43353b6b9320a97106b59b9dea7ce817`
- 许可：MIT，Copyright (c) 2026 Ariful Alam；完整文本见 [LICENSE](LICENSE)
- 本仓库改编层：Copyright (c) 2026 EricChan（MIT），保留上游版权声明

## 本改编做了什么（相对上游）

1. 改成 Eric 常用的 **【输入】参数字段** + `{{placeholders}}` 大纲/主题模板；缺字段合理补全。
2. 保留上游核心规则：**先提案视觉（主题 + 两页预览）再整本构建**；编辑已有 deck 时跳过提案门。
3. 增加中英双语说明与「无 Node/Chrome 环境时的降级输出」（直接交付大纲 + 主题变量 + 可粘贴 HTML 骨架说明）。
4. 未整仓搬运上游 `slide-wright/scripts/`、`tests/`、reveal.js 工具链；需要校验脚本/PPTX 导出时请安装上游完整包。

## 未改动的上游硬约束

- 新 deck：先主题提案与两页预览，用户确认后再建全本
- 一次只提一个方向，不要菜单式多主题
- 编辑已有 reveal.js deck 时保留主题、原地改
- 非 reveal.js 的 HTML deck 不强制改写引擎
