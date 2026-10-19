---
name: computer-usage-macos
description: Use when Herdr is asked to inspect or operate macOS desktop applications through the Herdr Computer Use MCP server.
---

# Herdr Computer Use for macOS

Use the `herdr-computer-use` MCP server to work with visible macOS applications, including existing browser windows. This skill applies only when that MCP server is configured and available to the agent.

## Start with readiness and observation

1. Call `computer_status` to check that the helper is connected and its Accessibility and screenshot permissions are granted. This check does not prompt or capture the screen.
2. Call `computer_list_apps`, then `computer_list_windows` when the target app has more than one window. Use the app identifier returned by discovery when possible.
3. Call `computer_get_app_state` for the target app/window. Use the accessibility tree to identify controls; request a screenshot only when visual context helps. Set `noScreenshot: true` when pixels are unnecessary.

Before every input action, use the most recent `snapshotId` and element index for that same app/window. Refresh the state after navigation, focus changes, scrolling, or any visible UI change; indices from an older snapshot or another agent are not reliable.

## Choose and verify actions

Prefer element-based actions when the accessibility tree identifies the target. Coordinate actions use logical points relative to the selected window, not the whole desktop. Convert screenshot pixels with `x = pixelX / screenshot.scale` and `y = pixelY / screenshot.scale`.

Available input tools are `computer_click`, `computer_secondary_action`, `computer_set_value`, `computer_type_text`, `computer_press_key`, `computer_paste_text`, `computer_scroll`, and `computer_drag`. Supply the snapshot and target fields required by each tool. For coordinate targets, provide complete coordinate pairs; for drags, provide both complete endpoints.

After each action, inspect its result and take a fresh state snapshot to verify the visible effect. A successful tool response means the action was delivered; it does not prove the application accepted it. If a call times out, disconnects, or reports an uncertain result, observe the current state before considering any retry. Never automatically replay an input action.

Treat typing into a composer or form as a draft. Do not press Enter, click Send/Submit, or otherwise finalize an external action unless the user asked you to do so. If the user asks for a draft only, verify the text is present and leave it unsent.

## Permissions and limits

If status or a tool reports missing Accessibility or Screen Recording permission, explain that the user must grant it in macOS System Settings. Do not try to bypass the permission prompt. If setup is needed, direct the user to the plugin's `setup` action or [setup instructions](../../docs/setup.md); status and inspection are not substitutes for consent.

The helper operates only on the local logged-in Mac desktop session. It does not provide remote desktop access, browser DOM access, or Linux/Windows support. If the MCP server is unavailable or the request targets another machine, explain the limitation rather than switching to an unrelated control path.
