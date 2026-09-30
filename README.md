# Fused Gaming Skills Repository

A skill-centric MCP (Model Context Protocol) repository for Fused Gaming. This repository contains the core MCP infrastructure and skill management system.

## Overview

This is a monorepo containing:

- **mcp-core**: Core MCP server and skill registry for managing dynamic skill loading and tool registration

## Project Structure

```
.
├── mcp-core/                    # Core MCP server and skill registry
│   ├── src/
│   │   ├── index.ts            # Main entry point
│   │   ├── config.ts           # Configuration management
│   │   ├── server.ts           # MCP server implementation
│   │   ├── skill-registry.ts   # Skill loading and management
│   │   ├── types.ts            # Type definitions
│   │   └── servers/
│   │       ├── sync-coordinator-server.ts
│   │       └── skill-repository-server.ts
│   ├── package.json
│   ├── tsconfig.json
│   └── README.md
├── package.json                # Root workspace configuration
└── README.md                    # This file
```

## Getting Started

### Prerequisites

- Node.js >= 18.0.0
- npm >= 8.0.0

### Installation

```bash
# Install dependencies for all workspaces
npm install
```

### Building

```bash
# Build all packages
npm run build

# Build in watch mode (development)
npm run dev
```

### Testing

```bash
# Run tests for all packages
npm run test
```

### Cleaning

```bash
# Remove all generated artifacts
npm run clean
```

## MCP Core Package

The `mcp-core` package provides:

- **SkillRegistry**: Dynamically loads and manages skill instances
- **Type definitions**: Standard interfaces for skills and tools
- **Configuration management**: Load/save skill configuration
- **MCP Server**: Stdio-based MCP server with skill tool registration

### Usage

```typescript
import { SkillRegistry } from "./mcp-core/src/index.ts";

const registry = new SkillRegistry();
const skill = await registry.loadSkill("my-skill");
console.log(skill?.tools);
```

## Architecture

### Skill Registry

The SkillRegistry manages the lifecycle of skills:

1. **Loading**: Dynamically loads skill instances with configuration
2. **Registration**: Registers skills and their tools with the MCP server
3. **Lifecycle**: Manages initialization and cleanup of skills

### MCP Server

The MCP server exposes skills' tools to MCP clients through the standard protocol.

## Development Workflow

### Adding a New Skill

1. Create a new workspace package in this repository
2. Implement the Skill interface from mcp-core
3. Register the skill with the SkillRegistry
4. Build and test

### Modifying MCP Core

```bash
# Make changes to mcp-core/src/
# Build the changes
npm run build --workspace=mcp-core

# Test the changes
npm run test --workspace=mcp-core
```

## Configuration

Configuration is managed through `.fused-gaming-mcp.json` files, which specify:

- Enabled skills
- Tool configurations
- Skill-specific settings

## Contributing

When contributing to this repository:

1. Make changes on a feature branch
2. Build and test locally
3. Create a pull request with a clear description
4. Ensure all tests pass before merging

## License

**Fused Gaming Skills Marketplace - Non-Commercial License v1.0**

- ✅ **Free for**: Individual use, education, research, academic institutions
- ❌ **Not free for**: Commercial use, revenue-generating services, business applications

### License Terms

This software is **free** for:
- Personal projects and experiments
- Educational purposes and learning
- Academic and research institutions
- Student projects and assignments
- Non-profit activities

**Commercial use requires a separate commercial license.** Contact playxrewards@gmail.com for commercial licensing.

See [LICENSE](./LICENSE) file for complete terms.

## Related Documentation

- See `mcp-core/README.md` for detailed MCP core documentation
- See `.fused-gaming-mcp.json` for configuration examples
