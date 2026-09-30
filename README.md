<!-- Version Control
- Version: 1.0.1
- Last Updated: 2026-09-30
- Status: active
- Repository: Fused-Gaming/skills
-->

# Fused Gaming Skills

A comprehensive, production-ready skill marketplace for Fused Gaming powered by MCP (Model Context Protocol).

**Version**: 1.0.1 | **Status**: Stable | **License**: Apache-2.0 + Non-Commercial

## Quick Links

- 📖 [Getting Started](./docs/getting-started/README.md)
- 🔧 [Integration Guide](./docs/guides/integration-guide.md)
- 👨‍💻 [Development Guide](./docs/guides/development-guide.md)
- ⚙️ [Environment Setup](./docs/configuration/ENVIRONMENT.md)
- 📋 [Skills Catalog](./docs/reference/SKILLS_CATALOG.md)
- 📦 [Marketplace Reference](./docs/reference/MARKETPLACE.md)
- 📝 [Release Notes](./docs/releases/RELEASE_v1.0.1.md)
- 📄 [Changelog](./CHANGELOG.md)

## What's Inside

- **53 Skills** across 13 categories
- **23 Legal/Case-Management** skills (new in v1.0.1)
- **Core MCP Infrastructure** for dynamic skill loading
- **Rock-Hardened Release** with verified integrity
- **Comprehensive Documentation** for integration and development

## Installation

```bash
npm install fused-gaming-skills
```

## Usage

```typescript
import { SkillRegistry } from 'fused-gaming-skills';

const registry = new SkillRegistry();
const skill = await registry.loadSkill('your-skill-name');
console.log(skill?.tools);
```

## Project Structure

```
skills/
├── docs/                        # Documentation
│   ├── getting-started/        # Entry point and quickstart
│   ├── guides/                 # Integration and development guides
│   ├── reference/              # Reference documentation
│   ├── configuration/          # Configuration files
│   └── releases/               # Release notes
├── mcp-core/                   # Core MCP infrastructure (v1.0.40)
├── package.json                # Root workspace config
└── README.md                   # This file
```

## Key Features

- ✅ **Dynamic Skill Loading** - Load skills on demand with configuration
- ✅ **Type Safety** - Full TypeScript support throughout
- ✅ **Reproducible Builds** - Locked dependencies and verified integrity
- ✅ **Rock Hardened** - Deterministic and production-ready
- ✅ **Comprehensive Docs** - Complete guides and references
- ✅ **Legal Skills** - 23 case-management and legal tools
- ✅ **Non-Commercial** - Free for education and research

## Skills Overview

| Category | Count | Status |
|----------|-------|--------|
| Legal Services | 23 | ✅ |
| Case Management | 10 | ✅ |
| Workflow Management | 8 | ✅ |
| Data Management | 6 | ✅ |
| Other (9 categories) | 6 | ✅ |
| **Total** | **53** | **✅** |

## Development

### Prerequisites

- Node.js >= 18.0.0
- npm >= 8.0.0

### Setup

```bash
# Install dependencies
npm install

# Build all packages
npm run build

# Start development
npm run dev

# Run tests
npm run test
```

## Version Control

- **Repository**: Fused-Gaming/skills
- **Current Version**: 1.0.1
- **Status**: Stable
- **Last Updated**: 2026-09-30

See [CHANGELOG.md](./CHANGELOG.md) for version history.

## Configuration

Skills are configured via `.fused-gaming-mcp.json`:

```json
{
  "enabledSkills": ["skill-1", "skill-2"],
  "toolConfigurations": {
    "skill-1": { "option1": "value1" }
  }
}
```

See [Environment Setup](./docs/configuration/ENVIRONMENT.md) for details.

## Documentation

Complete documentation is organized in the `docs/` directory:

- **Getting Started**: [docs/getting-started/README.md](./docs/getting-started/README.md)
- **Integration**: [docs/guides/integration-guide.md](./docs/guides/integration-guide.md)
- **Development**: [docs/guides/development-guide.md](./docs/guides/development-guide.md)
- **Configuration**: [docs/configuration/ENVIRONMENT.md](./docs/configuration/ENVIRONMENT.md)
- **Reference**: [docs/reference/](./docs/reference/)
- **Releases**: [docs/releases/](./docs/releases/)

## License

**Fused Gaming Skills - Non-Commercial License v1.0**

- ✅ Free for: Individual use, education, research, academic institutions
- ❌ Not free for: Commercial use, revenue-generating services

See [LICENSE](./docs/reference/LICENSE) for complete terms.

Commercial licensing available: contact license@vln.gg

## Related Repositories

- [Fused-Gaming/agents](https://github.com/Fused-Gaming/agents) - Agent marketplace (v1.0.1)
- [Fused-Gaming/tools](https://github.com/Fused-Gaming/tools) - Tools marketplace (v1.0.0)

## Support

- 📖 See [Getting Started](./docs/getting-started/README.md) for quickstart
- 🔧 Check [Integration Guide](./docs/guides/integration-guide.md) for usage
- 👨‍💻 Review [Development Guide](./docs/guides/development-guide.md) for creating skills
- ⚙️ See [Environment Setup](./docs/configuration/ENVIRONMENT.md) for installation help

## Changelog

Latest updates in v1.0.1:
- Added 23 legal/case-management skills
- Reorganized documentation structure
- Enhanced configuration documentation
- Improved development guides

See [CHANGELOG.md](./CHANGELOG.md) for full history.

---

**Fused Gaming Skills Marketplace v1.0.1**  
Rock-hardened, production-ready, and fully documented.  
Copyright © 2026 Fused Gaming Inc.

