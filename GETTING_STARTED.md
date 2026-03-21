# Getting Started: Disable Accessibility Permission Checks

## TL;DR (Too Long; Didn't Read)

Your company doesn't allow permission prompts? No problem! Run the app with one flag:

```bash
./handy --disable-permission-check
```

Or add this to your settings file:
```json
{
  "disable_permission_check_on_startup": true
}
```

That's it! The app will skip the permission check and work normally.

---

## What This Does

This feature allows you to disable the accessibility permission check that appears when Handy starts on macOS. This is useful if your organization has policies that restrict permission prompts at application startup.

## How to Use

### Method 1: Command Line (Recommended for Testing)

Simply add the flag when launching the app:

```bash
./handy --disable-permission-check
```

**Pros:**
- Easy to test
- No files to edit
- Takes effect immediately
- Temporary (doesn't affect next launch)

**Cons:**
- Only works for that single run
- Must include flag every time

### Method 2: Settings File (Recommended for Permanent Use)

1. Find your settings file:
   - **macOS**: `~/Library/Application Support/com.handy.app/settings.json`
   - **Linux**: `~/.config/handy/settings.json`
   - **Windows**: `%APPDATA%\handy\settings.json`

2. Open the file in a text editor

3. Add this line (if the setting doesn't already exist):
   ```json
   "disable_permission_check_on_startup": true
   ```

4. Save the file

5. Restart the app

**Pros:**
- Permanent (takes effect on every launch)
- No need for command-line flags
- Easy to distribute to multiple