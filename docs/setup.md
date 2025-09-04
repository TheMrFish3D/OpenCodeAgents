# Setup Instructions

This document provides instructions on how to set up this multi-agent system with `opencode`.

## 1. Place the Files

Place the `opencode.json` file in your project's root directory or in your global `opencode` configuration directory (`~/.config/opencode/`).

Place the `prompts/` directory in the same directory as your `opencode.json` file.

## 2. Configure Your Models

The `opencode.json` file is configured to use two local models: `gpt-oss-120b` and `gpt-oss-20b`. You need to replace the placeholder URLs with the actual URLs of your model servers.

Open the `opencode.json` file and find the `mcp` section:

```json
"mcp": {
  "gpt-oss-120b": {
    "type": "remote",
    "url": "http://your-local-model-server/gpt-oss-120b",
    "enabled": true
  },
  "gpt-oss-20b": {
    "type": "remote",
    "url": "http://your-local-model-server/gpt-oss-20b",
    "enabled": true
  }
},
```

Replace `"http://your-local-model-server/gpt-oss-120b"` and `"http://your-local-model-server/gpt-oss-20b"` with the correct URLs for your models.

## 3. (Optional) Install Recommended MCP Servers

For enhanced functionality, you can install one or more of the recommended MCP servers listed in `docs/recommended_mcp_servers.md`. The installation and configuration instructions for each server can be found in their respective documentation.

Once installed, you can add them to your `opencode.json` file in the `mcp` section. See `docs/mcp_servers.md` for more details on how to configure MCP servers.
