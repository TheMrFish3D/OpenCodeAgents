# OpenCodeAgents

A comprehensive multi-agent system configuration for software development, research, and ideation using [OpenCode](https://opencode.ai).

## Overview

OpenCodeAgents provides a pre-configured team of AI agents designed to collaborate on software development projects. Each agent has specialized roles and capabilities, working together through an orchestrator to complete complex tasks efficiently.

## Features

- **🤖 Multi-Agent Architecture**: Six specialized agents working in coordination
- **🔧 Configurable Models**: Support for local and remote model servers
- **📁 File-Based Communication**: Simple inter-agent communication system
- **🛠️ MCP Server Integration**: Extensible tool ecosystem
- **📚 Comprehensive Documentation**: Detailed setup and usage guides

## Agent Roles

| Agent | Role | Description |
|-------|------|-------------|
| `@orchestrator` | Primary Agent | Manages the entire workflow and delegates tasks |
| `@architect` | Sub-agent | Designs software structure and architecture |
| `@coder` | Sub-agent | Writes clean, efficient, and maintainable code |
| `@tester` | Sub-agent | Creates comprehensive tests for the code |
| `@reviewer` | Sub-agent | Reviews code for quality and best practices |
| `@researcher` | Sub-agent | Finds information on the web to help other agents |

## Quick Start

### 1. Setup

1. Clone this repository
2. Place `opencode.json` in your project root or `~/.config/opencode/`
3. Place the `prompts/` directory alongside your `opencode.json`
4. Configure your model servers (see [Setup Guide](docs/setup.md))

### 2. Basic Usage

Start by talking to the orchestrator:

```
@orchestrator Please create a simple web server with error handling and write tests for it.
```

The orchestrator will coordinate with other agents to complete the task.

## Configuration

### Model Configuration

The system is configured to use two models:
- `gpt-oss-120b` - For complex reasoning and orchestration
- `gpt-oss-20b` - For coding and testing tasks

Update the URLs in `opencode.json` to point to your model servers:

```json
{
  "mcp": {
    "gpt-oss-120b": {
      "type": "remote",
      "url": "http://your-local-model-server/gpt-oss-120b",
      "enabled": true
    }
  }
}
```

### MCP Servers

The system supports various MCP servers for enhanced functionality. See [Recommended MCP Servers](docs/recommended_mcp_servers.md) for a curated list of useful tools.

## Documentation

- **[Setup Instructions](docs/setup.md)** - Detailed installation and configuration guide
- **[Usage Guide](docs/usage.md)** - How to use the agents effectively
- **[MCP Server Configuration](docs/mcp_servers.md)** - Configure external tools
- **[Recommended MCP Servers](docs/recommended_mcp_servers.md)** - Curated list of useful servers
- **[Future Tasks](future_tasks.md)** - Planned enhancements and new features

## Example Project

The `sample_project/` directory contains a simple calculator example that demonstrates how the agents work together on a real project.

## Project Structure

```
├── opencode.json              # Agent configuration
├── prompts/                   # Agent prompt templates
│   ├── orchestrator_prompt.txt
│   ├── architect_prompt.txt
│   ├── coder_prompt.txt
│   ├── tester_prompt.txt
│   ├── reviewer_prompt.txt
│   └── researcher_prompt.txt
├── docs/                      # Documentation
├── sample_project/            # Example calculator project
└── development_notes.md       # Original development notes
```

## Contributing

When contributing to this project:

1. Follow the existing code style and conventions
2. Update documentation for any configuration changes
3. Test your changes with the sample project
4. Do not modify `development_notes.md` (contains historical context)

## Resources

- [OpenCode Documentation](https://opencode.ai/docs/)
- [Model Context Protocol](https://modelcontextprotocol.org/)
- [OpenCode GitHub](https://github.com/opencode-ai)

## License

This project is open source. Please check individual MCP servers for their respective licenses. 
