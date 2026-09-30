<!-- Version Control
- Version: 1.0.1
- Last Updated: 2026-09-30
- Status: active
- Repository: Fused-Gaming/skills
-->

# Fused Gaming Skills - Agent Development Guide

## Overview

This guide provides instructions for agents, AI assistants, and developers working with the Fused Gaming Skills repository. It outlines best practices, conventions, and workflows specific to this codebase.

## Repository Structure

```
skills/
├── docs/                     # Organized documentation (see hierarchy below)
├── mcp-core/                 # Core MCP server infrastructure
├── marketplace-registry.json # Skills registry and metadata
├── package.json              # Root workspace configuration
├── VERSION.json              # Version metadata
├── CHANGELOG.md              # Version history
├── README.md                 # Entry point
├── SKILL.md                  # This file
├── CLAUDE.md                 # Claude-specific configuration
└── AGENTS.md                 # Agent guidelines
```

## Documentation Hierarchy

### Quick Access by Purpose

**For Getting Started:**
- Start: [README.md](./README.md) - Entry point overview
- Guide: [docs/getting-started/README.md](./docs/getting-started/README.md) - Getting started tutorial

**For Integration:**
- [docs/guides/integration-guide.md](./docs/guides/integration-guide.md) - How to use skills

**For Development:**
- [docs/guides/development-guide.md](./docs/guides/development-guide.md) - Creating new skills
- [docs/configuration/ENVIRONMENT.md](./docs/configuration/ENVIRONMENT.md) - Setup instructions

**For Reference:**
- [docs/reference/MARKETPLACE.md](./docs/reference/MARKETPLACE.md) - Marketplace specs
- [docs/reference/SKILLS_CATALOG.md](./docs/reference/SKILLS_CATALOG.md) - Skill inventory
- [docs/reference/LICENSE](./docs/reference/LICENSE) - License terms

**For Configuration:**
- [docs/configuration/MANIFEST.md](./docs/configuration/MANIFEST.md) - Rock-hardened manifest
- [docs/configuration/VERSION.json](./docs/configuration/VERSION.json) - Version metadata

**For Releases:**
- [docs/releases/RELEASE_v1.0.1.md](./docs/releases/RELEASE_v1.0.1.md) - Current release
- [CHANGELOG.md](./CHANGELOG.md) - Full version history

## Agent Workflows

### Recommended Approach for Agents

When working with this repository, follow this order:

1. **Read README.md** - Get oriented
2. **Check CLAUDE.md** - Understand Claude-specific setup
3. **Review AGENTS.md** - Learn agent guidelines
4. **Use docs/getting-started/** - Follow quickstart
5. **Apply docs/guides/** - Follow relevant guide

### Common Agent Tasks

#### Task: Add a New Skill

**Process:**
1. Review [docs/guides/development-guide.md](./docs/guides/development-guide.md)
2. Create skill in workspace
3. Implement Skill interface
4. Add to marketplace-registry.json
5. Create PR with clear description
6. Ensure all tests pass
7. Update CHANGELOG.md

**Files to Modify:**
- `marketplace-registry.json` - Register skill
- `package.json` (workspace) - Add workspace entry
- `VERSION.json` - Update metadata

#### Task: Update Documentation

**Process:**
1. Locate file in `docs/` hierarchy
2. Update content with version header
3. Ensure cross-references work
4. Update CHANGELOG.md
5. Create PR with documentation-focused title

**Version Header Format:**
```html
<!-- Version Control
- Version: 1.0.1
- Last Updated: YYYY-MM-DD
- Status: active|draft|deprecated
- Repository: Fused-Gaming/skills
-->
```

#### Task: Create a Release

**Process:**
1. Update VERSION.json with new version
2. Update package.json version
3. Create docs/releases/RELEASE_vX.X.X.md
4. Update CHANGELOG.md with changes
5. Create PR targeting main
6. Tag release after merge: `git tag -a vX.X.X -m "Release vX.X.X"`

#### Task: Fix an Issue

**Process:**
1. Create feature branch: `git checkout -b fix/issue-description`
2. Make minimal changes (bug fixes only)
3. Add test cases if applicable
4. Create PR with clear description
5. Ensure CI passes before merge

## Conventions

### Commit Messages

**Format:**
```
[Type] Brief description

Detailed explanation if needed

Affected Files:
- path/to/file1
- path/to/file2
```

**Types:**
- `[feat]` - New skill or feature
- `[fix]` - Bug fix
- `[docs]` - Documentation only
- `[refactor]` - Code reorganization
- `[test]` - Test additions
- `[chore]` - Maintenance tasks

**Example:**
```
[feat] Add anti-SLAPP defense skill

Implemented comprehensive skill for anti-SLAPP screening and defense procedures.
Includes intake workflow and evidence preservation tools.

Affected Files:
- marketplace-registry.json
- docs/reference/SKILLS_CATALOG.md
- CHANGELOG.md
```

### Branch Naming

**Format:** `{type}/{descriptor}`

**Types:**
- `feature/` - New skills or features
- `fix/` - Bug fixes
- `docs/` - Documentation updates
- `refactor/` - Code reorganization
- `claude/` - Claude-specific work (e.g., `claude/documentation-reorganization`)

**Examples:**
- `feature/new-skill-anti-slapp`
- `fix/skill-registry-error`
- `docs/update-integration-guide`
- `claude/documentation-structure-reorganization-skills`

### Pull Request Process

1. **Title**: Clear, descriptive (max 72 chars)
2. **Description**: Use template from repository
3. **Files Changed**: Keep focused on single concern
4. **Tests**: Ensure all pass locally
5. **Documentation**: Update affected docs
6. **Ready for Review**: Never open as draft unless noted

## Testing

### Local Testing

```bash
# Install dependencies
npm install

# Build all packages
npm run build

# Run tests
npm run test

# Check version sync
npm run version:sync
```

### Before Creating PR

1. Run `npm run build` - No compilation errors
2. Run `npm run test` - All tests pass
3. Check `npm run version:sync` - Versions match
4. Review git diff - Changes are minimal and focused
5. Validate documentation - Links work, headers present

## Version Management

### Semantic Versioning

- **Major (X.0.0)**: Breaking changes
- **Minor (1.X.0)**: New features, backward compatible
- **Patch (1.0.X)**: Bug fixes only

### Current Version: 1.0.1

### Files to Update for Version Changes

1. `package.json` - version field
2. `VERSION.json` - version and metadata
3. `CHANGELOG.md` - new entry with changes
4. `docs/releases/RELEASE_vX.X.X.md` - release notes

## Cross-Repository Coordination

This repository is part of Fused Gaming ecosystem:

- **Fused-Gaming/agents** (v1.0.1) - Agent marketplace
- **Fused-Gaming/tools** (v1.0.0) - Tools marketplace
- **Fused-Gaming/skills** (v1.0.1) - Skills marketplace (this repo)

### Consistency Requirements

- Similar documentation structure
- Compatible version numbering
- Cross-repository references maintained
- Dependencies tracked in VERSION.json

## Agent-Specific Guidelines

### When Making Changes

1. **Always read CLAUDE.md first** - Claude-specific setup
2. **Always read AGENTS.md second** - Agent-specific guidelines
3. **Follow conventions above** - Commit messages, branches, PRs
4. **Test locally before pushing** - No broken builds
5. **Keep changes minimal and focused** - One concern per PR
6. **Update documentation** - Changes need docs updates
7. **Update CHANGELOG.md** - All user-facing changes logged

### What NOT to Do

- ❌ Don't push directly to main
- ❌ Don't skip tests or CI checks
- ❌ Don't add files without version headers
- ❌ Don't update version files manually
- ❌ Don't force-push to shared branches
- ❌ Don't merge your own PRs without review
- ❌ Don't make unrelated changes in same PR

### Proactive Agent Actions

Agents should proactively:

1. **Maintain CI/CD** - Fix failing tests immediately
2. **Keep docs current** - Update when code changes
3. **Monitor dependencies** - Check for updates
4. **Organize structure** - Follow established patterns
5. **Review documentation** - Ensure accuracy
6. **Validate cross-references** - Check internal links

## Performance & Optimization

### Build Performance

```bash
# Watch mode for development
npm run dev

# Clean build for CI
npm run clean && npm run build

# Run specific workspace
npm run test --workspace=mcp-core
```

### Optimization Tips

1. Use `npm ci` instead of `npm install` in CI
2. Cache dependencies in CI pipelines
3. Run tests in parallel when possible
4. Keep workspace dependencies lean
5. Monitor bundle size trends

## Security

### Security Checklist

- ✅ Dependencies locked in package-lock.json
- ✅ No hardcoded secrets in code
- ✅ License compliance verified
- ✅ Version integrity tracked
- ✅ Non-commercial license enforced

### Before Pushing

Review for:
- No API keys or tokens
- No internal hostnames
- No sensitive data
- No security bypasses

## Support & Escalation

### Issues & Questions

1. Check relevant `docs/` file
2. Review CLAUDE.md for Claude-specific issues
3. Check AGENTS.md for agent-specific guidelines
4. Consult CHANGELOG.md for version info
5. Review previous PRs for similar patterns

### When to Ask for Help

- Architectural decisions
- Breaking changes
- Cross-repository impacts
- Design-level feedback
- Ambiguous requirements

## Summary for Agents

**Start here:**
1. Read this file (SKILL.md)
2. Read CLAUDE.md for Claude setup
3. Read AGENTS.md for agent guidelines
4. Check docs/getting-started/README.md
5. Follow appropriate guide in docs/guides/

**Before any change:**
- Is this in scope?
- Does it follow conventions?
- Are docs updated?
- Do tests pass?
- Is CHANGELOG updated?

**For specific tasks:**
- New skill → docs/guides/development-guide.md
- Integration help → docs/guides/integration-guide.md
- Setup issues → docs/configuration/ENVIRONMENT.md
- Version info → docs/configuration/VERSION.json

---

**Last Updated**: 2026-09-30  
**Current Version**: 1.0.1  
**Repository**: https://github.com/Fused-Gaming/skills  
**License**: Apache-2.0 + Non-Commercial v1.0

