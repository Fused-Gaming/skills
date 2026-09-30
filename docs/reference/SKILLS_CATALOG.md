<!-- Version Control
- Version: 1.0.1
- Last Updated: 2026-09-30
- Status: active
- Repository: Fused-Gaming/skills
-->

# Fused Gaming Skills Catalog

Complete inventory of all 53 skills available in the Fused Gaming ecosystem, organized by category and with full metadata for discovery and integration.

## Quick Summary

- **Total Skills**: 30
- **Active Status**: 100%
- **Source Repository**: Fused-Gaming/Fused-Gaming-Skill-MCP
- **Last Updated**: 2026-09-30

## Skills by Category

### Design (8 skills)
- **Agentic Flow DevKit** - Design and visualize agentic orchestration flows
- **ASCII Mockup** - Mobile-first ASCII wireframe mockup generator
- **Canvas Design** - Visual design generation for web with SVG
- **Frontend Design** - Frontend component design and HTML/CSS generation
- **Storybook Component Library** - Component library documentation and visual testing
- **Style Dictionary System** - Design tokens and style dictionary generation
- **SVG Generator** - Generate SVG assets and icon concepts
- **Tailwind CSS Style Builder** - Utility-first styling and design system builder
- **Theme Factory** - Design system and theme generation

### Development (4 skills)
- **Playwright Test Automation** - End-to-end testing automation framework
- **Pre-Deploy Validator** - Pre-deployment validation and quality checks
- **Smart Contract Tools** - Smart contract development for Hardhat/Truffle/Foundry
- **TypeScript Toolchain** - Advanced TypeScript configuration and type generation
- **Vite Module Bundler** - Next-generation JavaScript module bundler

### Generative Art (3 skills)
- **Algorithmic Art** - Generative art using p5.js with flow fields and particles
- **NFT Generative Art** - NFT artwork generation and blockchain-ready assets
- **Theme Factory** - Design system and theme generation

### Content Creation (2 skills)
- **LinkedIn Master Journalist** - Draft polished LinkedIn posts and thought-leadership content
- **Underworld Writer** - Dual-methodology for fictional narratives and true crime writing

### Project Management (3 skills)
- **Project Manager** - Plan projects with milestones and dependencies
- **Project Manager Skill** - Task and project management for team collaboration
- **Project Status Tool** - Summarize project status, risks, and next actions

### MCP Tools (2 skills)
- **Skill Creator** - Create custom skills and tools for the MCP ecosystem
- **MCP Builder** - Build and scaffold MCP servers and skills

### Infrastructure (2 skills)
- **SyncPulse Hub** - Centralized orchestration and installation of @h4shed packages
- **Vercel Next.js Deployment** - Vercel deployment optimization for serverless apps

### Automation (1 skill)
- **SyncPulse** - Project state caching, multi-agent coordination, email automation with 9 workflows

### Productivity (1 skill)
- **Daily Review** - Productivity tracking and session aggregation with metrics analysis

### Visualization (1 skill)
- **Mermaid Terminal** - Generate terminal-friendly Mermaid diagrams and flowcharts

### Session Management (1 skill)
- **Multi-Account Session Tracking** - Track Claude sessions across multiple accounts

### User Experience (1 skill)
- **UX Journey Mapper** - Create UX journey maps with pain points and opportunities

## Key Capabilities by Domain

### Design & Visual
- SVG and canvas rendering
- Component design and generation
- Design system management
- Wireframing and prototyping
- Theme and style generation

### Development & DevOps
- Smart contract development
- TypeScript configuration
- E2E testing automation
- Module bundling
- Pre-deployment validation
- Vercel/Next.js deployment

### Content & Creativity
- LinkedIn content generation
- Creative writing (fiction & true crime)
- Generative art creation
- Mermaid diagram generation

### Project & Process
- Project planning and tracking
- Task management
- Status reporting and dashboards
- Daily productivity reviews
- Multi-account session tracking

### Infrastructure & Automation
- Email automation workflows
- Project state caching
- Multi-agent coordination
- Centralized package management

## Accessing the Registry

### JSON Format
- **File**: `marketplace-registry.json`
- **Type**: Complete metadata for all 30 skills
- **Usage**: Query by category, tag, repository, or capability

### Querying Examples

#### All Design Skills
```json
registry.skills.filter(s => s.category === "design")
```

#### Skills with Specific Capability
```json
registry.skills.filter(s => s.capabilities.includes("deployment-optimization"))
```

#### Skills by Repository
```json
registry.skills.filter(s => s.repository.repo === "Fused-Gaming-Skill-MCP")
```

## Skill Metadata Structure

Each skill entry includes:
- **id**: Unique identifier
- **name**: Display name
- **version**: Semantic version
- **description**: Purpose and capabilities
- **category**: Classification
- **package**: NPM package name
- **status**: active/beta/deprecated
- **capabilities**: Feature list
- **tools**: Available MCP tools
- **repository**: GitHub location
- **tags**: Searchable keywords
- **author**: Maintainer
- **license**: Apache-2.0

## Integration Guide

### 1. Discovering Skills
Browse `marketplace-registry.json` for available skills matching your needs.

### 2. Getting Metadata
Access complete skill information including version, capabilities, and tools.

### 3. Installing Skills
Most skills are available as npm packages: `@h4shed/skill-{name}`

### 4. Using Skills
Skills are integrated via the MCP ecosystem and provide tools for various tasks.

## Maintenance

This catalog is maintained in the skills repository and should be updated when:
- New skills are created
- Existing skills release new versions
- Skills are deprecated or archived
- Metadata requires updates

## Related Resources

- **Marketplace Registration**: See `MARKETPLACE.md` for registry specifications
- **MCP Core**: See `mcp-core/README.md` for core infrastructure
- **Original Source**: https://github.com/Fused-Gaming/Fused-Gaming-Skill-MCP

## Statistics

### By Category
- Design: 8 skills (27%)
- Development: 5 skills (17%)
- Project Management: 3 skills (10%)
- Generative Art: 3 skills (10%)
- Content Creation: 2 skills (7%)
- MCP Tools: 2 skills (7%)
- Infrastructure: 2 skills (7%)
- Other: 4 skills (13%)

### By Status
- Active: 30 skills (100%)
- Beta: 0 skills
- Deprecated: 0 skills

## Search & Filtering

Use the marketplace registry to search by:
- **Category**: design, development, automation, etc.
- **Capability**: svg-generation, testing, deployment, etc.
- **Tags**: mcp, skill, blockchain, css, etc.
- **Repository**: Fused-Gaming-Skill-MCP, syncpulse, underworld-writer
- **Package**: @h4shed/skill-* naming pattern
