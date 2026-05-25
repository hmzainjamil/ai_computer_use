# ai_computer_use

> **AI computer use — Claude controls desktop apps via screenshot and action loops**

![Status](https://img.shields.io/badge/status-active-brightgreen?style=flat)
![License](https://img.shields.io/badge/license-MIT-blue?style=flat)
![Claude Code](https://img.shields.io/badge/Claude_Code-Skill-FF6B35?style=flat)
![Stars](https://img.shields.io/github/stars/hmzainjamil/ai_computer_use?style=flat)
![Last Commit](https://img.shields.io/github/last-commit/hmzainjamil/ai_computer_use?style=flat)

---

## CONCEPTS

| Concept | Description |
|---|---|
| **Computer Use** | Claude sees screen, clicks, types autonomously |
| **Screenshot** | Capture screen state for visual understanding |
| **Action Loop** | Observe → decide → act → verify cycle |
| **App Control** | Operate any desktop application |
| **Form Fill** | Auto-fill complex forms from data |
| **Navigation** | Browse and interact with any UI |
| **Error Recovery** | Detect failed actions and retry |
| **Audit Trail** | Log every action with screenshot proof |

---

## 🔥 Hot Commands

```bash
# Activate skill
claude --skill ai_computer_use 'your task'

# Quick workflow
claude 'computer automation task'

# Get capabilities
claude 'what can ai_computer_use do?'
```

## ■ tip
> Mention **computer** or **use** in your prompt to auto-activate this skill.

---

## ☠️ STARTUPS / BUSINESSES

- **Agencies**: automate computer workflows for clients at scale
- **Founders**: ship use features 10x faster
- **Freelancers**: deliver desktop work with AI precision

---

## Features

- Computer automation
- Use automation
- Desktop automation
- Automation automation
- Screenshot automation
- Action automation

---

## Installation

```bash
git clone https://github.com/hmzainjamil/ai_computer_use.git
cd ai_computer_use
```

---

## Usage

```bash
# Activate skill in Claude Code
claude --skill ai_computer_use "your task here"

# Quick workflow
claude "computer automation task"

# Get help
claude "what can ai_computer_use do?"
```

---

## Configuration

| Variable | Description | Default |
|---|---|---|
| `API_KEY` | Primary API key | Required |
| `MODEL` | AI model to use | claude-3-5-sonnet |
| `DEBUG` | Enable verbose debug | false |
| `MAX_TOKENS` | Max token budget | 8192 |
| `TIMEOUT` | Request timeout (sec) | 30 |
| `LOG_LEVEL` | Logging verbosity | info |

---

## Architecture

```
ai_computer_use/
├── README.md           # Documentation
├── SKILL.md            # Claude Code skill definition
├── scripts/            # Automation scripts
├── templates/          # Output templates
├── examples/           # Usage examples
└── docs/               # Extended documentation
```

---

## Examples

### Basic

```bash
# Simple task
claude --skill ai_computer_use "computer task"

# Verbose
claude --skill ai_computer_use --verbose "detailed use task"
```

### Advanced Pipeline

```bash
# Chain skills
claude --skill ai_computer_use "step 1" | claude --skill summarize

# Batch run
for item in $(cat list.txt); do
  claude --skill ai_computer_use "process $item"
done
```

---

## Troubleshooting

| Issue | Cause | Fix |
|---|---|---|
| Auth fails | Invalid API key | Re-export key in shell profile |
| Timeout | Network or large payload | Increase TIMEOUT value |
| Empty output | Prompt too vague | Add more context |
| Rate limit | Too many requests | Add delay between calls |
| Model error | Unsupported version | Update MODEL variable |
| Import error | Missing dependency | Run pip install -r requirements.txt |

---

## Comparison

| Feature | This Skill | Alt A | Alt B |
|---|---|---|---|
| Claude Code native | ✅ | ❌ | ✅ |
| Auto-activation | ✅ | ✅ | ❌ |
| Free to use | ✅ | ❌ | ✅ |
| Production ready | ✅ | ✅ | ❌ |
| Active maintenance | ✅ | ❌ | ❌ |

---

## Changelog

| Version | Changes |
|---|---|
| v2.0 | Claude 4 support, auto-activation |
| v1.5 | Added keyword triggers |
| v1.0 | Initial release |

---

## Contributing

1. Fork → feature branch → commit → PR
2. Follow conventional commits: `feat:`, `fix:`, `docs:`
3. Add tests for new features

---

## ⭐ Star History

[![Star History Chart](https://api.star-history.com/svg?repos=hmzainjamil/ai_computer_use&type=Date)](https://star-history.com/#hmzainjamil/ai_computer_use&Date)

---

## 📜 License

MIT — free to use, modify, distribute.

---

Made with ❤️ by [@hmzainjamil](https://github.com/hmzainjamil)
