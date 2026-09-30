<!-- Version Control
- Version: 1.0.1
- Last Updated: 2026-09-30
- Status: active
- Repository: Fused-Gaming/skills
-->

# Fused Gaming Skills - Repository Manifest v1.0.1

**Release Date**: 2026-09-30  
**Status**: STABLE  
**Revision**: main (as of 2026-09-30)  

## Repository Information

- **Repository**: Fused-Gaming/skills
- **Type**: Skills Marketplace + Development Workspace
- **Version**: 1.0.1
- **License**: Apache-2.0 + Non-Commercial
- **Copyright**: Fused Gaming Inc.
- **Package**: `@h4shed/mcp-core` (npm - production)

## Contents

| Item | Count | Notes |
|------|-------|-------|
| Skills | 53 | Cataloged in marketplace-registry.json |
| Categories | 13 | Organized by function |
| Legal Skills | 23 | Case-management and legal procedures |
| MCP Core | v1.0.40 | Core infrastructure (mcp-core workspace) |
| Documentation Files | 10+ | Organized in docs/ directory |
| Configuration Files | 4 | Root-level + docs/configuration/ |
| Guide Files | 3 | SKILL.md, CLAUDE.md, AGENTS.md |

## Repository Structure

```
skills/
├── docs/                           # Organized documentation (v1.0.1)
│   ├── getting-started/           # Entry point and quickstart
│   │   └── README.md
│   ├── guides/                    # Development and integration guides
│   │   ├── integration-guide.md
│   │   └── development-guide.md
│   ├── reference/                 # Reference materials
│   │   ├── MARKETPLACE.md         # Marketplace specs
│   │   ├── SKILLS_CATALOG.md      # Skill inventory
│   │   └── LICENSE                # License terms
│   ├── configuration/             # Configuration and metadata
│   │   ├── MANIFEST.md            # This file
│   │   ├── VERSION.json           # Version metadata
│   │   └── ENVIRONMENT.md         # Environment setup
│   └── releases/                  # Release information
│       └── RELEASE_v1.0.1.md      # Current release notes
├── mcp-core/                      # Core MCP server (v1.0.40)
│   ├── src/                       # TypeScript source
│   ├── package.json               # Workspace config
│   └── tsconfig.json              # TypeScript config
├── marketplace-registry.json      # Skills registry (53 skills)
├── package.json                   # Root workspace (private)
├── package-lock.json              # Locked dependencies
├── VERSION.json                   # Version metadata
├── CHANGELOG.md                   # Version history
├── README.md                       # Root entry point
├── SKILL.md                       # Agent development guide
├── CLAUDE.md                      # Claude AI configuration
├── AGENTS.md                      # Agent autonomy guidelines
└── LICENSE                        # License file

## Dependency Matrix

### Root Package (private workspace)
- `@modelcontextprotocol/sdk: ^1.29.0`
- `express: ^4.18.2`
- Development tools as needed

**Note**: Root package is marked `private: true` for workspace use only.

### MCP Core Package (@h4shed/mcp-core)
- Packaged for npm publication
- Exports: SkillRegistry, Skill interface, Tool types
- Targets Node.js 18+

### External Dependencies

| Repository | Version | Type | Status |
|-----------|---------|------|--------|
| Fused-Gaming/tools | 1.0.0 | Optional | Pinned |
| Fused-Gaming/agents | 1.0.1 | Optional | Pinned |

## Version Information

**Current Version**: 1.0.1  
**Semantic Versioning**: MAJOR.MINOR.PATCH

### Version Files
- `package.json` - `version: "1.0.1"`
- `VERSION.json` - `version: "1.0.1"`
- File headers - All docs marked `Version: 1.0.1`

**Sync Status**: Manual verification required (no CI validation yet)

## Documentation Organization

### By Purpose

**For Getting Started**
- Entry: `README.md` (minimal entry point)
- Getting Started: `docs/getting-started/README.md`

**For Usage**
- Integration: `docs/guides/integration-guide.md`
- Skills List: `docs/reference/SKILLS_CATALOG.md`
- Marketplace: `docs/reference/MARKETPLACE.md`

**For Development**
- Development Guide: `docs/guides/development-guide.md`
- Repository Conventions: `SKILL.md`
- Agent Guidelines: `AGENTS.md`
- Claude Guide: `CLAUDE.md`

**For Configuration**
- Environment Setup: `docs/configuration/ENVIRONMENT.md`
- Version Metadata: `docs/configuration/VERSION.json`
- Manifest: `docs/configuration/MANIFEST.md` (this file)

**For Release Info**
- Current Release: `docs/releases/RELEASE_v1.0.1.md`
- Version History: `CHANGELOG.md`

## Quality Assurance Status

### Locked Dependencies
- ✅ `package-lock.json` present
- ✅ All major versions pinned
- ✅ Reproducible install: `npm ci`

### Documentation
- ✅ Organized in logical categories
- ✅ Version control headers present
- ✅ Cross-references maintained
- ⚠️ Needs CI validation for links

### Testing & Verification
- ⚠️ Test framework setup pending
- ⚠️ CI/CD workflow needed for automated verification
- ⚠️ Integrity checksums are manual labels

### Known Limitations (v1.0.1)

1. **Testing**: mcp-core has placeholder tests
2. **CI/CD**: No automated verification workflow
3. **Linting**: No root-level linting configured
4. **TypeScript**: Configuration only in mcp-core workspace
5. **Verification Claims**: Manual vs. machine-verified distinction not yet clear

## Integrity & Verification

### What's Verified
- ✅ Dependency lock: `package-lock.json`
- ✅ Version consistency: Manual (check VERSION.json vs package.json)
- ✅ Documentation structure: Manual review
- ✅ License compliance: Manual verification

### What's NOT Yet Verified by CI
- ❌ Automated build verification
- ❌ Automated test verification
- ❌ Link validity checking
- ❌ Cross-reference validation
- ❌ Security scanning

### Future Improvements

CI/CD should add:
1. Build verification on PRs
2. Test execution
3. Documentation link checking
4. TypeScript type checking (at workspace level)
5. Security audits
6. Version consistency validation

## File Statistics

| Category | Count | Notes |
|----------|-------|-------|
| Markdown docs | 10+ | In docs/ + root |
| JSON config | 4 | package.json, package-lock.json, VERSION.json, marketplace-registry.json |
| TypeScript | TBD | In mcp-core/src/ |
| Guide files | 3 | SKILL.md, CLAUDE.md, AGENTS.md |

## Deployment Checklist

**For Development/Testing:**
```bash
npm install              # Install dependencies
npm run build           # Build all workspaces
npm run test            # Run available tests
npm run version:sync    # Check version consistency
```

**For Production (mcp-core):**
- Install `@h4shed/mcp-core` from npm
- Verify version matches intention
- Check security audit: `npm audit`

## Support & Maintenance

**This Manifest Document**
- Location: `docs/configuration/MANIFEST.md`
- Purpose: Track repository structure and state
- Update: When major structure changes occur
- Verification: Manual (until CI added)

**Related Documents**
- `CHANGELOG.md` - Version history and changes
- `VERSION.json` - Authoritative version metadata
- `SKILL.md` - Repository conventions
- `AGENTS.md` - Agent guidelines
- `CLAUDE.md` - Claude AI guidance

## Notes for Contributors

1. **When adding files**: Update this manifest if structure changes
2. **When releasing**: Update VERSION.json, package.json, CHANGELOG.md
3. **When documenting**: Use docs/ hierarchy and add version headers
4. **When creating PRs**: Reference related docs in description
5. **When verifying state**: Check documentation hasn't drifted

## Future Roadmap

**For v1.0.2+:**
- Add comprehensive test suite
- Set up CI/CD workflows
- Add automated verification
- Link checking in CI
- TypeScript configuration at root level

**For v1.1.0:**
- Enhanced skill composition
- Performance monitoring
- Extended marketplace categories
- Advanced documentation generation

---

**Last Updated**: 2026-09-30  
**Revision**: v1.0.1 (2026-09-30)  
**Authority**: Manual (no CI validation yet)  
**Status**: Active - Documentation Reorganization Complete

**Note**: This manifest describes current repository state as of v1.0.1. Integrity verification is manual at this stage. Future versions will add CI/CD validation.

