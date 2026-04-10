# master-plugin-repository

**OKX Internal Claude Code Plugin Marketplace** — the official submission target for the OKX internal hackathon.

> 简体中文版本： [README.zh-Hans.md](./README.zh-Hans.md)

## What this is

A Claude Code plugin marketplace. Once you add it, every plugin submitted to the hackathon becomes discoverable inside Claude Code's `/plugin` interface and installable with one command.

## Who it's for

Authorized OKX personnel and hackathon participants only. Use is governed by the [LICENSE](./LICENSE) — confidential, internal-use-only, no redistribution without OKX Legal approval.

## Add this marketplace to Claude Code

In any Claude Code session:

```
/plugin marketplace add mastersamasama/master-plugin-repository
```

Then open the marketplace UI:

```
/plugin
```

You'll see submitted plugins under the **Discover** tab.

## Install a plugin

Pick a plugin from the list and run:

```
/plugin install <plugin-name>@master-plugin-repository
/reload-plugins
```

The plugin's skills/commands are then invokable in your current session.

## Submit a plugin (bootstrap flow)

> **Phase A (current):** install `test-plugin` and use its `submit-plugin` skill to open a submission PR. This is the bootstrap path until `plugin-store-tools` is merged.
>
> **Phase B (coming):** install `plugin-store-tools` for the full toolkit — `scaffold-plugin`, `validate-plugin`, `skill-to-plugin`, and a production-grade `submit-plugin` that calls the shared validator.

Bootstrap steps:

1. `/plugin marketplace add mastersamasama/master-plugin-repository`
2. `/plugin install test-plugin@master-plugin-repository`
3. `/reload-plugins`
4. `/test-plugin:submit-plugin` — an interactive runbook that asks for your plugin directory, runs sanity checks, forks this repo, and opens a PR.

You can submit in either **external** mode (your plugin lives in your own repo; the PR only adds a `marketplace.json` entry pointing at it) or **monorepo** mode (your plugin directory is copied under `plugins/` here).

## Repository layout

```
.claude-plugin/marketplace.json     # the catalog
plugins/test-plugin/                # bootstrap plugin, ships submit-plugin
LICENSE                             # OKX proprietary notice
README.md                           # you are here
README.zh-Hans.md                   # 简体中文
```

## Compliance notice

This repository and every plugin inside it are confidential OKX property. Do not publish, fork externally, or share outside authorized OKX channels. Submissions must contain no secrets, no confidential OKX data, and no third-party IP you do not have rights to. See [LICENSE](./LICENSE) for the full terms.

## Questions

Open an issue inside this repo or contact the hackathon organizers through internal OKX channels.
