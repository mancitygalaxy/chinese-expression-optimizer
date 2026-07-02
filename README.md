# 中文表达优化规则

一套给 AI 使用的中文表达优化规则，目标是让中文输出更自然、更清楚，少一点翻译腔、客服腔、营销腔和空泛黑话。

它的重点是保留原意、事实、数字、术语、业务口径和风险边界，让文本更像真实中文使用者在对应场景里会写的话。

## 适合场景

- 优化中文文案、中文 Markdown、工作说明、方案、评审稿和汇报稿。
- 审校 AI 生成内容，减少“看起来正确但不像人写”的表达。
- 统一团队文档里的术语、字段名、命令、路径和代码符号写法。
- 让面向业务、产品、测试、教研、研发或管理层的材料更贴近对应读者。

## 仓库内容

```text
skill/chinese-expression-optimizer/
  SKILL.md
  agents/openai.yaml
  references/rewrite-patterns.md
  references/portable-rule.md

rules/
  中文表达优化规则.md

examples/
  业务文档改写示例.md
  技术文档改写示例.md
  Markdown审校示例.md
```

- `skill/chinese-expression-optimizer/`：可放入 Codex 技能目录的完整技能包。
- `rules/中文表达优化规则.md`：可直接复制到其他 AI 助手里的轻量规则。
- `examples/`：常见中文表达问题的改写示例。

## 英文保留范围

项目中优先使用中文，但不机械翻译。以下内容保留英文，是因为它们属于平台、工具、开源仓库习惯或代码约定：

- GitHub 固定文件名：`README.md`、`LICENSE`、`.gitignore`。
- 常见仓库结构名：`skill/`、`rules/`、`examples/`。
- Codex 技能固定文件：`SKILL.md`、`agents/openai.yaml`、`references/`。
- 技能标识：`chinese-expression-optimizer`，用于安装和触发技能。
- 命令、路径、字段名、代码符号和产品名，例如 `Codex`、`Markdown`、`field_name`。

## 快速使用

如果你只是想把规则贴到自己的 AI 助手里，复制 `rules/中文表达优化规则.md` 里的规则即可。

如果你使用 Codex 并想作为技能使用，可以把 `skill/chinese-expression-optimizer` 复制到本机技能目录：

```bash
mkdir -p "${CODEX_HOME:-$HOME/.codex}/skills"
cp -R skill/chinese-expression-optimizer "${CODEX_HOME:-$HOME/.codex}/skills/"
```

之后可以这样请求：

```text
使用 $chinese-expression-optimizer 优化这份中文 Markdown，保留事实、术语和业务口径。
```

## 核心规则

- 普通概念优先用自然中文，例如“规则”“流程”“输入”“输出”“示例”“当前情况”“建议”。
- 专有名词、产品名、协议名、命令、路径、文件名、字段名、函数名和代码符号保留原文，并用反引号标出。
- 字段名要配中文说明，优先写成“中文说明 + `field_name`”，例如“检查项 `checks`”“预期结果 `expected`”。
- 把生硬英文句式改成自然中文，例如把“基于……进行……”“通过……来……”“被用于……处理……”改成更直接的动作句。
- 减少客服腔、营销腔、公文腔和空泛黑话，把抽象词改成能看见动作和结果的说法。
- 面向业务、产品、测试、教研读者时，先讲动作和结果，再补必要术语。
- 面向研发读者时，保留必要工程术语和准确标识，并补一句中文解释，让术语服务理解。
- 改写时保持事实、数字、路径、业务口径、项目结论和风险边界一致；拿不准就标为“待确认”。

## 使用边界

- 事实核查仍由使用者完成；规则会提示可疑内容需要确认，并把拿不准的信息标为“待确认”。
- 目标是优化中文表达；英文术语、代码标识、字段名和路径等精确信息应保留原文。
- 约束、风险和工作痕迹需要继续留在文档里；表达优化应提升可读性，同时保持材料可执行。

## 许可证

MIT 许可证
