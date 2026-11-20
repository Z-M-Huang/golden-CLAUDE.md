# Golden CLAUDE.md

[English](README.md) | 中文

一份开箱即用的 [Claude Code](https://docs.anthropic.com/en/docs/claude-code) 行为规则模板。基于大量研究，操作化写法。

从30多份高质量的 CLAUDE.md 文件、博客文章和 Anthropic 官方文档中，提炼出一套通用的行为规则。

## 快速开始

选择一个安装位置，在终端中运行对应的命令。

| 适用范围 | 命令 |
|---------|------|
| 个人所有项目（推荐） | `rules_dir="$HOME/.claude/rules"` |
| 单个团队仓库，在仓库根目录运行 | `rules_dir=".claude/rules"` |

在同一终端中运行以下命令，目标文件系统需支持硬链接。模板下载完整后才会创建 `golden.md`，如果文件已存在，安装会报错退出。要安装中文版，请将下载地址末尾的 `CLAUDE.md` 改为 `CLAUDE.zh.md`。

```bash
(
  set -eu
  mkdir -p "$rules_dir"
  download_dir=$(mktemp -d "$rules_dir/.golden.XXXXXXXX")
  trap 'rm -f "$download_dir/golden.md"; rmdir "$download_dir"' EXIT
  curl -fsSL -o "$download_dir/golden.md" https://raw.githubusercontent.com/Z-M-Huang/golden-CLAUDE.md/main/CLAUDE.md
  ln "$download_dir/golden.md" "$rules_dir/"
)
```

Claude Code 会同时加载 `golden.md` 和项目的 `CLAUDE.md`。团队安装后，可将 `.claude/rules/golden.md` 纳入版本控制。如果之前已经安装过规则文件，或把规则粘贴进了 `CLAUDE.md`，请对照新版在原处合并更新，以免重复加载。

## 模板内容

| 章节 | 用途 |
|------|------|
| **核心承诺** | 核实上下文和事实，说明不确定之处，执行破坏性操作前取得确认 |
| **修改代码之前** | 先阅读相关代码，复用已有功能，有缺口时优先选用持续维护的软件包 |
| **沟通诚实** | 反讨好、暴露困惑、对不好的想法提出反对意见 |
| **验证质量** | 做出最小有效改动，报告检查方式、结果和仍未验证的部分 |
| **批判评估** | 先证伪再认可、可见的风险分析、默认非简单、禁止泛泛警告 |
| **安全底线** | 统一的破坏性操作防护、密钥保护、权限范围确认 |
| **自律守则** | 不走捷径、不过度设计、崩溃是数据、追根溯源 |
| **回复风格** | Caveman 精简模式 — 去掉废话/模糊表达，保留冠词和完整句子，安全场景自动展开 |
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
- 内置的 Explore 和 Plan 子代理启动时会跳过用户级和项目级指令。委派任务时，在任务说明中写明相关约束。[子代理的上下文](https://code.claude.com/docs/en/sub-agents#what-loads-at-startup)
- 需要强制执行的工具限制，可通过 Claude Code 权限规则或钩子实施。Git 钩子和文件系统权限也可用于保护仓库和文件操作。[权限规则](https://code.claude.com/docs/en/permissions) · [Claude Code 钩子](https://code.claude.com/docs/en/hooks)

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
