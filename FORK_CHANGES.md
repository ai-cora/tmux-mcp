# Tmux MCP Fork - Enhanced Terminal Control

This is a fork of [nickgnd/tmux-mcp](https://github.com/nickgnd/tmux-mcp) with added capabilities for better terminal control and show-and-tell demonstrations.

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

### Added `select-pane` Tool

This fork adds a new tool `select-pane` that allows AI agents to programmatically switch focus between tmux panes, windows, and sessions. This is essential for show-and-tell demonstrations and terminal control workflows.

**Features**:
- Switch to any pane by ID (`%1`, `%2`)
- Switch to any window by ID (`@1`, `@2`) 
- Switch to any session by ID (`$0`, `$1`)
- Support for composite targets (`$0:@2.%3`)
- Previous pane tracking - call with no arguments to return to previous pane (like `cd -`)
- Flexible argument formats for different use cases

### Usage Examples

```javascript
// Switch to specific pane
await selectPane({ target: "%2" });

// Switch to window
await selectPane({ target: "@2" });

// Switch using components
await selectPane({ session: "cora", window: "ffmpeg-demo" });

// Return to previous pane
await selectPane({});  // Like cd -
```

## Version

- Original: 0.1.3
- Fork: 0.1.3-raw-select