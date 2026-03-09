# Tmux Configuration Guide

## Overview

Custom tmux setup with **SteamOS theme** styling, **TPM** (Tmux Plugin Manager), and **Gitmux** integration for git status display in the status bar.

## Plugins

Managed via TPM (`~/.tmux/plugins/tpm`):

- **tmux-sensible** - Sensible defaults
- **tmux-resurrect** - Session persistence across restarts
- **tmux-prefix-highlight** - Highlights when prefix is active
- **tmux-mem-cpu-load** - System resource monitor
- **tmux-acpi** - Battery/power status
- **tmux-notify** - Notifications for long-running commands
- **tmux-autoreload** - Auto-reload config on changes

## Basic Keys

| Key | Action |
|-----|--------|
| `Ctrl-b` + `\|` | Split pane vertically |
| `Ctrl-b` + `-` | Split pane horizontally |
| `Alt` + Arrow | Navigate between panes |
| `Ctrl-b` + `c` | Create new window |
| `Ctrl-b` + `x` | Close pane/window |
| `Ctrl-b` + `r` | Reload config |

## Status Bar - SteamOS Theme

The status bar displays:

- **Left:** Session name (cyan highlight) + mem-cpu-load
- **Center:** Window list (centered)
- **Right:** Git status (via gitmux) + Power/Battery (via acpi) + current time

### Color Scheme

- **Background:** `#0E1419` (SteamOS dark)
- **Highlight:** `#00BFFF` (Cyan)
- **Pane borders:** Dark background with cyan active border

## Installation

### Gitmux Setup

Gitmux is optional but recommended for git status display. Install it:

```bash
~/.dotfiles/linux/tmux/.tmux/bin/gitmux.sh
```

Or manually:

```bash
brew install gitmux      # macOS
apt install gitmux       # Debian/Ubuntu
dnf install gitmux       # RHEL/Fedora
pacman -S gitmux        # Arch Linux
pkg install gitmux      # Termux
```

If gitmux is not installed, the status bar will fall back to showing just the time.

### Tmux Config

The main config file is at `~/.tmux.conf`. After changes:

```bash
# Reload configuration
Ctrl-b + r

# Or reload from terminal
tmux source ~/.tmux.conf
```

## Troubleshooting

**Gitmux not showing in status bar:**

- Ensure gitmux is installed: `command -v gitmux`
- Check the config file exists: `~/.gitmux.conf`
- The status bar will fall back to time-only if gitmux is missing (no errors)

**Color issues:**

- Ensure terminal supports 256 colors: `echo $TERM`
- Set in shell if needed: `export TERM=screen-256color`

**Reset configuration:**

```bash
# Remove tmux session
tmux kill-server

# Remove config and restore
rm ~/.tmux.conf
# Re-stow or copy from dotfiles
```

## Auto-Start Behavior

Tmux auto-start is controlled by `TMUX_DISABLE_AT_BOOT`:

- Set to `0` (enabled) only if both `tmux` and `brew` are installed
- Set to `1` (disabled) otherwise

Configured in `~/.profile` and `~/.bashrc.d/00-env`.
