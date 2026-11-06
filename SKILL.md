---
name: slide-wright
description: 把主题、草稿笔记或大纲做成董事会级网页演示文稿（单文件 HTML），并支持事后增删改页。先发明主题并做两页预览，用户确认方向后再建全本；编辑已有 deck 则跳过提案门。当用户要做 slides / presentation / pitch deck / talk deck，或改已有幻灯片时使用。Use when the user wants slides, a presentation, a pitch/talk deck, or to add/remove/revise slides in an existing deck — propose look first, then build; fill missing inputs without a long questionnaire.
license: MIT
---

# slide-wright · 网页演示文稿 Skill

把主题或粗糙笔记变成董事会级演示：一张自包含 HTML，任意浏览器可播。
Turn a topic or rough notes into a boardroom-grade deck: one self-contained HTML file that runs in any browser.

改编自 [arifszn/slide-wright](https://github.com/arifszn/slide-wright)（MIT）。完整 reveal.js 模板、校验脚本、PPTX/PDF/部署流程见上游；本文件是填参可执行版。

## 输入 · Inputs

```
【主题/标题】：
【用途】：融资路演 / 内部分享 / 课程 / 产品发布 / 策略汇报（可推断）
【受众】：
【素材】：大纲 / 要点 / 数据 / 草稿笔记（可粘贴原文）
【页数意向】：短（约 6–10）/ 中（约 10–16）/ 长（按素材，默认按素材推断）
【语言】：中文 / 英文 / 双语（默认跟素材）
【视觉方向】：不指定则由你发明一个主题名（无预设库）
【是否需要动画】：否（默认）
【是否需要代码页】：按素材推断
【已有 deck 路径】：（编辑模式时填写；有则跳过提案门）
【导出意向】：仅 HTML（默认）/ PDF 说明 / PPTX 说明
```

**缺失字段不要追问**：只给一句话主题也能开工——自行推断用途、受众、长度与视觉语言。仅当「一个词且完全无角度」时，最多问 **一个** 澄清问题。
If fields are missing, infer them. Ask at most one clarifying question only when the request is too thin to design.

## 使用方法 · How to use

### 新 deck（默认）
1. 读输入，推断用途/受众/长度/展陈家族。
2. **先提案视觉**：发明一个主题（色板、字体、版式、展陈风格），生成 **真实标题页 + 一页真内容** 的两页预览，然后停下等确认。
3. 用户确认后再在同一文件上扩展成全本；已批准的两页不要推倒重来。
4. 交接：路径、主题名、页数、快捷键（方向键/空格/F/Esc·O/S），并说明 `?print-pdf`。

### 编辑已有 deck
若用户指向已有 HTML 且含 reveal.js CDN 标签：保留主题，原地修改；改完按能力运行上游 `check-deck.mjs`。非 reveal.js 引擎不要强行改写——说明超出本 Skill 编辑路径。

## 核心规则 · Core rules

### 定义本 Skill 的规则
**先提案外观，再建全本。** 第一轮绝不交付完整 presentation。一次只提一个方向；用户说不，就换一个明显不同的方向。每个主题为当前 deck 现发明，无预设主题库。

### 内容结构
- 每页自包含：不听演讲只看 PDF 也能懂要点。
- 一页一主张；装不下就拆页；禁止滚动/溢出/重叠/字号过小。
- 叙事：标题 → 主结论/建议 → 支撑页 → 行动呼吁/下一步。
- 内容页要有行动标题 + 一个展陈（流程/对比/时间线/指标板/示意图/图表等）；章节页与结尾页可无展陈。
- Speaker notes 放在合适处。

### 视觉
- 色板、字体（Fontshare / Google Fonts）、版式、展陈风格必须成套一致。
- 预览文件名用 deck slug（如 `./clickhouse.html`），不要出现 demo/preview/option A。
- 主题名称只出现在对用户的说明里，不印在幻灯片上。

### 引擎（对用户保持内部）
实现可用 CDN 加载的 reveal.js；对用户只谈 slides / theme / design。无 Node/Chrome 时：仍交付主题变量 + 完整大纲 + HTML 骨架说明，并注明视觉校验脚本未运行。

### 执行 · Execution
新 deck 在获得「Looks great — build it」类确认前，不建全本。编辑模式跳过提案门。

## 可直接粘贴的开工模板 · Ready-to-paste template

```
请按 slide-wright Skill 做演示文稿。

【主题/标题】：{{TITLE}}
【用途】：{{PURPOSE}}
【受众】：{{AUDIENCE}}
【素材】：
{{NOTES_OR_OUTLINE}}

【页数意向】：{{LENGTH}}
【语言】：{{LANGUAGE}}
【视觉方向】：{{VISUAL_DIRECTION}}
【是否需要动画】：{{MOTION}}
【是否需要代码页】：{{CODE_SLIDES}}
【已有 deck 路径】：{{EXISTING_DECK}}
【导出意向】：{{EXPORT}}

流程要求：
1) 若无已有 deck：先发明一个主题名，输出两页预览（真标题页 + 一页真内容），然后只问方向是否 OK。
2) 我确认后再扩展为完整单文件 HTML。
3) 若有已有 reveal.js deck：保留主题，按素材原地增删改。
4) 缺字段请自行补全，不要发长问卷。
```

## 确认门文案 · Approval gate (copy)

> Here's the design direction — **{{THEME_NAME}}**. Does this look right, or want a different direction?
>
> - **Looks great — build it**
> - **Try a different direction**
> - **Adjust this one**（换强调色 / 字体 / 更轻 / 更重）

若选不同方向：先给 1 个转向问题，选项以 **Surprise me** 开头，其余按主题现编；再换一套明显不同的主题与预览。

## 交接清单 · Hand-off checklist

- [ ] 文件路径与主题名
- [ ] 页数
- [ ] 快捷键：箭头/空格/滑动；F 全屏；Esc/O 总览；S 演讲者视图
- [ ] PDF：URL 加 `?print-pdf` 再打印
- [ ] 下一步可提供：改内容 / 换主题 / PDF / PPTX（需上游脚本）/ 部署

## 致谢 · Attribution

Upstream skill by Ariful Alam ([arifszn/slide-wright](https://github.com/arifszn/slide-wright)) — MIT.
Adaptation & fillable-parameter template by EricChan — MIT.
详见 [SOURCES.md](SOURCES.md) 与 [LICENSE](LICENSE)。
