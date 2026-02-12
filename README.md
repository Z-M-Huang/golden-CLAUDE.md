# Golden CLAUDE.md

English | [中文](README-zh.md)

A copy-paste-ready behavioral template for [Claude Code](https://docs.anthropic.com/en/docs/claude-code). Research-backed. Oath-style. Under 60 lines.

Distilled from 30+ of the most successful CLAUDE.md files, blog posts, and Anthropic's own documentation into one firm, general-purpose set of behavioral rules.

## Quick Start

**Solo developer** — apply globally to all projects:

```bash
curl -o ~/.claude/CLAUDE.md https://raw.githubusercontent.com/Z-M-Huang/golden-CLAUDE.md/main/CLAUDE.md
```

**Team project** — add to your repository root:

```bash
curl -o CLAUDE.md https://raw.githubusercontent.com/Z-M-Huang/golden-CLAUDE.md/main/CLAUDE.md
```

**Existing CLAUDE.md** — paste the golden rules at the **top** of your file, above your project-specific rules. Behavioral rules go first for maximum attention budget.

> If your combined CLAUDE.md exceeds ~120 lines, move project-specific rules to `.claude/rules/*.md` files. See the [wiki](../../wiki/FAQ) for details.

## What's Inside

| Section | Purpose |
|---------|---------|
| **The Oath** | 6 core commitments — certainty, honesty, verification, diligence, understanding, safety |
| **Before Every Action** | Pre-action checklist — read first, check existing patterns, never assume |
| **Honesty & Communication** | Anti-sycophancy, surface confusion, push back on bad ideas |
| **Verification & Quality** | Smallest change, one at a time, Chesterton's fence, prefer editing over creating |
| **Safety & Boundaries** | Consolidated destructive-action guard, secrets protection, permission-scope clarification |
| **Discipline** | No shortcuts, no over-engineering, crashes are data, root-cause investigation |

## What's NOT Inside

This template is **behavioral only**. It does not include:

- Code style or formatting rules — use linters (`eslint`, `prettier`, `ruff`)
- Language or framework-specific rules — add those as project-specific rules
- Personality instructions ("act as a senior engineer") — wastes attention budget
- Task-specific workflows — use [Claude Code skills](https://docs.anthropic.com/en/docs/claude-code/skills) instead

## Limitations

CLAUDE.md rules are **defense-in-depth, not a security guarantee**. Be aware:

- Rules may degrade over long conversations — keep sessions focused
- Claude may acknowledge a rule and still violate it ([known issue](https://github.com/anthropics/claude-code/issues/2544))
- Pair with external enforcement: git hooks, [Claude Code permission modes](https://docs.anthropic.com/en/docs/claude-code/security), filesystem permissions

These rules measurably improve compliance. They do not eliminate risk.

## Learn More

Visit the [wiki](https://github.com/Z-M-Huang/golden-CLAUDE.md/wiki) for deep dives:

- [Why These Rules](https://github.com/Z-M-Huang/golden-CLAUDE.md/wiki/Why-These-Rules) — philosophy and research backing
- [Rule-by-Rule Explanation](https://github.com/Z-M-Huang/golden-CLAUDE.md/wiki/Rule-by-Rule-Explanation) — rationale for every line
- [FAQ](https://github.com/Z-M-Huang/golden-CLAUDE.md/wiki/FAQ) — common questions including AGENTS.md compatibility
- [Anti-Patterns](https://github.com/Z-M-Huang/golden-CLAUDE.md/wiki/Anti-Patterns) — what NOT to put in CLAUDE.md

## Contributing

Open an issue or PR. Every proposed rule change must justify its attention budget cost — one line added means one line of compliance pressure on every other rule.

## License

[MIT](LICENSE)
