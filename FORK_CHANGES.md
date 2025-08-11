# Tmux MCP Fork - Raw Send Keys

This is a fork of [nickgnd/tmux-mcp](https://github.com/nickgnd/tmux-mcp) with added raw send-keys capability.

## Changes Made

### Added `send-keys-raw` Tool

This fork adds a new tool `send-keys-raw` that sends keystrokes directly to tmux panes without any safety markers. This is specifically designed for controlling text editors and other interactive applications where the safety markers would interfere.

**WARNING**: This tool bypasses all safety checks. Use only for trusted operations.

### Usage Example

```javascript
// Send text to a neovim instance
await sendKeysRaw(paneId, "iHello, World!");

// Send control sequences
await sendKeysRaw(paneId, "C-x C-s");  // Save file in emacs
await sendKeysRaw(paneId, "Escape");   // Exit insert mode in vim
```

### Why This Fork?

The original tmux-mcp wraps all commands with safety markers (`TMUX_MCP_START` and `TMUX_MCP_DONE`) to track command execution. While this is great for shell commands, it prevents sending keystrokes to interactive applications like text editors.

This fork maintains backward compatibility with all existing tools while adding the raw capability needed for voice-controlled code demonstrations.

## Version

- Original: 0.1.3
- Fork: 0.1.3-raw