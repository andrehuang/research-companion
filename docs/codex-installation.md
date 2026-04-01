# Codex Installation

Research Companion supports Codex plugins and includes the files Codex expects:

- `.codex-plugin/plugin.json`
- `agents/openai.yaml`
- `.agents/plugins/marketplace.json`

## Recommended: repo marketplace

Codex supports marketplaces in the app and CLI Plugin Directory. This repository includes a repo-scoped marketplace file so you can install the plugin after cloning, without manually writing marketplace JSON.

At the time of writing, Codex has an official Plugin Directory and marketplace support, but official public self-serve plugin publishing is still rolling out. That means this plugin is easiest to install from the repo marketplace today.

### Steps

1. Clone the repository:

```bash
git clone https://github.com/andrehuang/research-companion.git
```

2. Open the cloned repository in Codex.

3. If Codex was already open, restart it so the repo marketplace at `.agents/plugins/marketplace.json` is picked up.

4. Open the Plugin Directory.

In the CLI:

```bash
codex
/plugins
```

In the desktop app, open **Plugins**.

5. Choose the **Research Companion** marketplace, open the plugin, and install it.

6. Start a new thread and invoke it with `@research-companion` or `$research-companion`.

## Manual: personal local marketplace

If you want to install it outside the repo marketplace flow, you can add it to your personal Codex marketplace.

### Steps

1. Clone the repository:

```bash
git clone https://github.com/andrehuang/research-companion.git
```

2. Create the local plugin directories:

```bash
mkdir -p ~/.agents/plugins ~/.codex/plugins
```

3. Copy the repository into your personal Codex plugin directory:

```bash
cp -R /path/to/research-companion ~/.codex/plugins/research-companion
```

4. Create or update `~/.agents/plugins/marketplace.json` and add:

```json
{
  "name": "local-plugins",
  "interface": {
    "displayName": "Local Plugins"
  },
  "plugins": [
    {
      "name": "research-companion",
      "source": {
        "source": "local",
        "path": "./.codex/plugins/research-companion"
      },
      "policy": {
        "installation": "AVAILABLE",
        "authentication": "ON_INSTALL"
      },
      "category": "Productivity"
    }
  ]
}
```

If the file already exists, append the `research-companion` object to the existing `plugins` array instead of replacing the whole file.

5. Restart Codex, install the plugin from the Plugin Directory, and invoke it with `@research-companion` or `$research-companion`.

## Official docs

- [Plugins overview](https://developers.openai.com/codex/plugins)
- [Build plugins](https://developers.openai.com/codex/plugins/build)
