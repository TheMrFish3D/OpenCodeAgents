# OpenCodeAgents Multi-Agent Workflow System

Always reference these instructions first and fallback to search or bash commands only when you encounter unexpected information that does not match the info here.

## Working Effectively

### Bootstrap the Development Environment
- Install OpenCode CLI: `npm install -g opencode-ai`
- Verify installation: `opencode --version` (should show version 0.6.4 or later)
- Verify Python 3: `python3 --version` (Python 3.12+ recommended)
- Test sample project: `cd sample_project && python3 -c "import calculator; print('Calculator import successful')"`

### Key Repository Structure
```
/
├── opencode.json              # Main agent configuration
├── prompts/                   # Agent prompt files
│   ├── orchestrator_prompt.txt
│   ├── architect_prompt.txt
│   ├── coder_prompt.txt
│   ├── tester_prompt.txt
│   ├── reviewer_prompt.txt
│   └── researcher_prompt.txt
├── docs/                      # Documentation
│   ├── setup.md              # Setup instructions
│   ├── usage.md              # Agent usage guide
│   ├── mcp_servers.md         # MCP server configuration
│   └── recommended_mcp_servers.md
├── sample_project/            # Example Python calculator
│   ├── calculator.py          # Simple calculator implementation
│   └── AGENTS.md             # Project-specific agent instructions
└── .github/
    └── copilot-instructions.md # This file
```

### Working with OpenCode Agents
- List available models: `opencode models`
- Start OpenCode TUI: `opencode` (from project root)
- Run with message: `opencode run "your message here"`
- View OpenCode help: `opencode --help`

### Agent Configuration
The repository defines 6 specialized agents in `opencode.json`:
1. **@orchestrator** (Primary) - Manages entire workflow using gpt-oss-120b
2. **@architect** (Sub-agent) - Designs software structure using gpt-oss-120b
3. **@coder** (Sub-agent) - Writes code using gpt-oss-20b
4. **@tester** (Sub-agent) - Creates tests using gpt-oss-20b
5. **@reviewer** (Sub-agent) - Reviews code quality using gpt-oss-120b
6. **@researcher** (Sub-agent) - Web research using gpt-oss-20b

### Model Server Setup Requirements
**CRITICAL**: The configuration requires local model servers. Update `opencode.json` URLs:
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
}
```

## Validation & Testing

### Validate Repository Setup
Always run these validation steps after making changes:
```bash
# Validate JSON configuration
python3 -c "import json; json.load(open('opencode.json'))" && echo "✓ opencode.json is valid"

# Test sample calculator
cd sample_project
python3 -c "
import calculator
assert calculator.add(2, 3) == 5
assert calculator.subtract(5, 2) == 3
assert calculator.multiply(4, 3) == 12
assert calculator.divide(10, 2) == 5.0
assert calculator.divide(10, 0) == 'Error! Division by zero.'
print('✓ Calculator functions work correctly')
"

# Test interactive calculator (manual validation required)
echo -e "1\n5\n3\n5" | python3 calculator.py
```

### Manual Validation Scenarios
**ALWAYS** test these scenarios after making configuration changes:
1. **Agent Configuration**: Validate `opencode.json` syntax and structure
2. **Calculator Import**: Ensure `import calculator` works from sample_project/
3. **Calculator Functions**: Test all arithmetic operations (add, subtract, multiply, divide)
4. **Interactive Mode**: Run calculator interactively and test user input handling
5. **Error Handling**: Verify division by zero returns proper error message

### No Build Process Required
This repository is primarily configuration-based with no traditional build/test infrastructure:
- **No package.json**: Pure configuration repository
- **No Makefile**: No compilation needed
- **No CI/CD**: No automated build pipelines
- **No Dependencies**: Only requires Python 3 and OpenCode CLI

## Common Tasks

### Repository Exploration (Reference Output)
```bash
# Root directory contents
$ ls -la
total 36
drwxr-xr-x 6 runner docker 4096 Sep  4 03:32 .
drwxr-xr-x 3 runner docker 4096 Sep  4 03:32 ..
drwxr-xr-x 7 runner docker 4096 Sep  4 03:32 .git
drwxr-xr-x 2 runner docker 4096 Sep  4 03:32 docs
-rw-r--r-- 1 runner docker 3455 Sep  4 03:32 future_tasks.md
-rw-r--r-- 1 runner docker 2772 Sep  4 03:32 opencode.json
drwxr-xr-x 2 runner docker 4096 Sep  4 03:32 prompts
-rw-r--r-- 1 runner docker 1133 Sep  4 03:32 readme.md
drwxr-xr-x 3 runner docker 4096 Sep  4 03:33 sample_project

# Available OpenCode models (when properly configured)
$ opencode models
opencode/x-ai/grok-code-fast-1
opencode/qwen/qwen3-coder
```

### Working with Agent Prompts
- Agent prompts are stored in `prompts/` directory
- Each agent has a dedicated prompt file (e.g., `orchestrator_prompt.txt`)
- Modify prompts to customize agent behavior
- Always validate `opencode.json` syntax after prompt changes

### Adding New MCP Servers
1. Review `docs/recommended_mcp_servers.md` for options
2. Install chosen MCP server per its documentation
3. Add configuration to `opencode.json` mcp section
4. Test with `opencode models` or `opencode run`

### Sample Project Development
The `sample_project/` contains a working Python calculator:
- **Location**: `sample_project/calculator.py`
- **Functions**: add(), subtract(), multiply(), divide()
- **Interactive**: Run with `python3 calculator.py`
- **Testing**: Import and call functions directly
- **Agent Instructions**: See `sample_project/AGENTS.md`

## Troubleshooting

### Common Issues
- **"OpenCode CLI not found"**: Run `npm install -g opencode-ai`
- **"Model server connection failed"**: Update URLs in `opencode.json` to point to running model servers
- **"JSON syntax error"**: Validate with `python3 -c "import json; json.load(open('opencode.json'))"`
- **"Calculator import fails"**: Ensure you're in `sample_project/` directory

### Required External Dependencies
- **Node.js/npm**: For OpenCode CLI installation
- **Python 3.12+**: For sample project and validation scripts
- **Local Model Servers**: Must be running on configured URLs for full functionality

### Performance Notes
- Agent responses depend on model server performance
- No long-running builds or timeouts to consider
- Configuration changes take effect immediately
- Sample calculator runs instantly (<1 second)

### File Modification Guidelines
- **Always validate**: `opencode.json` syntax after editing
- **Test imports**: Verify Python modules still import correctly
- **Update prompts**: Modify agent behavior through prompt files
- **Document changes**: Update relevant documentation when adding features

## Important Locations
- **Main config**: `/opencode.json` - Core agent and MCP server configuration
- **Agent prompts**: `/prompts/` - Individual agent behavior definitions
- **Setup guide**: `/docs/setup.md` - Complete setup instructions
- **Usage examples**: `/docs/usage.md` - Agent interaction examples
- **Sample code**: `/sample_project/calculator.py` - Working example application
- **MCP servers**: `/docs/recommended_mcp_servers.md` - External tool options