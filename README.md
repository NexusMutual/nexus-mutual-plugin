# Nexus Mutual Plugin

A [Claude Code plugin](https://code.claude.com/docs/en/plugins) that bundles the Nexus Mutual MCP server with advisory skills. One install gives you tools for products, pricing, capacity, cover terms, and claims history, plus guided workflows for cover sizing, term explanations, and claims analysis.

## Install (Claude Code)

Add the marketplace, then install the plugin:

```
/plugin marketplace add https://github.com/NexusMutual/nexus-mutual-plugin.git
/plugin install nexus-mutual@nexus-mutual
```

Once installed, the MCP tools are available automatically and skills activate based on context — ask about cover products and the products skill kicks in, ask about claims history and the claims skill takes over.

### Skills

| Skill | Activates when |
|-------|---------------|
| `/nexus-mutual:products` | Asking about cover products, pricing, what's covered/excluded, vault protection |
| `/nexus-mutual:claims` | Asking about claims history, approval rates, payout amounts, claims for a product |

### Tools

| Tool | Description |
|------|-------------|
| `list_products` | Browse and search all available cover products |
| `get_product_details` | Product info, supported cover assets, annex hash |
| `get_quote` | Real-time premium pricing for a given amount and period |
| `get_capacity` | Available cover capacity and utilization |
| `get_cover_wording` | Full cover terms (the main legal document for a product type) |
| `get_product_annex` | Product-specific details: covered vaults, tokens, thresholds, sub-limits |
| `get_wallet_positions` | Wallet DeFi positions via DeBank for cover sizing |
| `query_claims` | Query historical closed claims with filters (verdict, product, date range) |

## Other Platforms

If you're not using Claude Code, you can connect to the MCP server directly.

### Claude Desktop

Claude Desktop supports marketplaces via **Settings > Plugins > Add marketplace by URL**:

```
https://github.com/NexusMutual/nexus-mutual-plugin.git
```

Alternatively, add the MCP server directly to `~/Library/Application Support/Claude/claude_desktop_config.json` (macOS):

```json
{
  "mcpServers": {
    "nexus-mutual": {
      "url": "https://api.staging.nexusmutual.io/mcp"
    }
  }
}
```

Restart Claude Desktop after editing.

### Cursor

Add to your MCP configuration in Cursor settings:

```json
{
  "mcpServers": {
    "nexus-mutual": {
      "url": "https://api.staging.nexusmutual.io/mcp"
    }
  }
}
```

Note: Claude Desktop and Cursor get the MCP tools but not the skills. For the full guided experience, use Claude Code with this plugin.

## Links

- [Nexus Mutual App](https://app.nexusmutual.io) — Buy cover
- [Nexus Mutual MCP Server](https://github.com/NexusMutual/nexus-mutual-mcp) — Source code for the MCP server

## License

MIT
