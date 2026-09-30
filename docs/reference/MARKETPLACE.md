<!-- Version Control
- Version: 1.0.1
- Last Updated: 2026-09-30
- Status: active
- Repository: Fused-Gaming/skills
-->

# Fused Gaming Skills Marketplace

A centralized catalog and registry for all skills available in the Fused Gaming ecosystem.

## Overview

The Skills Marketplace is a JSON-based registry that catalogs all available skills across the Fused Gaming organization. This enables:

- **Discovery**: Find skills by name, category, or capability
- **Documentation**: Complete metadata for each skill
- **Versioning**: Track skill versions and updates
- **Dependencies**: Understand skill requirements and relationships
- **Integration**: Easy access to skill information for tools and dashboards

## Registry Structure

### Main Registry File: `marketplace-registry.json`

```json
{
  "registry": {
    "version": "1.0.0",
    "name": "Fused Gaming Skills Marketplace",
    "description": "Central catalog of all available skills",
    "lastUpdated": "ISO-8601 timestamp",
    "skills": [
      {
        "id": "unique-skill-id",
        "name": "Skill Display Name",
        "version": "1.0.0",
        "description": "Brief description of what the skill does",
        "category": "content-generation",
        "repository": {
          "owner": "Fused-Gaming",
          "repo": "repository-name",
          "url": "https://github.com/Fused-Gaming/repository-name",
          "branch": "main",
          "path": "path/to/skill"
        },
        "capabilities": [
          "capability-1",
          "capability-2"
        ],
        "tools": [
          {
            "name": "tool-name",
            "description": "What this tool does",
            "inputSchema": {
              "type": "object",
              "properties": {}
            }
          }
        ],
        "configuration": {
          "configFile": ".fused-gaming-mcp.json or similar",
          "environmentVariables": [],
          "requiredSettings": []
        },
        "dependencies": {
          "required": ["@h4shed/mcp-core"],
          "optional": []
        },
        "author": "author-name",
        "license": "Apache-2.0",
        "tags": ["tag1", "tag2"],
        "status": "active|deprecated|beta",
        "lastModified": "ISO-8601 timestamp"
      }
    ]
  },
  "categories": [
    "content-generation",
    "data-analysis",
    "development-tools",
    "gaming",
    "security",
    "web3",
    "infrastructure",
    "ai-augmentation",
    "automation",
    "other"
  ],
  "skillIndex": {
    "by-id": {},
    "by-category": {},
    "by-tag": {},
    "by-repository": {}
  }
}
```

## Skill Schema Reference

### Required Fields

- **id**: Unique identifier (kebab-case, lowercase)
- **name**: Display name
- **version**: Semantic version (MAJOR.MINOR.PATCH)
- **description**: Brief description (1-2 sentences)
- **category**: One of the predefined categories
- **repository**: GitHub repository information
- **status**: One of: active, beta, deprecated

### Optional Fields

- **capabilities**: Array of high-level capabilities
- **tools**: Array of MCP tool definitions
- **configuration**: Configuration requirements
- **dependencies**: Required and optional dependencies
- **author**: Skill author/maintainer
- **license**: Open source license
- **tags**: Searchable tags
- **documentation**: Links to documentation
- **examples**: Example usage code

## Categories

- **content-generation**: Skills for generating content (text, code, etc.)
- **data-analysis**: Skills for analyzing and processing data
- **development-tools**: Developer utilities and tools
- **gaming**: Gaming-related skills
- **security**: Security and compliance tools
- **web3**: Blockchain and Web3 tools
- **infrastructure**: Infrastructure and DevOps tools
- **ai-augmentation**: AI-powered augmentation tools
- **automation**: Automation and workflow tools
- **other**: Miscellaneous skills

## Adding Skills to the Marketplace

1. Identify the skill in a Fused Gaming repository
2. Extract metadata (name, description, capabilities, etc.)
3. Add an entry to `marketplace-registry.json`
4. Update the skill index
5. Document the skill in this file
6. Commit changes to the skills repository

### Metadata Extraction Checklist

- [ ] Skill name and ID
- [ ] Version number
- [ ] Description of purpose
- [ ] Category classification
- [ ] Repository path and URL
- [ ] List of capabilities/features
- [ ] Tool definitions (if applicable)
- [ ] Configuration requirements
- [ ] Dependencies
- [ ] Author/maintainer
- [ ] License information
- [ ] Relevant tags

## Querying the Marketplace

### By Category

```javascript
const skills = registry.skillIndex["by-category"]["content-generation"];
```

### By Tag

```javascript
const skills = registry.skillIndex["by-tag"]["web3"];
```

### By Repository

```javascript
const skills = registry.skillIndex["by-repository"]["Fused-Gaming/underworld-writer"];
```

## Skill Status

- **active**: Actively maintained and production-ready
- **beta**: Under active development, may change
- **deprecated**: No longer recommended for new use

## Maintenance

The marketplace registry should be updated whenever:

- A new skill is created or discovered
- A skill is updated or released
- A skill is deprecated or removed
- Skill metadata changes
- Dependencies are updated

## Related Documentation

- See `mcp-core/README.md` for core MCP infrastructure
- See individual skill repositories for detailed documentation
- See `SKILL_DEVELOPMENT.md` for guidelines on creating new skills
