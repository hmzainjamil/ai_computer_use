# ai_computer_use

> **Claude drives your Mac and iPhone** - Streamlit app that hands Claude the keyboard and mouse - controls macOS apps, iOS Simulator, and real iPhones via accessibility APIs and screen capture.

<p align="center"><a href="https://github.com/hmzainjamil/ai_computer_use">Repository</a> · <a href="https://github.com/hmzainjamil/ai_computer_use/commits/main">Commits</a> · <a href="https://github.com/hmzainjamil/ai_computer_use/issues">Issues</a></p>
<p align="center"><img alt="Documentation" src="https://img.shields.io/badge/documentation-deep%20editorial-lightgrey"> <img alt="Lifecycle" src="https://img.shields.io/badge/lifecycle-active-success"></p>

<!-- HMZ DEEP README v1 -->

## At a glance

| Field | Current state |
|---|---|
| Repository | ai_computer_use |
| Visibility | Public |
| Lifecycle | Active |
| Evidence basis | Current repository documentation and source-visible material |

## Why this exists

**Claude drives your Mac and iPhone** - Streamlit app that hands Claude the keyboard and mouse - controls macOS apps, iOS Simulator, and real iPhones via accessibility APIs and screen capture.

The README documents computer-use capabilities and keeps automation authority, credentials, side effects, and external application behavior explicit.

## CONCEPTS

| Concept | Location | Description |
|---|---|---|
| **Streamlit UI** | `src/ui/streamlit_app.py` | Chat front-end at :8501 - [Source](https://github.com/hmzainjamil/ai_computer_use/blob/main/src/ui/streamlit_app.py) |
| **Anthropic client** | `src/api/anthropic.py` | Streaming + tool-use loop - [Source](https://github.com/hmzainjamil/ai_computer_use/blob/main/src/api/anthropic.py) |
| **Mac tool** | `src/tools/mac_tool.py` | Drives macOS via accessibility - [Source](https://github.com/hmzainjamil/ai_computer_use/blob/main/src/tools/mac_tool.py) |
| **iOS tool** | `src/tools/ios_tool.py` | Drives iPhone via USB/wifi - [Source](https://github.com/hmzainjamil/ai_computer_use/blob/main/src/tools/ios_tool.py) |
| **Mac safety guard** | `src/tools/mac_safety.py` | Hard-blocks destructive ops - [Source](https://github.com/hmzainjamil/ai_computer_use/blob/main/src/tools/mac_safety.py) |
| **Device manager** | `src/tools/device_manager.py` | Real + simulator iOS device routing - [Source](https://github.com/hmzainjamil/ai_computer_use/blob/main/src/tools/device_manager.py) |
| **System tool** | `src/tools/system_tool.py` | Shell, fs, network primitives - [Source](https://github.com/hmzainjamil/ai_computer_use/blob/main/src/tools/system_tool.py) |
| **Tool collection** | `src/tools/collection.py` | Tool registry exposed to Claude - [Source](https://github.com/hmzainjamil/ai_computer_use/blob/main/src/tools/collection.py) |
| **Entry** | `src/main.py` | App bootstrap - [Source](https://github.com/hmzainjamil/ai_computer_use/blob/main/src/main.py) |
| **Config** | `src/config.py` | Runtime config + flags - [Source](https://github.com/hmzainjamil/ai_computer_use/blob/main/src/config.py) |

## HOW IT WORKS

```
+---------------------------------------------------------+
|                       INPUT                             |
|   macOS 14+ . iOS 17+ (real device & simulator)     |
+--------------------------+------------------------------+
                           v
+---------------------------------------------------------+
|                  ORIENT / PARSE                         |
|   - Validate inputs                                     |
|   - Load skill / agent / tool definitions               |
|   - Resolve config + secrets from .env                  |
+--------------------------+------------------------------+
                           v
+---------------------------------------------------------+
|                  PLAN (Claude Sonnet)                   |
|   - Decompose goal into ordered subtasks                |
|   - Pick model per task (Sonnet / Haiku / Tier-0)       |
+--------------------------+------------------------------+
                           v
+---------------------------------------------------------+
|                  EXECUTE (parallel)                     |
|   - Spawn sub-agents / call tools                       |
|   - Stream tokens, persist artifacts                    |
+--------------------------+------------------------------+
                           v
+---------------------------------------------------------+
|                  VERIFY                                 |
|   - Lint / typecheck / visual diff / QA agent           |
|   - On failure -> re-prompt with error context          |
+--------------------------+------------------------------+
                           v
+---------------------------------------------------------+
|                  SHIP                                   |
|   - Write to disk . commit . PR . upload                |
+---------------------------------------------------------+
```

## Install

```bash
git clone https://github.com/hmzainjamil/ai_computer_use.git
cd ai_computer_use

# Per-repo install (try in order):
bash install.sh 2>/dev/null || \
npm install 2>/dev/null || \
bun install 2>/dev/null || \
pip install -r requirements.txt 2>/dev/null || true
```

Environment:

```bash
cp .env.example .env  # if present
# fill ANTHROPIC_API_KEY at minimum
```

## Usage

```bash
# Claude Code skill packs:
/skill-name "your goal"

# CLI / scripts:
python scripts/<script>.py --input ./input --output ./output

# TypeScript projects:
bun run dev    # or npm run dev
```

### Configuration knobs

| Key | Default | Description |
|---|---|---|
| `ANTHROPIC_API_KEY` | - (required) | Claude API key |
| `MODEL` | `claude-sonnet-4-7` | Default LLM |
| `MODEL_FALLBACK` | `claude-haiku-4` | Cheaper fallback |
| `MAX_TOKENS` | `8192` | Per-call ceiling |
| `TEMPERATURE` | `0.2` | Determinism dial |
| `LOG_LEVEL` | `info` | debug / info / warn / error |
| `OUT_DIR` | `./out` | Where artifacts land |
| `CACHE_DIR` | `.cache` | Prompt cache root |
| `PARALLELISM` | `4` | Sub-agent concurrency |
| `RETRY_MAX` | `3` | Per-call retry budget |
| `TIMEOUT_S` | `120` | Per-call timeout |
| `DRY_RUN` | `false` | Plan-only, no side effects |

### Case 3 - DTC brand, ad creative testing

- Before: $2K/month UGC creator retainer, 4 ads/month.
- After: 30+ ad variants/week via Arcads + Claude, A/B-tested.
- Result: 3x creative velocity, 41% lower CAC after 6 weeks.

## Security

- Never commit API keys. `.env` is in `.gitignore` by default.
- Use [git-secret](https://git-secret.io/) or 1Password CLI for team secret sharing.
- Review the QA / safety layer for any tool that writes to disk or runs shells (see `mac_safety.py` style guards).
- Vulnerability reports: open a private GitHub Security Advisory.

## Limitations

- UI behavior depends on external applications and display environments.
- Automated interaction can have real side effects and requires guardrails.
- Performance and success-rate claims require task-specific evaluation.

## Related

- [Claude Code](https://docs.claude.com/en/docs/claude-code) - official docs
- [Anthropic Console](https://console.anthropic.com) - API keys + billing
- [Crawlee](https://crawlee.dev) - web scraping framework
- [hmz-claude-code-best-practice](https://github.com/hmzainjamil/hmz-claude-code-best-practice) - sister repo

## Maintainer

[hmzainjamil](https://github.com/hmzainjamil)