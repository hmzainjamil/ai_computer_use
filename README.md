# Mac and iOS Computer Use

A Python application that connects a Streamlit interface to Anthropic computer-use tools for interacting with macOS and iOS devices. It can send inputs to real applications and devices; those actions can change files, settings, messages, or other user data.

## Current scope

| Area | Evidence in this repository |
|---|---|
| Interface | Streamlit UI in `src/ui/streamlit_app.py` |
| Model API | Anthropic client and tool-use loop in `src/api/anthropic.py` |
| macOS controls | UI automation in `src/tools/mac_tool.py` |
| iOS controls | Appium-based actions in `src/tools/ios_tool.py` and device setup in `src/tools/ios_connection.py` |
| Shell, filesystem, network | System tool in `src/tools/system_tool.py` |
| Configuration | `src/config.py`, with example values in `.env.example` |
| Requirements | Python 3.12+ in `pyproject.toml` |
| Tests | `tests/test_core.py` |

This README does not claim that all actions are safe or that every device configuration works. In particular, the current macOS safety helper contains an empty sensitive-region list, and the iOS swipe branch is marked unimplemented. Review the relevant source before enabling actions.

## Configuration

Copy `.env.example` to a local `.env` and set values for your own environment. The current example names:

| Variable | Purpose |
|---|---|
| `ANTHROPIC_API_KEY` | Anthropic API credential |
| `API_PROVIDER` | Provider selector; source currently defines Anthropic, Bedrock, and Vertex |
| `SCREEN_WIDTH`, `SCREEN_HEIGHT` | Screen dimensions |
| `IOS_DEVICE_ID` | Optional iOS device identifier |

The configuration module creates a local `temp/` directory for screenshots and related artifacts. Keep credentials out of version control and handle screenshots as potentially sensitive data.

## Running

The project manifest requires Python 3.12 or newer. Inspect [pyproject.toml](pyproject.toml), [src/main.py](src/main.py), and [src/utils/system_check.py](src/utils/system_check.py) for dependency and system requirements before starting the UI. The CLI defines `check` and `ui` commands. macOS accessibility permissions are required for computer interaction; iOS operation also depends on a configured device, Appium, and Xcode as applicable.

No install or launch command is asserted here because the repository metadata does not define a console-script entry point or a requirements.txt file. Confirm the current package layout and dependencies before installing.

## Safety and privacy

- Run only on devices and accounts you own or are authorized to control.
- Use a dedicated test device or account where possible. Avoid interacting with financial, health, identity, or production systems.
- Keep a human in control. Review proposed actions and observe device state; do not treat a coordinate or text-pattern check as a complete safety policy.
- Shell, filesystem, and network tools can have effects beyond the visible UI. Inspect the tool implementation and restrict permissions before use.
- Do not enter passwords, authentication codes, private messages, or sensitive customer data into prompts.
- Screenshots and logs may contain personal information. Store them securely and remove them when no longer needed.
- Never commit API keys, device identifiers that expose private devices, or captured data.

## Documentation

See [docs/README.md](docs/README.md) for source map and verification boundaries.
