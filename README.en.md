# Claude Code Vietnamese IME Fix

English | [Tiếng Việt](README.md)

Fix Vietnamese typing issues in Claude Code CLI when using IME tools such as OpenKey, EVKey, PHTV, Unikey, etc. Supports macOS, Linux, and Windows (npm).

## The Problem

Vietnamese IME tools use a "backspace then replace" technique to compose characters (e.g., `a` → `á`). Claude Code CLI processes the backspace (`\x7F`) but fails to insert the replacement character, resulting in:

- Characters being "swallowed" or lost while typing
- Displayed text not matching what was typed
- Having to copy-paste instead of typing directly

> **Note:** This patcher only works with the **npm** version of Claude Code (`npm install -g @anthropic-ai/claude-code`). The standalone binary (installed via the official `curl` installer) is not supported as it is compiled into a native binary with no JS files to patch.

## Installation

The first run will **automatically apply the fix**.

**macOS / Linux:**

```bash
curl -fsSL https://raw.githubusercontent.com/BALUTCorp/claude-code-vietnamese-fix/main/install.sh | bash
```

**Windows (PowerShell):**

```powershell
irm https://raw.githubusercontent.com/BALUTCorp/claude-code-vietnamese-fix/main/install.ps1 | iex
```

## After Updating Claude Code

Re-apply the fix:

```bash
python3 ~/.claude-vn-fix/patcher.py
```

**Windows:**

```powershell
python ~\.claude-vn-fix\patcher.py
```

## Commands

```bash
python3 patcher.py              # Auto-detect and fix
python3 patcher.py --restore    # Restore from backup
python3 patcher.py --path FILE  # Fix a specific file
python3 patcher.py --help       # Show help
```

## Update Patcher

```bash
cd ~/.claude-vn-fix && git pull
```

## Credits

Based on and improved from [manhit96/claude-code-vietnamese-fix](https://github.com/manhit96/claude-code-vietnamese-fix) and [PHTV](https://github.com/phamhungtien/PHTV).
