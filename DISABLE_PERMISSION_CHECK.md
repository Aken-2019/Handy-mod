# Disable Accessibility Permission Check on macOS

## Problem
Your company doesn't allow permission prompts on app startup, but you want to use Handy.

## Solution
We added two ways to disable the accessibility permission check:

### Method 1: CLI Flag (Temporary - per session)
```bash
./handy --disable-permission-check
```

### Method 2: Settings File (Permanent)
Edit your settings file and add:
```json
{
  "disable_permission_check_on_startup": true
}
```

Settings file location:
- **macOS**: `~/Library/Application Support/com.handy.app/settings.json`
- **Linux**: `~/.config/handy/settings.json`
- **Windows**: `%APPDATA%\handy\settings.json`

## What Works
✅ Audio recording and transcription
✅ Model management
✅ History and post-processing
✅ Settings and configuration
✅ All other app features

## What May Need Extra Setup
⚠️ Keyboard shortcuts (global hotkeys) - requires manually granting accessibility permissions:
1. System Preferences → Security & Privacy → Accessibility
2. Add Handy to the allowed apps list
3. Restart Handy

## Verify It's Working
When disabled, you'll see in logs:
```
Accessibility permission check disabled via CLI flag or setting
```

## Code Changes
Modified 3 files:
- `src-tauri/src/cli.rs` - Added `--disable-permission-check` flag
- `src-tauri/src/settings.rs` - Added `disable_permission_check_on_startup` setting
- `src-tauri/src/lib.rs` - Skip permission check if disabled

All changes compile without errors and are backward compatible.