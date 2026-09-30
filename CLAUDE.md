<!-- Version Control
- Version: 1.0.1
- Last Updated: 2026-09-30
- Status: active
- Repository: Fused-Gaming/skills
-->

# Claude Configuration Guide - Fused Gaming Skills

## Overview

This file provides Claude-specific configuration, permissions, and guidelines for working with the Fused Gaming Skills repository. It enables Claude AI assistants to understand repository-specific requirements and work efficiently.

## Claude Environment Setup

### Repository Configuration

**Primary Directory:** `/home/user/skills`  
**Repository:** `Fused-Gaming/skills`  
**Current Branch:** `main` (development on feature branches)  
**Node Version:** >= 18.0.0  
**Package Manager:** npm with workspace support  

### Default Permissions

Claude should have permission for:
- ✅ Read all files
- ✅ Edit documentation
- ✅ Create/modify code files
- ✅ Run npm commands
- ✅ Run git commands (non-destructive)
- ✅ Create pull requests
- ✅ Add comments to PRs

Claude should NOT:
- ❌ Force-push to main
- ❌ Delete branches
- ❌ Merge PRs without review
- ❌ Modify security/license files without context
- ❌ Push secrets or credentials

## Working with Skills

### Understanding Skill Structure

A skill in Fused Gaming:
- Implements MCP (Model Context Protocol)
- Exports tools for Claude to use
- Has configuration via .fused-gaming-mcp.json
- Includes documentation and tests
- Is registered in marketplace-registry.json

### Skill Interface (TypeScript)

```typescript
interface Skill {
  name: string;           // Unique identifier
  version: string;        // Semantic version
  description: string;    // What it does
  category: string;       // Skill category
  tools: Tool[];         // Array of tools
  
  initialize(): Promise<void>;
  execute(toolName: string, input: any): Promise<any>;
  cleanup(): Promise<void>;
}

interface Tool {
  name: string;                    // Tool identifier
  description: string;             // Tool description
  inputSchema: JSONSchema;         // Input validation
  outputSchema?: JSONSchema;       // Output schema
}
```

### Key Files for Skills

- `marketplace-registry.json` - Registry of all skills
- `mcp-core/src/skill-registry.ts` - Skill loading logic
- `docs/reference/SKILLS_CATALOG.md` - Catalog of skills
- `docs/guides/development-guide.md` - Development instructions

## Claude-Specific Tasks

### Task: Analyze Skill Integration

**Steps:**
1. Read the skill's package.json for dependencies
2. Check marketplace-registry.json for metadata
3. Review skill's README for usage
4. Verify MCP tool schema is valid
5. Check for conflicts with existing tools

**Use These Tools:**
```bash
npm run build          # Compile skill
npm run test           # Test skill
npm run test:integration # Test integration
```

### Task: Create a New Skill

**Pre-requisites:**
1. Read docs/guides/development-guide.md
2. Review existing skills in marketplace-registry.json
3. Understand MCP protocol basics
4. Check skill naming conventions

**Process:**
1. Create workspace package
2. Implement Skill interface
3. Define tool schemas
4. Write tests (>80% coverage)
5. Add to marketplace-registry.json
6. Create comprehensive README
7. Create PR with documentation

**Key Checks:**
- ✅ No TypeScript errors
- ✅ All tests pass
- ✅ Tool schemas are valid
- ✅ Documentation is complete
- ✅ Version headers present
- ✅ CHANGELOG updated

### Task: Update Documentation

**Always:**
1. Preserve version control header
2. Update "Last Updated" date
3. Validate all links work
4. Check cross-references
5. Run `npm run version:sync` after changes
6. Update CHANGELOG.md

**Never:**
- ❌ Remove version control headers
- ❌ Break cross-references
- ❌ Use outdated examples
- ❌ Change file structures without planning

### Task: Fix Skills or Tests

**Diagnosis First:**
1. Reproduce the issue locally
2. Check error messages carefully
3. Review related test files
4. Look at git history for context
5. Check VERSION.json for compatibility

**Minimal Fix Approach:**
- Make smallest possible change
- Fix root cause, not symptoms
- Add regression test
- Update documentation
- Create focused PR

## MCP Protocol Guidelines

### Tool Schema Requirements

Every tool must have:

```json
{
  "name": "tool-name",
  "description": "What this tool does",
  "inputSchema": {
    "type": "object",
    "properties": {
      "param1": { "type": "string", "description": "..." },
      "param2": { "type": "number", "description": "..." }
    },
    "required": ["param1"]
  }
}
```

### Schema Validation

Before submitting:
1. Test schema with sample inputs
2. Ensure all required fields are listed
3. Provide meaningful descriptions
4. Handle edge cases in validation

## NPM Scripts for Claude

### Useful Commands

```bash
# Build and validate
npm run build              # Build all workspaces
npm run test               # Run all tests
npm run clean              # Clean build artifacts

# Development
npm run dev                # Watch mode

# Documentation
npm run docs:build         # Build docs
npm run version:check      # Show current version
npm run version:sync       # Verify version consistency
npm run manifest:update    # Update manifest

# Workspace-specific
npm run build --workspace=mcp-core
npm run test --workspace=mcp-core
```

## Handling Dependencies

### Adding Dependencies

**When to add:**
- Required functionality not available
- Established, well-maintained package
- Minimal security concerns

**When NOT to add:**
- Duplicate functionality
- Large dependency trees
- Unmaintained packages
- Security vulnerabilities

**Process:**
1. Add to package.json
2. Run `npm install`
3. Update package-lock.json
4. Test thoroughly
5. Document in CHANGELOG.md

### Updating Dependencies

```bash
# Check outdated packages
npm outdated

# Update specific package
npm update package-name

# Update all packages
npm update

# Rebuild with new versions
npm run clean && npm run build
```

## Version Management for Claude

### Understanding Versioning

- **Current:** 1.0.1
- **Format:** MAJOR.MINOR.PATCH
- **Rules:** Semantic Versioning 2.0.0

### When to Bump Version

| Change | Version | Files to Update |
|--------|---------|-----------------|
| Bug fix | 1.0.X+1 | package.json, VERSION.json, CHANGELOG.md |
| New feature | 1.X+1.0 | package.json, VERSION.json, CHANGELOG.md |
| Breaking change | X+1.0.0 | package.json, VERSION.json, CHANGELOG.md |

### Version Sync Check

```bash
# Check version consistency
npm run version:sync

# Should show:
# Package: 1.0.1, VERSION.json: 1.0.1
```

## Git Workflow for Claude

### Branch Strategy

**Main branch:** `main` - Production, tagged releases  
**Development:** Feature branches from main  
**Pattern:** `{type}/{descriptor}`

**Examples:**
```
feature/new-skill-name
fix/skill-registry-error
docs/update-guide
claude/documentation-reorganization
```

### Commit Message Format

```
[type] Brief description

Detailed explanation

Affected Files:
- path/to/file1
- path/to/file2
```

### Pull Request Process

1. Push to feature branch
2. Create PR with title and description
3. Ensure CI passes
4. Address review comments
5. Rebase if needed (keep history clean)
6. Wait for approval before merge

## Testing Guidelines for Claude

### Test Requirements

Every code change should have:
- ✅ Unit tests (>80% coverage)
- ✅ Integration tests if applicable
- ✅ Type safety (TypeScript)
- ✅ Documentation updates

### Running Tests

```bash
# All tests
npm run test

# Specific workspace
npm run test --workspace=mcp-core

# Watch mode
npm run test -- --watch
```

### Test File Organization

```
skill-name/
├── src/
│   └── [implementation]
├── tests/
│   ├── unit/
│   │   └── skill.test.ts
│   └── integration/
│       └── integration.test.ts
└── jest.config.js
```

## Error Handling & Debugging

### Common Issues

**Issue: TypeScript Compilation Error**
```bash
# Solution:
npm run clean
npm run build
```

**Issue: Test Failures**
```bash
# Debug:
npm run test -- --verbose
npm run test -- --testNamePattern="test name"
```

**Issue: Version Mismatch**
```bash
# Check:
npm run version:sync
# Fix manually if needed
```

### Debugging Tips

1. Check error messages carefully
2. Look for file paths in errors
3. Review recent commits
4. Run `npm run build` for compilation issues
5. Check TypeScript errors: `npx tsc --noEmit`

## Repository Health Checks

### Regular Maintenance

Claude should periodically:

1. **Check Dependencies**
   ```bash
   npm outdated
   npm audit
   ```

2. **Verify Documentation**
   - All links work
   - Version headers present
   - Examples are current
   - Cross-references valid

3. **Validate Manifest**
   ```bash
   cat marketplace-registry.json | jq '.stats'
   ```

4. **Check Integrity**
   ```bash
   npm run version:sync
   npm run build
   npm run test
   ```

## Special Considerations

### Legal Skills Category

The repository includes 23 legal/case-management skills:
- Anti-SLAPP defense
- Asset recovery
- Attorney approval workflows
- California civil procedures
- Protective orders
- And more...

**When modifying legal skills:**
- Preserve legal accuracy
- Maintain attorney approval workflows
- Respect state-specific procedures
- Document compliance requirements
- Never remove legal safeguards

### Non-Commercial License

All skills are under Non-Commercial License v1.0:
- ✅ Free for education, research, personal use
- ❌ Not free for commercial services

**When adding content:**
- Ensure compliance with license
- Document any limitations
- Flag commercial restrictions
- Keep copyright notice current

## Claude Best Practices

### Before Starting Work

1. ✅ Read this file (CLAUDE.md)
2. ✅ Read SKILL.md for conventions
3. ✅ Read AGENTS.md for agent guidelines
4. ✅ Check docs/getting-started/README.md
5. ✅ Review CHANGELOG.md for recent changes

### During Development

1. ✅ Test locally: `npm run build && npm run test`
2. ✅ Validate types: `npm run build`
3. ✅ Check formatting and style
4. ✅ Update documentation
5. ✅ Add version control headers

### Before Creating PR

1. ✅ All tests pass
2. ✅ No TypeScript errors
3. ✅ Documentation updated
4. ✅ CHANGELOG.md updated
5. ✅ Version sync verified: `npm run version:sync`
6. ✅ Git diff reviewed for minimal changes

### PR Review Checklist

- [ ] Code follows conventions
- [ ] Tests pass locally
- [ ] Documentation complete
- [ ] CHANGELOG updated
- [ ] Version headers present
- [ ] Cross-references work
- [ ] No security issues
- [ ] No breaking changes (unless intended)

## Quick Reference

| Need | Location |
|------|----------|
| Getting started | docs/getting-started/README.md |
| Integration help | docs/guides/integration-guide.md |
| Create a skill | docs/guides/development-guide.md |
| Setup instructions | docs/configuration/ENVIRONMENT.md |
| Skills list | docs/reference/SKILLS_CATALOG.md |
| Conventions | SKILL.md (this repo) |
| Claude guide | CLAUDE.md (this file) |
| Agent guide | AGENTS.md (this repo) |
| Version history | CHANGELOG.md |
| Current version | VERSION.json |

## Support

**For Claude-specific issues:**
1. Check this file (CLAUDE.md)
2. Review SKILL.md for general guidelines
3. Check AGENTS.md for agent-specific help
4. Consult relevant docs/ file
5. Review git history for patterns

**For repository issues:**
1. Check CHANGELOG.md for known issues
2. Review recent PRs for solutions
3. Consult docs/configuration/ENVIRONMENT.md
4. Look at GitHub issues

---

**Last Updated**: 2026-09-30  
**Current Version**: 1.0.1  
**Repository**: https://github.com/Fused-Gaming/skills  
**License**: Apache-2.0 + Non-Commercial v1.0

**Claude Remember:**
1. Always run tests before pushing
2. Always update documentation
3. Always update CHANGELOG.md
4. Always use version headers
5. Always keep changes focused

