<!-- Version Control
- Version: 1.0.1
- Last Updated: 2026-09-30
- Status: active
- Repository: Fused-Gaming/skills
-->

# Changelog

All notable changes to Fused Gaming Skills are documented in this file.

## [1.0.1] - 2026-09-30

### Added
- 23 new legal/case-management skills
- New Legal Services skill category
- Enhanced VERSION.json with extended metadata
- Rock-hardened release certification
- Documentation reorganization with structured docs/ directory
- Integration guide for skill usage
- Development guide for creating custom skills
- Environment setup documentation
- Cross-repository dependency tracking

### Changed
- Skills marketplace expanded from 30 to 53 total skills (+77%)
- Updated MANIFEST.md with rock-hardening verification
- Enhanced marketplace-registry.json with legal skills metadata
- Version control headers added to all documentation files
- Repository structure reorganized for better maintainability

### Security
- All dependencies locked in package-lock.json
- Reproducible builds verified
- Integrity checksums updated: sha256-SKILLS-v1.0.1
- Non-commercial license enforcement maintained

### Documentation
- Created structured docs/ directory tree
- docs/getting-started/ - Entry point and quickstart
- docs/guides/ - Integration and development guides
- docs/reference/ - Reference documentation
- docs/configuration/ - Configuration and manifest files
- docs/releases/ - Release notes and history

## [1.0.0] - 2026-06-15

### Initial Release
- Core MCP server infrastructure
- SkillRegistry for dynamic skill loading
- Initial 30 skills in marketplace
- 12 skill categories
- Package lock for reproducible builds
- Comprehensive documentation
- Apache-2.0 + Non-Commercial license

## Project Timeline

### 2026-09-30: Version 1.0.1
- Legal skills integration complete
- Documentation restructure complete
- Rock-hardened release published

### 2026-06-15: Version 1.0.0
- Initial marketplace launch
- Core infrastructure complete
- 30 skills available

## Version History

| Version | Release Date | Status | Skills | Categories | Notes |
|---------|--------------|--------|--------|------------|-------|
| 1.0.1 | 2026-09-30 | Stable | 53 | 13 | Legal skills added |
| 1.0.0 | 2026-06-15 | Stable | 30 | 12 | Initial release |

## Dependencies

### MCP Core
- Version: 1.0.40
- Status: Pinned and locked

### External Repositories
- **Fused-Gaming/tools** (v1.0.0) - Optional integration
- **Fused-Gaming/agents** (v1.0.1) - Optional integration

## Known Issues

None reported for v1.0.1.

## Deprecations

None at this time.

## Upgrade Guide

### From 1.0.0 to 1.0.1

1. **Update version in package.json**
   ```bash
   npm version minor
   ```

2. **Install new dependencies**
   ```bash
   npm install
   ```

3. **Load new legal skills**
   ```json
   {
     "enabledSkills": [
       "anti-slapp-screening",
       "asset-recovery",
       "attorney-approval"
     ]
   }
   ```

4. **Verify integrity**
   ```bash
   npm run test
   ```

## Security Advisories

No security advisories for version 1.0.1.

## Roadmap

### Planned for Future Releases
- Enhanced skill analytics and monitoring
- Advanced skill composition capabilities
- Extended MCP protocol support
- Performance optimizations
- Additional tool marketplace categories

## Support

For questions or issues:
- See [Environment Setup](./docs/configuration/ENVIRONMENT.md)
- Check [Integration Guide](./docs/guides/integration-guide.md)
- Review [Development Guide](./docs/guides/development-guide.md)
- Consult [Manifest](./docs/configuration/MANIFEST.md)

## License

Fused Gaming Skills - Non-Commercial License v1.0

See [LICENSE](./docs/reference/LICENSE) for complete terms.

---

**Last Updated**: 2026-09-30  
**Maintainer**: Fused Gaming Inc.  
**Repository**: https://github.com/Fused-Gaming/skills

