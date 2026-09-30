<!-- Version Control
- Version: 1.0.1
- Last Updated: 2026-09-30
- Status: active
- Repository: Fused-Gaming/skills
-->

# Skills Integration Guide

## Overview

This guide explains how to integrate Fused Gaming skills into your Claude AI applications and environments.

## Quick Start

### 1. Installation

The MCP Core infrastructure is published as `@h4shed/mcp-core`:

```bash
npm install @h4shed/mcp-core
```

### 2. Import and Use

```typescript
import { SkillRegistry } from '@h4shed/mcp-core';

const registry = new SkillRegistry();
const skill = await registry.loadSkill('your-skill-name');
console.log(skill?.tools);
```

**Note**: This repository (`Fused-Gaming/skills`) is the development workspace. The production package is `@h4shed/mcp-core` on npm.

## Working with Skill Registry

The SkillRegistry manages the complete lifecycle of skills:

- **Loading**: Dynamically loads skill instances with configuration
- **Registration**: Registers skills and their tools with the MCP server
- **Lifecycle**: Manages initialization and cleanup of skills

### Configuration

Skills are configured through `.fused-gaming-mcp.json` files:

```json
{
  "enabledSkills": ["skill-1", "skill-2"],
  "toolConfigurations": {
    "skill-1": {
      "option1": "value1"
    }
  }
}
```

## MCP Server Integration

### Starting the MCP Server

```bash
npm run build
npm run dev
```

The MCP server exposes all registered skills' tools through the standard MCP protocol.

## Available Skills Categories

- **Legal Services** (23 skills)
- **Case Management** (10 skills)
- **Workflow Management** (8 skills)
- **Data Management** (6 skills)
- And 8 more categories...

See [Skills Catalog](../reference/SKILLS_CATALOG.md) for the complete list.

## Best Practices

1. **Always validate skill configuration** before loading
2. **Use proper error handling** when loading skills
3. **Keep skill registry instances** for the lifetime of your application
4. **Document custom skill implementations** following the same structure
5. **Test skill interactions** with other tools before production deployment

## Troubleshooting

### Skill Not Loading

1. Check that the skill name is correct
2. Verify the configuration file exists
3. Check console logs for detailed error messages

### Tool Registration Issues

1. Ensure MCP server is running
2. Verify skill implements the Skill interface
3. Check that all required tool fields are defined

## Next Steps

- See [Development Guide](./development-guide.md) for creating custom skills
- Check [Configuration Guide](../configuration/ENVIRONMENT.md) for advanced setup
- Review [Release Notes](../releases/RELEASE_v1.0.1.md) for latest updates

