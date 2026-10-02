# Documentation index

| File | Purpose |
|---|---|
| [Root README](../README.md) | Application scope, configuration, safety, and limits |
| [Project manifest](../pyproject.toml) | Python version, dependencies, and tool settings |
| [Example environment](../.env.example) | Configuration variable names; replace example values locally |
| [Application entry point](../src/main.py) | CLI commands for system check and UI startup |
| [Configuration](../src/config.py) | Provider and device configuration behavior |
| [System checks](../src/utils/system_check.py) | Host requirements checked by the application |
| [macOS safety helper](../src/tools/mac_safety.py) | Current coordinate and input checks; not a complete safety boundary |
| [iOS tool](../src/tools/ios_tool.py) | Appium-driven device actions and current implementation |
| [Tests](../tests/test_core.py) | Existing core tests; not run for this documentation update |

The project does not contain a root `requirements.txt` or a declared console-script entry point. Verify package installation and launch behavior against the current source before publishing setup commands.
