# claude-plugins

A [Claude Code](https://code.claude.com) plugin marketplace from [WireSage](https://github.com/wiresage). It lists plugins
that bundle WireSage projects, so one command installs everything a plugin needs.

## Add the marketplace

In a Claude Code session:

```text
/plugin marketplace add wiresage/claude-plugins
```

Or from your shell:

```bash
claude plugin marketplace add wiresage/claude-plugins
```

## Install a plugin

The marketplace is named `wiresage`, so a plugin installs as `<plugin>@wiresage`:

```text
/plugin install mikrotik@wiresage
```

Or from your shell:

```bash
claude plugin install mikrotik@wiresage
```

## Available plugins

| Plugin | What it does |
| :- | :- |
| [`mikrotik`](#mikrotik) | RouterOS skills, an MCP server that manages MikroTik routers, and a language server for `.rsc` scripts. |

### mikrotik

The plugin bundles three projects. Each one stays in its own repository and has its own releases; this marketplace only
references them.

| Component | Repository | What you get |
| :- | :- | :- |
| Skills | [routeros-skills](https://github.com/wiresage/routeros-skills) | 34 skills on RouterOS 7: firewall, routing, VPN, wireless, scripting and more. |
| MCP server | [mikrotik-mcp](https://github.com/wiresage/mikrotik-mcp) | Tools to read and change a router over SSH, started as `uvx mcp-server-mikrotik`. |
| Language server | [routeros-lsp](https://github.com/wiresage/routeros-lsp) | Syntax errors, unknown commands and parameters, and completions for `.rsc` files, started as `uvx routeros-lsp --stdio`. |

The skills come from the plugin source, the `routeros-skills` repository. The MCP server and the language server run from
their PyPI packages, which are built from their repositories, so they are always the latest release.

**Requirements:** [uv](https://docs.astral.sh/uv/), which provides `uvx`.

**Connect a router:** the MCP server reads its settings from environment variables, so set them before you start Claude
Code. For one router:

```bash
export MIKROTIK_HOST=192.168.88.1
export MIKROTIK_USERNAME=admin
export MIKROTIK_PASSWORD=...        # or MIKROTIK_KEY_FILENAME=/path/to/key
```

Use `MIKROTIK_INVENTORY_FILE` for several routers and `MIKROTIK_READ_ONLY=true` to hide every tool that changes a router.
The [mikrotik-mcp installation guide](https://github.com/wiresage/mikrotik-mcp/blob/master/docs/getting-started/installation.md)
lists the settings.

## License

[MIT](LICENSE)
