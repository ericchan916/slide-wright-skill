# slide-wright Skill / 网页演示文稿 Skill

把主题、草稿笔记或大纲做成董事会级单文件 HTML 演示文稿；支持事后增删改页。先提案视觉（主题 + 两页预览），确认后再建全本。

改编自 [arifszn/slide-wright](https://github.com/arifszn/slide-wright)（MIT），做成 Eric 风格的 **【输入】填参模板**。

## 它能做什么
- 从一句话主题或粗糙大纲推断用途、受众与长度
- 为当前 deck 现发明主题（色板 / 字体 / 版式 / 展陈），无预设库
- 两页真预览 → 确认门 → 同文件扩展全本
- 编辑已有 reveal.js deck：保留主题、原地改
- 中英双语；无 Node/Chrome 时降级交付大纲 + 主题变量 + HTML 骨架说明

## 安装

```bash
git clone https://github.com/ericchan916/slide-wright-skill.git
cp -r slide-wright-skill ~/.claude/skills/slide-wright
# 或 ~/.cursor/skills/、~/.codex/skills/ 等
```

需要上游校验脚本 / PPTX 导出时，另装完整上游包：

```bash
npx skills add arifszn/slide-wright
# 或 git clone https://github.com/arifszn/slide-wright.git
```

## 使用示例

```
【主题/标题】：Q4 产品策略复盘
【用途】：内部分享
【受众】：产品 + 设计 + 增长
【素材】：（粘贴大纲或要点）
【页数意向】：中
```

新 deck 会先给你一个主题名 + 两页预览，确认后再建全本。

## 相对上游的改进
1. 【输入】参数块 + `{{placeholders}}` 开工模板
2. 缺字段合理推断，避免长问卷
3. 明确无工具链环境的降级路径
4. 中英双语说明；完整 scripts/references 仍指向上游

完整来源与提交哈希见 [SOURCES.md](SOURCES.md)。

## License
MIT © 2026 EricChan  
Portions © 2026 Ariful Alam（上游 MIT）— 见 [LICENSE](LICENSE)。
