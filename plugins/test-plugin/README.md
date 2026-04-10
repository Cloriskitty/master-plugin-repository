# test-plugin

Bootstrap plugin for `master-plugin-repository`. It exists for one purpose: provide a working `submit-plugin` skill that hackathon participants (and the maintainer) can use to open submission PRs **before** the full `plugin-store-tools` plugin is available.

## Skills

- **submit-plugin** — interactive runbook that validates a plugin directory with inline sanity checks, then forks this repo, edits `.claude-plugin/marketplace.json`, and opens a PR through the `gh` CLI. Supports both external-repo and monorepo submission modes.

## Usage

```
/plugin marketplace add mastersamasama/master-plugin-repository
/plugin install test-plugin@master-plugin-repository
/reload-plugins
/test-plugin:submit-plugin
```

## Status

This plugin is a **bootstrap artifact**. Once `plugin-store-tools` is merged into the marketplace, its production `submit-plugin` skill — which calls the shared JSON Schema validator and runs inside CI — becomes the canonical path. `test-plugin` is kept as a minimal reference submission and may be deprecated post-hackathon.

## Requirements

- GitHub CLI (`gh`) installed and authenticated (`gh auth login`)
- Git installed
- Write access to GitHub (you'll be forking `mastersamasama/master-plugin-repository`)
