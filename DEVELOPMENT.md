# Development

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

## Plugin Source Types

The `source` field determines where Claude Code fetches the plugin from. There are five options:

### Relative Path

For plugins that live in the same repo as the marketplace. The path must start with `./` and resolves relative to the marketplace root (the directory containing `.claude-plugin/`). Only works when users add the marketplace via Git, not via a direct URL to `marketplace.json`.

```json
"source": "./plugins/my-plugin"
```

### GitHub

For plugins hosted on GitHub. Supports pinning to a specific branch, tag, or commit via `ref` and `sha`.

```json
"source": {
  "source": "github",
  "repo": "owner/repo",
  "ref": "v2.0.0",
  "sha": "a1b2c3d4e5f6a7b8c9d0e1f2a3b4c5d6e7f8a9b0"
}
```

### Git URL

For plugins on any git host (GitLab, Bitbucket, etc.). The `.git` suffix is optional. Supports `ref` and `sha` pinning.

```json
"source": {
  "source": "url",
  "url": "https://gitlab.com/team/plugin.git"
}
```

### Git Subdirectory

For plugins that live in a subdirectory of a monorepo. Uses sparse/partial clone to minimize bandwidth. Requires `url` and `path`. Supports `ref` and `sha` pinning.

```json
"source": {
  "source": "git-subdir",
  "url": "https://github.com/acme-corp/monorepo.git",
  "path": "tools/claude-plugin"
}
```

### npm Package

For plugins distributed as npm packages. Supports semver ranges (e.g., `^2.0.0`, `~1.5.0`) and private registries.

```json
"source": {
  "source": "npm",
  "package": "@acme/claude-plugin",
  "version": "2.1.0",
  "registry": "https://npm.example.com"
}
```

The `version` and `registry` fields are optional.

## Version Pinning

The GitHub, Git URL, and Git subdirectory sources all support two optional fields for version control:

- **`ref`** — a branch name or tag (e.g., `"main"`, `"v2.0.0"`)
- **`sha`** — an exact 40-character commit hash for reproducible installs

When both are provided, `sha` takes precedence.
