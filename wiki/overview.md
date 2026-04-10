---
title: Shuk Overview
summary: What Shuk is and how it works
updated: 2026-04-10
---

# Shuk Overview

Shuk is a Claude Code plugin marketplace maintained by idl3. It provides a registry where plugins can be discovered, installed, and versioned through the Claude Code plugin system.

## How It Works

### Discovery

Plugins are listed in the marketplace registry. Users add the marketplace as a source, then browse or install available plugins by name.

```bash
/plugin marketplace add idl3/shuk-marketplace
```

### Installation

Plugins are installed from the marketplace by name with an `@shuk-marketplace` scope qualifier:

```bash
/plugin install diakon@shuk-marketplace
```

The plugin system resolves the source URL from the marketplace manifest, clones the repository, and registers the plugin's skills and commands locally.

### Versioning

Each plugin entry in the manifest includes a `version` field (semver). The marketplace tracks the current published version. Updates are picked up when the marketplace registry is refreshed.

## The marketplace.json Manifest

The manifest lives at `.claude-plugin/marketplace.json` and defines the marketplace metadata and its plugin catalog.

### Structure

```json
{
  "name": "shuk-marketplace",
  "owner": {
    "name": "Owner Name",
    "url": "https://github.com/owner"
  },
  "plugins": [
    {
      "name": "plugin-short-name",
      "source": {
        "source": "url",
        "url": "https://github.com/owner/repo.git"
      },
      "version": "0.1.0",
      "description": "What the plugin does.",
      "author": { "name": "Author", "url": "https://github.com/author" },
      "homepage": "https://github.com/owner/repo",
      "repository": "https://github.com/owner/repo",
      "license": "SPDX-ID",
      "keywords": ["relevant", "tags"]
    }
  ]
}
```

### Plugin Fields

| Field | Required | Description |
|-------|----------|-------------|
| `name` | yes | Short identifier used in install commands |
| `source.url` | yes | Git URL to clone |
| `version` | yes | Current semver version |
| `description` | yes | One-line summary |
| `author` | yes | Name and URL of the plugin author |
| `homepage` | no | Landing page URL |
| `repository` | no | Source repository URL |
| `license` | no | SPDX license identifier |
| `keywords` | no | Tags for discovery |

## Current Plugins

| Plugin | Version | Description |
|--------|---------|-------------|
| **diakon** (`dk`) | 0.1.4 | Multi-project workspace orchestration — manage projects, git operations, and encrypted secrets across a unified workspace |

Diakon is the first and currently only plugin hosted on Shuk.
