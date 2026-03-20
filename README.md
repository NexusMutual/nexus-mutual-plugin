# Nexus Mutual Plugin

A plugin that bundles the Nexus Mutual MCP server with advisory skills. One install gives you tools for products, pricing, capacity, cover terms, and claims history, plus guided workflows for cover sizing, term explanations, and claims analysis.

Works with **Claude Code**, **Cursor**, and **Claude Desktop**.

## Skills

| Skill | Activates when |
|-------|---------------|
| `/nexus-mutual:products` | Asking about cover products, pricing, what's covered/excluded, vault protection |
| `/nexus-mutual:claims` | Asking about claims history, approval rates, payout amounts, claims for a product |

## Tools

| Tool | Description |
|------|-------------|
| `list_products` | Browse and search all available cover products |
| `get_product_details` | Product info, supported cover assets, annex hash, commission |
| `get_quote` | Real-time premium pricing for a given amount and period |
| `get_capacity` | Available cover capacity and utilization |
| `get_cover_wording` | Full cover terms (the main legal document for a product type) |
| `get_product_annex` | Product-specific details: covered vaults, tokens, thresholds, sub-limits |
| `get_wallet_positions` | Wallet DeFi positions via DeBank for cover sizing |
| `query_claims` | Query historical closed claims with filters (verdict, product, date range) |

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
