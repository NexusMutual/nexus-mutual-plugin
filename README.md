# Nexus Mutual Plugin

A plugin that bundles the Nexus Mutual MCP server with advisory skills. One install gives you tools for products, pricing, capacity, cover terms, and claims history, plus guided workflows for cover sizing, term explanations, and claims analysis.

Works with **Claude Code**, **Cursor**, and **Claude Desktop**.

## Skills

| Skill | Activates when |
|-------|---------------|
| `/nexus-mutual:products` | Asking about cover products, pricing, what's covered/excluded, vault protection |
| `/nexus-mutual:claims` | Asking about claims history, approval rates, payout amounts, claims for a product |

## Tools

See the [MCP server repo](https://github.com/NexusMutual/nexus-mutual-mcp) for the full list of tools and configuration options.

## Install

### Claude Code

```bash
claude plugin install --from https://github.com/NexusMutual/nexus-mutual-plugin.git
```

Or test locally:

```bash
claude --plugin-dir /path/to/nexus-mutual-plugin
```

### Cursor

Clone and symlink into the local plugins directory:

```bash
git clone https://github.com/NexusMutual/nexus-mutual-plugin.git
ln -s "$(pwd)/nexus-mutual-plugin/nexus-mutual" ~/.cursor/plugins/local/nexus-mutual
```

Restart Cursor. Skills appear in **Settings > Rules > Agent Decides** and are invocable via `/nexus-mutual:products` and `/nexus-mutual:claims`.

### Claude Desktop

Add the marketplace via **Settings > Plugins > Add marketplace by URL**:

```
https://github.com/NexusMutual/nexus-mutual-plugin.git
```

Or add the MCP server directly to `~/Library/Application Support/Claude/claude_desktop_config.json` (macOS):

```json
{
  "mcpServers": {
    "nexus-mutual": {
      "url": "https://api.staging.nexusmutual.io/mcp"
    }
  }
}
```

## Links

- [Nexus Mutual App](https://app.nexusmutual.io) — Buy cover
- [Nexus Mutual MCP Server](https://github.com/NexusMutual/nexus-mutual-mcp) — Source code for the MCP server

## License

MIT
