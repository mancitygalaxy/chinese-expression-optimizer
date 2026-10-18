# 中文表达优化规则

一套给 AI 使用的中文表达审校与润色规则。保留原意、信息和作者语气，让文字读起来更顺，减少翻译腔、套话和空泛黑话。

默认在表达层面润色，允许调整用词、语序、句式和段落衔接；已经合适的句段可以保留。改得更短不是默认目标，摘要、扩写或改变文体按用户要求处理。

## 适合场景

- 正式业务或技术文档需要中文表达审校。
- 需要批量统一术语、文风或表达口径。
- 用户明确要求润色、改写、去套话、减少翻译腔或去 AI 味；个人文章在这类明确要求下也适用。
- 用户直接指定使用本技能。

普通交流、个人思考、新稿创作、保存原回答、改标题和常规排版，按各自用途做必要检查。Markdown 格式、内容重要或需要保存到本地，本身不触发完整审校流程。

## 仓库内容

```text
skill/chinese-expression-optimizer/
  SKILL.md
  agents/openai.yaml
  references/rewrite-patterns.md
  references/ai-humanizer-patterns-zh.md
  references/style-calibration.md
  references/portable-rule.md

rules/
  中文表达优化规则.md

examples/
  业务文档改写示例.md
  技术文档改写示例.md
  Markdown审校示例.md
```

- [完整技能包](skill/chinese-expression-optimizer/SKILL.md)：可放入 Codex 技能目录，按当前任务读取相关参考文件。
- [可复制规则](rules/中文表达优化规则.md)：适合贴到其他 AI 助手里，与技能包中的轻量规则保持一致。
- [业务文档示例](examples/业务文档改写示例.md)、[技术文档示例](examples/技术文档改写示例.md)和 [Markdown 审校示例](examples/Markdown审校示例.md)：展示改顺句子、保留信息和按文体取舍的方法。

## 英文保留范围

项目中优先使用中文，但不机械翻译。以下内容保留英文，是因为它们属于平台、工具、开源仓库习惯或代码约定：

- GitHub 固定文件名：`README.md`、`LICENSE`、`.gitignore`。
- 常见仓库结构名：`skill/`、`rules/`、`examples/`。
- Codex 技能固定文件：`SKILL.md`、`agents/openai.yaml`、`references/`。
- 技能标识：`chinese-expression-optimizer`，用于安装和触发技能。
- 命令、路径、字段名、代码符号和产品名，例如 `Codex`、`Markdown`、`field_name`。

## 快速使用

如果你只是想把规则贴到自己的 AI 助手里，复制[可复制规则](rules/中文表达优化规则.md)中的正文即可。

如果你使用 Codex，先下载或克隆这个仓库，再将 `skill/chinese-expression-optimizer` 整个目录复制到技能目录。已经安装时，先备份原技能目录，再采用新版。以下命令从仓库根目录执行。

Windows（PowerShell）：

```powershell
$codexSkillRoot = if ($env:CODEX_HOME) { Join-Path $env:CODEX_HOME 'skills' } else { Join-Path $env:USERPROFILE '.codex\skills' }
New-Item -ItemType Directory -Path $codexSkillRoot -Force | Out-Null
Copy-Item -LiteralPath '.\skill\chinese-expression-optimizer' -Destination $codexSkillRoot -Recurse -Force
```

macOS / Linux：

```bash
mkdir -p "${CODEX_HOME:-$HOME/.codex}/skills"
cp -R skill/chinese-expression-optimizer "${CODEX_HOME:-$HOME/.codex}/skills/"
```

之后可以这样请求：

```text
使用 $chinese-expression-optimizer 润色这份工作说明，保留原意、完整信息与作者语气，允许调整句式，让表达更顺。

使用 $chinese-expression-optimizer 只审校这篇个人文章，指出不顺的地方并给建议，保留叙述顺序和情绪。
```

## 核心规则

- 保留独立信息、推理、例子、判断、情绪和有意义的修辞，可以合并重复表达。
- 保留事实、数字、名称、来源、归因、否定、条件、范围、时间和完成状态。“可能”不改成“确定”，“计划”不改成“已完成”。
- 具体内容只来自原文或用户材料。原文缺少细节时，保持概括表达；可疑事实另行提示。
- 普通概念优先用中文，必要术语和准确标识保留原文。命令、路径、字段名和代码符号用反引号标出，按读者背景补充解释。
- 正式工作文档讲清对象、动作、条件和结果；个人文章保留合适的叙述顺序与节奏。
- 去套话时可删无依据的宣传夸饰，保留原有目标和实际主张；已有幅度、限定和作者真实立场照原文保留。
- 连接词、否定句、长短句、排比和礼貌话按语境取舍，不作为禁用表处理。
- 有认可样稿时参考其表达习惯，目标文本的事实、经历和观点仍以原文为准；没有样稿时以原稿语气为准。

## 使用边界

- 表达审校和事实核验分别处理。润色完成，不代表原文中的数据或主张已经得到验证。
- 修改文件时保护代码、命令、路径、字段名、链接目标、引文和结构化数据；标题涉及锚点或外部引用时，保持引用有效。
- 保存用户认可的原回答时，以原文为准；提炼、压缩、重排或改变文体须有明确任务依据。
- 用户只要审校时，给问题和建议；已经授权改稿时，在范围内直接修改。

## 效果检查

改后先对照原文检查信息、推理、例子和限定是否完整，再通读改动段落，判断句间关系是否清楚、语气是否合适。字数减少、模型自评分和 AI 检测分数，均不足以单独证明润色效果。

交付形式按当前请求决定，不固定附加改写报告或自检声明；只说明影响使用的资料缺口、取舍和未完成检查，重要文档按需说明实际复查范围。

## 许可证

MIT 许可证

