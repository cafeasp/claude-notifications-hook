# Claude Code Notifications Hook (macOS)

Tiny shell scripts that send native macOS notifications when Claude Code needs your attention. Zero dependencies — uses built-in `osascript`.

Inspired by [TheNoeTrevino/claude-hooks](https://github.com/TheNoeTrevino/claude-hooks) (Linux version using `notify-send`).

## What it does

- **Stop** — Notifies you when Claude finishes and is waiting for input
- **PermissionRequest** — Notifies you when Claude needs permission to proceed

Both notifications include a sound so you can hear them even when the terminal isn't visible.

## Installation

```bash
git clone https://github.com/cafeasp/claude-notifications-hook.git ~/.claude/hooks
chmod +x ~/.claude/hooks/*.sh
```

Add this to your `~/.claude/settings.json`:

```json
{
  "hooks": {
    "Stop": [
      {
        "hooks": [
          {
            "type": "command",
            "command": "~/.claude/hooks/notify-ready.sh"
          }
        ]
      }
    ],
    "PermissionRequest": [
      {
        "matcher": "*",
        "hooks": [
          {
            "type": "command",
            "command": "~/.claude/hooks/needs-permissions.sh"
          }
        ]
      }
    ]
  }
}
```

## Requirements

- macOS (uses `osascript` for native Notification Center)
- [Claude Code](https://claude.com/claude-code)
