# Herdr Computer Usage for macOS

A portable agent skill for using Herdr's `herdr-computer-use` MCP server to inspect and operate visible macOS desktop applications, including existing browser windows.

The skill is in [`SKILL.md`](SKILL.md). It assumes the Herdr Computer Use helper is installed, running, and configured as an MCP server. See the [Herdr Computer Use project](https://github.com/jhionan/herdr-computer-use) for helper setup and MCP configuration.

## Install

Choose the method that fits your setup. Installing the skill does not install the helper, grant macOS permissions, or configure the MCP server.

### Install the Skills CLI globally

Install the CLI once, then use the `skills` command directly:

```sh
npm install --global skills
skills add jhionan/herdr-computer-usage-macos --skill computer-usage-macos
```

You can also use another package manager's one-shot runner:

```sh
pnpm dlx skills add jhionan/herdr-computer-usage-macos --skill computer-usage-macos
# or
bunx skills add jhionan/herdr-computer-usage-macos --skill computer-usage-macos
```

### Install manually

For Codex's global skills directory:

```sh
git clone --depth 1 https://github.com/jhionan/herdr-computer-usage-macos.git /tmp/herdr-computer-usage-macos
mkdir -p ~/.agents/skills/computer-usage-macos
cp /tmp/herdr-computer-usage-macos/SKILL.md ~/.agents/skills/computer-usage-macos/SKILL.md
```

For another agent, copy `SKILL.md` into that agent's documented skills directory as `computer-usage-macos/SKILL.md`. You can also download [`SKILL.md`](https://raw.githubusercontent.com/jhionan/herdr-computer-usage-macos/main/SKILL.md) directly and place it there.

The Skills CLI supports other install scopes and agent targets; see its [installation guide](https://github.com/vercel-labs/skills#installation-scope).
