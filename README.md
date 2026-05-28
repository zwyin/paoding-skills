# paoding-skills

[![license](https://img.shields.io/badge/license-MIT-green)](LICENSE) [![platform](https://img.shields.io/badge/platform-Claude%20Code-purple)](https://claude.ai/code)

Claude Code skill 合集——化繁为简，庖丁解牛，化复杂为轻松。把复杂的耗时任务变成一条命令。

English | [中文](#)

> 庖丁（Paoding）：源自《庄子》「庖丁解牛」——以无厚入有间，恢恢乎其于游刃必有余地。每个 skill 都是对复杂问题的精准解构。

## Install Skills

### Option 1: Via Browse UI

Select **Browse and install plugins** → Select **paoding-skills** → Select **Install now**

### Option 2: Direct Install

```bash
# 1. Add marketplace
/plugin marketplace add zwyin/paoding-skills

# 2. Install the plugin
/plugin install paoding-skills@paoding-skills

# 3. Reload plugins
/reload-plugins
```

### Option 3: Ask the Agent

Simply tell the Agent:

```
Please install Skills from github.com/zwyin/paoding-skills
```

### Option 4: Quick Install (npx)

```bash
npx skills add zwyin/paoding-skills
```

### Option 5: ClawHub (coming soon)

> Not yet published to ClawHub registry. Track progress at [github.com/zwyin/paoding-skills](https://github.com/zwyin/paoding-skills).

```bash
clawhub install github-safe-publish
clawhub install project-walkthrough
```

### Option 6: Manual Install

```bash
git clone https://github.com/zwyin/paoding-skills.git
claude --plugin-dir ./paoding-skills
```

---

## Skills

### github-safe-publish

安全发布到 GitHub——两层脱敏扫描（135 条规则 + AI）、自动修复、备份回滚、端到端发布。

[![version](https://img.shields.io/badge/version-0.7.0-blue)](skills/paoding-github-safe-publish/skills/paoding-github-safe-publish/SKILL.md)

**扫描覆盖 6 大维度**：密钥凭证（100 rules）、数据库连接（5 rules）、个人隐私（8 rules）、内部基础设施（6 rules）、文件黑名单（12 rules）、Git 历史（4 rules）。

```bash
# 完整流程：脱敏扫描 → 修复 → 发布到 GitHub
/paoding-github-safe-publish

# 核心 + SEO 优化（描述、Topics、Badges）
/paoding-github-safe-publish --seo

# 核心 + CI 生成（自动检测项目类型，生成 .github/workflows/test.yml）
/paoding-github-safe-publish --ci

# 全部：核心 + SEO + CI
/paoding-github-safe-publish --seo --ci

# 只做脱敏扫描，输出报告，不修复不发布
/paoding-github-safe-publish --scan

# 模拟运行：扫描 + 修复建议，但不做任何实际修改
/paoding-github-safe-publish --dry-run
```

| 参数 | 说明 | 互斥规则 |
|------|------|----------|
| (无参数) | 核心流程：脱敏 + 发布 | — |
| `--seo` | 附加 SEO 优化（描述、Topics、Badges、README 优化） | 不可与 `--scan` / `--dry-run` 组合 |
| `--ci` | 附加 CI 生成（自动检测项目类型并生成 workflow） | 不可与 `--scan` / `--dry-run` 组合 |
| `--scan` | 只扫描输出报告，不修复不发布 | 不可与 `--seo` / `--ci` / `--dry-run` 组合 |
| `--dry-run` | 模拟运行：扫描 + 修复建议，但不执行 | 不可与 `--seo` / `--ci` / `--scan` 组合 |

---

### project-walkthrough

项目技术走读——多深度、多受众、多语言，输出 markdown + 交互式 HTML。

[![version](https://img.shields.io/badge/version-1.6.1-blue)](skills/paoding-project-walkthrough/skills/paoding-project-walkthrough/SKILL.md)

```bash
# 自动分析当前目录，推荐深度
/paoding-project-walkthrough

# 指定项目路径
/paoding-project-walkthrough /path/to/project

# 快速概览（适合小项目或初次了解）
/paoding-project-walkthrough --depth brief

# 深度走读（适合需要全面了解的项目）
/paoding-project-walkthrough --depth deep

# 全量走读（包含所有细节，适合大型项目）
/paoding-project-walkthrough --depth all

# 面向开发者受众
/paoding-project-walkthrough --audience dev

# 纯中文输出（无英文混排）
/paoding-project-walkthrough --lang zh-pure

# 双语输出（中英对照）
/paoding-project-walkthrough --lang bilingual

# 跳过确认，使用推荐默认值（适合自动化流程）
/paoding-project-walkthrough --no-confirm

# 组合使用：深度走读 + 开发者受众 + 中文输出
/paoding-project-walkthrough --depth deep --audience dev --lang zh

# 查看版本号
/paoding-project-walkthrough --version
```

| 参数 | 说明 | 可选值 | 默认 |
|------|------|--------|------|
| `path` | 项目路径 | 任意目录路径 | 当前目录 |
| `--depth` | 走读深度 | `brief` / `medium` / `deep` / `all` | 自动推荐 |
| `--audience` | 目标受众 | `general` / `dev` | `general` |
| `--lang` | 输出语言 | `zh` / `zh-pure` / `en` / `bilingual` | `zh` |
| `--no-confirm` | 跳过确认 | (flag, 无值) | — |
| `--version` | 打印版本号 | (flag, 无值) | — |

---

## License

[MIT](LICENSE)
