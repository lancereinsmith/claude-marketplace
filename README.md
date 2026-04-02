# Claude Plugin Marketplace (v.0.1.1)

A Claude Code plugin marketplace for custom skills and integrations.

## Available Plugins

| Plugin | Description | Install |
|--------|-------------|---------|
| **qgenda** | Query the QGenda scheduling system for physician schedules, staff, shifts, requests, rotations, and more. | `claude plugin install qgenda@lancereinsmith` |

## Getting Started

```bash
# Add the marketplace
claude plugin marketplace add lancereinsmith/claude-marketplace

# Install a plugin
claude plugin install <plugin-name>@lancereinsmith
```

## Updating the Marketplace and Plugins

```bash
# Update the marketplace index
claude plugin marketplace update lancereinsmith

# Update a specific plugin
claude plugin update <plugin-name>@lancereinsmith
```
