# Configuring MCP Servers

This document explains how to configure MCP (Model Context Protocol) servers in your `opencode.json` file.

## What are MCP Servers?

MCP servers are external tools that can provide additional context and capabilities to your AI agents. They can be local tools that run as a subprocess or remote services that you connect to via a URL.

## Configuration

MCP servers are configured in the `mcp` section of your `opencode.json` file. Each server is an object with a unique key.

### Local Servers

Local servers run as a subprocess on your machine. You need to provide the command to start the server.

```json
"mcp": {
  "my-local-server": {
    "type": "local",
    "command": ["python", "my_mcp_server.py"],
    "enabled": true
  }
}
```

### Remote Servers

Remote servers are accessed via a URL.

```json
"mcp": {
  "my-remote-server": {
    "type": "remote",
    "url": "https://my-remote-mcp-server.com",
    "enabled": true,
    "headers": {
      "Authorization": "Bearer YOUR_API_KEY"
    }
  }
}
```

## Recommended Servers

Please see `docs/recommended_mcp_servers.md` for a list of recommended MCP servers that you can install and configure.

For detailed installation instructions, please refer to the documentation of each individual MCP server.
