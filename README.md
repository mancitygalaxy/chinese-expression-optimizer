# Chinese Expression Optimizer

一套给 AI 使用的中文表达优化规则，目标是让中文输出更自然、更清楚，少一点翻译腔、客服腔、营销腔和空泛黑话。

它不追求把文本改成“标准范文”，而是尽量保留原意、事实、数字、术语、业务口径和风险边界，让读者先看懂意思，再看到必要的专业标识。

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
  portable-rule.md

examples/
  business-doc-before-after.md
  tech-doc-before-after.md
  markdown-review-example.md
```

- `skill/chinese-expression-optimizer/`：可放入 Codex skills 目录的完整技能包。
- `rules/portable-rule.md`：不安装 skill 时也可以复制使用的轻量规则。
- `examples/`：常见中文表达问题的改写示例。

## 快速使用

如果你只是想把规则贴到自己的 AI 助手里，复制 `rules/portable-rule.md` 里的规则即可。

如果你使用 Codex 并想作为 skill 使用，可以把 `skill/chinese-expression-optimizer` 复制到本机 skills 目录：

```bash
mkdir -p "${CODEX_HOME:-$HOME/.codex}/skills"
cp -R skill/chinese-expression-optimizer "${CODEX_HOME:-$HOME/.codex}/skills/"
```

之后可以这样请求：

```text
Use $chinese-expression-optimizer 优化这份中文 Markdown，保留事实、术语和业务口径。
```

## 核心规则

- 普通概念优先用自然中文，例如“规则”“流程”“输入”“输出”“示例”“当前情况”“建议”。
- 专有名词、产品名、协议名、命令、路径、文件名、字段名、函数名和代码符号保留原文，并用反引号标出。
- 字段名不要裸奔，优先写成“中文说明 + `field_name`”，例如“检查项 `checks`”“预期结果 `expected`”。
- 不照搬英文句式，少写“基于……进行……”“通过……来……”“被用于……处理……”这类翻译腔。
- 少用客服腔、营销腔、公文腔和空泛黑话，把抽象词改成能看见动作和结果的说法。
- 面向业务、产品、测试、教研读者时，先讲动作和结果，再补必要术语。
- 面向研发读者时，保留必要工程术语和准确标识，但补一句中文解释，避免孤立堆叠。
- 改写时不改变事实、数字、路径、业务口径、项目结论和风险边界；拿不准就标为“待确认”。

## 不适合做什么

- 不负责事实核查。它会提醒可疑内容需要确认，但不会替你补造事实。
- 不做机械翻译。目标是优化中文表达，不是把所有英文都翻成中文。
- 不把有约束、有风险、有工作痕迹的材料改成漂亮但失真的文章。

## 许可证

MIT License
