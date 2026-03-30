# claude-marketplace

A Claude Code plugin marketplace for custom skills and integrations.

## Available Plugins

| Plugin | Description |
|--------|-------------|
| **qgenda** | Query QGenda scheduling system for physician schedules, staff, shifts, requests, rotations, and more. |

## Installation

```bash
# Add the marketplace
claude plugin marketplace add lancereinsmith/claude-marketplace

# Install a plugin
claude plugin install qgenda@lancereinsmith
```

## Updating

```bash
claude plugin marketplace update lancereinsmith
claude plugin update qgenda@lancereinsmith
```

## Adding a New Plugin

To add a plugin to this marketplace, add an entry to `.claude-plugin/marketplace.json`:

```json
{
  "name": "my-plugin",
  "description": "What it does",
  "source": {
    "source": "url",
    "url": "https://github.com/owner/repo.git"
  },
  "category": "productivity"
}
```

Plugins can live in their own repos — this marketplace is just the index.
