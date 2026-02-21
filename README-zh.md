# Golden CLAUDE.md

[English](README.md) | 中文

一份开箱即用的 [Claude Code](https://docs.anthropic.com/en/docs/claude-code) 行为规则模板。基于大量研究，承诺式写法，不到80行。

从30多份高质量的 CLAUDE.md 文件、博客文章和 Anthropic 官方文档中，提炼出一套通用的行为规则。

## 快速开始

**个人开发者** — 全局生效：

```bash
curl -o ~/.claude/CLAUDE.md https://raw.githubusercontent.com/Z-M-Huang/golden-CLAUDE.md/main/CLAUDE.md
```

**团队项目** — 添加到仓库根目录：

```bash
curl -o CLAUDE.md https://raw.githubusercontent.com/Z-M-Huang/golden-CLAUDE.md/main/CLAUDE.md
```

**已有 CLAUDE.md** — 把 Golden 规则粘贴到你文件的**最顶部**，放在项目专属规则之上。行为规则放在前面，注意力预算的利用率最高。

> 如果合并后的 CLAUDE.md 超过约120行，建议把项目专属规则移到 `.claude/rules/*.md` 文件中。详见 [常见问题](https://github.com/Z-M-Huang/golden-CLAUDE.md/wiki/FAQ-zh)。

## 模板内容

| 章节 | 用途 |
|------|------|
| **核心承诺** | 6条核心承诺 — 确定性、诚实、验证、勤勉、理解、安全 |
| **动手之前** | 行动前检查清单 — 先读代码、检查已有模式、不要假设 |
| **沟通诚实** | 反讨好、暴露困惑、对不好的想法提出反对意见 |
| **验证质量** | 最小改动、逐个验证、切斯特顿之篱笆、优先编辑而非新建 |
| **安全底线** | 统一的破坏性操作防护、密钥保护、权限范围确认 |
| **自律守则** | 不走捷径、不过度设计、崩溃是数据、追根溯源 |
| **沟通与提案** | 用行动代替空谈——代码示例、前后对比、ASCII 图表、方案对比表 |

## 不包含的内容

这个模板**只管行为**，不包含：

- 代码风格或格式规则 — 用 linter（`eslint`、`prettier`、`ruff`）
- 语言或框架专属规则 — 作为项目专属规则单独添加
- 人设指令（"扮演资深工程师"）— 浪费注意力预算
- 任务流程 — 用 [Claude Code skills](https://docs.anthropic.com/en/docs/claude-code/skills) 代替

## 局限性

CLAUDE.md 规则是**纵深防御，不是安全保证**。需要注意：

- 长对话中规则可能会衰减 — 保持会话聚焦
- Claude 可能承认了规则但仍然违反（[已知问题](https://github.com/anthropics/claude-code/issues/2544)）
- 配合外部强制手段使用：git hooks、[Claude Code 权限模式](https://docs.anthropic.com/en/docs/claude-code/security)、文件系统权限

这些规则能明显提高遵循度，但不能消除风险。

## 了解更多

访问 [Wiki](https://github.com/Z-M-Huang/golden-CLAUDE.md/wiki/Home-zh) 深入了解：

- [为什么是这些规则](https://github.com/Z-M-Huang/golden-CLAUDE.md/wiki/Why-These-Rules-zh) — 设计思路和研究依据
- [逐条规则详解](https://github.com/Z-M-Huang/golden-CLAUDE.md/wiki/Rule-by-Rule-Explanation-zh) — 每条规则的来龙去脉
- [常见问题](https://github.com/Z-M-Huang/golden-CLAUDE.md/wiki/FAQ-zh) — 包括 AGENTS.md 兼容性等常见问题
- [反模式](https://github.com/Z-M-Huang/golden-CLAUDE.md/wiki/Anti-Patterns-zh) — 别往 CLAUDE.md 里放这些东西

## 贡献

欢迎提 Issue 或 PR。每条新增规则都必须论证其注意力预算成本 — 多加一行，就意味着其他每条规则的遵循压力都会增加。

## 许可证

[MIT](LICENSE)
