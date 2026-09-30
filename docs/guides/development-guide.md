<!-- Version Control
- Version: 1.0.1
- Last Updated: 2026-09-30
- Status: active
- Repository: Fused-Gaming/skills
-->

# Skill Development Guide

## Creating a New Skill

### Project Structure

When creating a new skill for the Fused Gaming marketplace:

```
my-skill/
├── src/
│   ├── index.ts           # Main skill implementation
│   ├── types.ts           # Type definitions
│   ├── tools/             # Tool implementations
│   └── utils/             # Helper functions
├── tests/                 # Test files
├── package.json           # Skill package config
├── tsconfig.json          # TypeScript config
└── README.md              # Skill documentation
```

### Implementing the Skill Interface

```typescript
import { Skill, Tool } from '@modelcontextprotocol/sdk';

export class MySkill implements Skill {
  name = 'my-skill';
  version = '1.0.0';
  
  tools: Tool[] = [
    {
      name: 'my-tool',
      description: 'Does something useful',
      inputSchema: {
        type: 'object',
        properties: {
          param1: { type: 'string' }
        }
      }
    }
  ];

  async initialize() {
    // Setup code
  }

  async execute(toolName: string, input: any) {
    if (toolName === 'my-tool') {
      // Implement tool logic
    }
  }

  async cleanup() {
    // Cleanup code
  }
}
```

## Development Workflow

### 1. Set Up Your Workspace

```bash
# Clone the repository
git clone https://github.com/Fused-Gaming/skills.git
cd skills

# Install dependencies
npm install

# Create a feature branch
git checkout -b feature/my-skill
```

### 2. Implement Your Skill

1. Create skill package in the repository
2. Implement the Skill interface
3. Add comprehensive documentation
4. Write unit tests

### 3. Build and Test

```bash
# Build all packages
npm run build

# Run tests
npm run test

# Build in development mode
npm run dev
```

### 4. Register Your Skill

Update `marketplace-registry.json` to include your skill:

```json
{
  "skills": [
    {
      "id": "my-skill",
      "name": "My Skill",
      "version": "1.0.0",
      "category": "custom",
      "description": "My skill description",
      "author": "Your Name",
      "status": "active"
    }
  ]
}
```

### 5. Create a Pull Request

1. Push your branch to GitHub
2. Create a PR with detailed description
3. Ensure all tests pass
4. Address review feedback

## Testing

### Unit Tests

```bash
npm run test --workspace=my-skill
```

### Integration Tests

```bash
npm run test:integration
```

### MCP Protocol Compliance

Ensure your skill properly implements the MCP tool interface and can be loaded by the SkillRegistry.

## Documentation Requirements

Every skill must include:

1. **README.md** - Usage and overview
2. **Type definitions** - Exported interfaces
3. **Tool descriptions** - Clear parameter documentation
4. **Examples** - Usage examples for each tool
5. **Error handling** - Expected errors and recovery

## Best Practices

1. **Use TypeScript** for type safety
2. **Write comprehensive tests** with >80% coverage
3. **Document all public APIs** with JSDoc comments
4. **Follow the Skill interface** contract strictly
5. **Avoid external dependencies** where possible
6. **Handle errors gracefully** and provide meaningful error messages
7. **Version your skills** using semantic versioning
8. **Test MCP protocol compliance** thoroughly

## Publishing

### Version Bump

Update version in package.json and VERSION.json:
- Patch: Bug fixes and minor updates
- Minor: New features
- Major: Breaking changes

### Create Release Tag

```bash
git tag -a v1.0.0 -m "Release version 1.0.0"
git push origin v1.0.0
```

### Update Marketplace

Add skill entry to `marketplace-registry.json` with all metadata.

## Troubleshooting

### Build Errors

1. Check TypeScript compilation: `npm run build`
2. Verify all dependencies are installed
3. Check for circular imports

### Test Failures

1. Run tests in isolation: `npm run test -- --testNamePattern="test name"`
2. Check for timing issues in async tests
3. Verify mock setup is correct

### MCP Registration Issues

1. Verify Skill interface implementation
2. Check tool schemas are valid JSON Schema
3. Ensure tool names are unique

## Resources

- [MCP Specification](../reference/MARKETPLACE.md)
- [Skills Catalog](../reference/SKILLS_CATALOG.md)
- [Integration Guide](./integration-guide.md)

