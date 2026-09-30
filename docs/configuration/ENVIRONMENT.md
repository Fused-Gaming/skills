<!-- Version Control
- Version: 1.0.1
- Last Updated: 2026-09-30
- Status: active
- Repository: Fused-Gaming/skills
-->

# Environment Setup Guide

## Prerequisites

- **Node.js**: >= 18.0.0
- **npm**: >= 8.0.0
- **git**: >= 2.20.0

## Installation

### 1. Clone the Repository

```bash
git clone https://github.com/Fused-Gaming/skills.git
cd skills
```

### 2. Install Dependencies

```bash
# Install all workspace dependencies
npm install

# Or use clean install with lockfile
npm ci
```

### 3. Verify Installation

```bash
npm run build
npm run test
```

## Environment Variables

Create a `.env` file in the root directory:

```env
# Node environment
NODE_ENV=development

# MCP Server Configuration
MCP_SERVER_PORT=3000
MCP_DEBUG=false

# Skill Registry Configuration
SKILL_REGISTRY_PATH=./mcp-core/src/skill-registry.ts
SKILL_CONFIG_PATH=.fused-gaming-mcp.json

# Logging
LOG_LEVEL=info
```

## Configuration Files

### .fused-gaming-mcp.json

Main configuration file for skills and tools:

```json
{
  "version": "1.0.1",
  "enabledSkills": [
    "skill-1",
    "skill-2"
  ],
  "toolConfigurations": {
    "skill-1": {
      "option1": "value1",
      "option2": "value2"
    }
  },
  "mcp": {
    "port": 3000,
    "debug": false
  }
}
```

### package.json Configuration

Key scripts and workspace configuration:

```json
{
  "scripts": {
    "build": "npm run build --workspaces",
    "dev": "npm run dev --workspaces",
    "test": "npm run test --workspaces",
    "clean": "rm -rf node_modules mcp-core/node_modules mcp-core/dist"
  },
  "workspaces": [
    "mcp-core"
  ]
}
```

## Development Setup

### 1. Start Development Mode

```bash
npm run dev
```

This starts the MCP server in watch mode with automatic recompilation.

### 2. Run Tests

```bash
npm run test
```

### 3. Build for Production

```bash
npm run build
```

## IDE Setup

### VSCode

1. Install TypeScript extension
2. Enable workspace TypeScript version:
   - Cmd+Shift+P → "TypeScript: Select TypeScript Version"
   - Choose "Use Workspace Version"

### IntelliJ / WebStorm

1. Mark `mcp-core/src` as Sources Root
2. Enable TypeScript compiler
3. Configure run configurations for npm scripts

## Troubleshooting

### Port Already in Use

```bash
# Change port in .fused-gaming-mcp.json
# Or kill existing process
lsof -i :3000 | grep LISTEN | awk '{print $2}' | xargs kill -9
```

### Module Resolution Issues

```bash
# Clean install
npm clean-install

# Rebuild dependencies
npm rebuild
```

### TypeScript Compilation Errors

```bash
# Clear cache
rm -rf mcp-core/dist

# Rebuild
npm run build
```

## Testing Locally

### Unit Tests

```bash
npm run test
```

### Integration Testing

```bash
# Start MCP server
npm run dev

# In another terminal, test connections
curl http://localhost:3000/status
```

## Next Steps

- See [Integration Guide](../guides/integration-guide.md) for usage examples
- Check [Development Guide](../guides/development-guide.md) for creating skills
- Review [VERSION.json](./VERSION.json) for current version and metadata

## Support

For issues or questions:
1. Check [MANIFEST.md](./MANIFEST.md) for system information
2. Review error logs in console output
3. Verify configuration matches examples

