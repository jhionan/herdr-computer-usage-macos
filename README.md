# Herdr Computer Usage for macOS

A portable agent skill for using Herdr's `herdr-computer-use` MCP server to inspect and operate visible macOS desktop applications, including existing browser windows.

The skill is in [`SKILL.md`](SKILL.md). It assumes the Herdr Computer Use helper is installed, running, and configured as an MCP server. See the [Herdr Computer Use project](https://github.com/jhionan/herdr-computer-use) for helper setup and MCP configuration.

## Install

With the Skills CLI:

```sh
npx skills add jhionan/herdr-computer-usage-macos --skill computer-usage-macos
```

The MCP server setup is separate; installing this skill does not grant macOS permissions or configure the server.
