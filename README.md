# Golden CLAUDE.md

English | [中文](README-zh.md)

A copy-paste-ready behavioral template for [Claude Code](https://docs.anthropic.com/en/docs/claude-code). Research-backed. Operational.

Distilled from 30+ of the most successful CLAUDE.md files, blog posts, and Anthropic's own documentation into one firm, general-purpose set of behavioral rules.

## Quick Start

Choose one destination and run its command in your shell.

| Scope | Command |
|-------|---------|
| All your projects (recommended) | `rules_dir="$HOME/.claude/rules"` |
| One team repository, from its root | `rules_dir=".claude/rules"` |

Run the installer in the same shell on a filesystem that supports hard links. It downloads the complete template before creating `golden.md` and refuses to overwrite an existing file.

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

Claude Code loads `golden.md` alongside your project’s `CLAUDE.md`. For a team install, include `.claude/rules/golden.md` in version control. If an earlier version is already in a rules file or pasted into a `CLAUDE.md`, review and merge updates into that copy so Claude loads the rules once.

## What's Inside

| Section | Purpose |
|---------|---------|
| **Core Commitments** | Verify context and facts, state uncertainty, and confirm destructive actions |
| **Before Changing Code** | Read the relevant code, reuse existing functionality, and prefer maintained packages for gaps |
| **Honesty & Communication** | Anti-sycophancy, surface confusion, push back on bad ideas |
| **Verification & Quality** | Make the smallest effective change and report the check, its outcome, and remaining uncertainty |
| **Critical Evaluation** | Falsify before endorsing, visible Risk section, inverted non-trivial default, no generic warnings |
| **Safety & Boundaries** | Consolidated destructive-action guard, secrets protection, permission-scope clarification |
| **Discipline** | No shortcuts, no over-engineering, crashes are data, root-cause investigation |
| **Response Style** | Caveman Lite — drop filler/hedging, keep articles and full sentences, auto-expand for safety |
| **Communication & Proposals** | Show don't tell — code examples, before/after diffs, ASCII diagrams, comparison tables |

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
- The built-in Explore and Plan agents skip user and project instructions at startup. Pass relevant constraints in the task prompt when delegating. [Subagent context](https://code.claude.com/docs/en/sub-agents#what-loads-at-startup)
- Enforce mandatory tool restrictions with Claude Code permission rules or hooks. Git hooks and filesystem permissions can also protect repository and file operations. [Permission rules](https://code.claude.com/docs/en/permissions) · [Claude Code hooks](https://code.claude.com/docs/en/hooks)

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
