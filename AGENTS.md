<!-- Version Control
- Version: 1.0.1
- Last Updated: 2026-09-30
- Status: active
- Repository: Fused-Gaming/skills
-->

# Agent Guidelines - Fused Gaming Skills

## Overview

This document provides guidelines for autonomous agents working with the Fused Gaming Skills repository. It covers agent-specific workflows, autonomy levels, escalation points, and decision-making frameworks.

## Quick Start for Agents

### Essential Reading Order

1. **This file (AGENTS.md)** - Agent-specific guidelines
2. **SKILL.md** - Repository conventions and structure
3. **CLAUDE.md** - Claude AI assistant setup
4. **docs/getting-started/README.md** - Project overview
5. **Relevant guide in docs/guides/** - Task-specific help

### Agent Checklist Before Starting

- [ ] Repository cloned and dependencies installed
- [ ] Read this file (AGENTS.md)
- [ ] Read SKILL.md for conventions
- [ ] Understood permission levels
- [ ] Understood escalation points
- [ ] Reviewed recent CHANGELOG.md

## Autonomy Levels & Decision Making

### Level 1: No Autonomy (Always Ask First)

These decisions require human approval before proceeding:

- **Architecture Changes**: Restructuring core components
- **Version Bumps**: Major version changes (X.0.0)
- **Breaking Changes**: Changes that affect API contracts
- **Dependency Changes**: Adding/removing major dependencies
- **License Changes**: Modifying license terms
- **Security Policy**: Changes to security model
- **Scope Expansion**: Adding work beyond the defined task
- **Commercial Considerations**: License-related decisions

**When to Escalate:**
```
User, I need your decision on:
- [Specific decision]
- [Why it requires human judgment]
- [Options if applicable]
```

### Level 2: Ask if Ambiguous (Default)

For these decisions, ask if unclear, proceed if confident and small:

- **Feature Design**: New skill structure or capability
- **Documentation Changes**: Large documentation restructures
- **Testing Strategy**: Test organization or framework changes
- **Build Configuration**: Changes to build process
- **Optimization Approach**: Performance improvements
- **Code Organization**: Refactoring non-trivial code

**Decision Framework:**
1. Is the change small and local? → Proceed
2. Is it clearly in scope? → Proceed
3. Will it affect other systems? → Ask first
4. Is the benefit clear? → Ask if unsure
5. Could there be side effects? → Ask first

### Level 3: Full Autonomy (Proceed Directly)

Agents have full autonomy for:

- **Bug Fixes**: Fixing identified bugs
- **Documentation Updates**: Fixing docs, updating examples
- **Test Additions**: Adding test coverage
- **Code Formatting**: Style and consistency fixes
- **Version Headers**: Adding/updating version control headers
- **CHANGELOG Updates**: Documenting changes
- **Comments & Documentation**: Explaining code
- **Dependency Updates**: Patch version updates only
- **Minor Refactoring**: Improving code clarity locally

**Success Criteria for Autonomy:**
- Change is minimal and focused
- Tests pass locally
- Documentation updated
- CHANGELOG updated
- No breaking changes
- No new dependencies (major)

## Workflow Patterns

### Pattern 1: Creating a New Skill

**Autonomy Level:** Ask if architecture is unclear, proceed if following established pattern

**Steps:**
1. Read docs/guides/development-guide.md
2. Review existing skills in marketplace-registry.json
3. Create workspace package following pattern
4. Implement Skill interface
5. Write tests (comprehensive test framework setup is pending)
6. Add to marketplace-registry.json
7. Create comprehensive README
8. Create PR with clear description

**Success Criteria:**
- ✅ Tests pass: `npm run test`
- ✅ Builds: `npm run build`
- ✅ Follows MCP protocol
- ✅ Documentation complete
- ✅ marketplace-registry.json updated
- ✅ CHANGELOG.md updated

**When to Ask:**
- Unique skill architecture
- Novel tool patterns
- Cross-skill dependencies
- Performance implications

### Pattern 2: Fixing a Bug

**Autonomy Level:** Full autonomy (proceed directly)

**Steps:**
1. Reproduce bug locally
2. Write failing test case
3. Implement minimal fix
4. Verify test passes
5. Check no new errors introduced
6. Update CHANGELOG.md
7. Create focused PR with "fix:" prefix

**Success Criteria:**
- ✅ Reproducer exists
- ✅ Root cause identified
- ✅ Minimal fix applied
- ✅ Test added or updated
- ✅ No new issues introduced
- ✅ Documentation updated if needed

**When to Ask:**
- Root cause unclear
- Multiple potential fixes
- Affects other systems
- Requires architectural change

### Pattern 3: Documentation Update

**Autonomy Level:** Full autonomy (proceed directly)

**Steps:**
1. Identify documentation file
2. Preserve version control header
3. Update content
4. Validate all links work
5. Check cross-references
6. Update "Last Updated" date
7. Create PR with "docs:" prefix

**Success Criteria:**
- ✅ All links work
- ✅ Version header preserved
- ✅ Examples are current
- ✅ Cross-references valid
- ✅ Formatting consistent
- ✅ No broken navigation

**When to Ask:**
- Major reorganization
- Significant content expansion
- Architecture documentation
- New sections with wide impact

### Pattern 4: Dependency Management

**Autonomy Levels:**
- **Patch updates (1.0.x)**: Full autonomy
- **Minor updates (1.x.0)**: Ask if security or breaking
- **Major updates (x.0.0)**: Always ask first

**Steps:**
1. Check what changed: `npm outdated`
2. Test locally: `npm update && npm run build && npm run test`
3. Review breaking changes
4. Update package-lock.json
5. Create PR with detailed description
6. Update CHANGELOG.md

**Security**: Always update immediately if security issue, no autonomy level restriction

## Decision Frameworks

### "Should I Make This Change?" Framework

```
Question 1: Is this change in scope?
├─ NO  → Ask user if it should be
└─ YES → Continue

Question 2: Does it follow established patterns?
├─ NO  → Propose the approach, ask if unclear
└─ YES → Continue

Question 3: Is this change minimal and focused?
├─ NO  → Break into smaller changes, ask user
└─ YES → Continue

Question 4: Does it affect other systems?
├─ NO  → Continue
└─ YES → Ask user if impact is acceptable

Question 5: Will tests pass?
├─ UNSURE → Do not proceed, ask user
└─ YES   → Proceed with confidence

Result: PROCEED with PR creation
```

### "When to Escalate?" Framework

Escalate if ANY of these are true:

1. **Uncertainty**: "I'm not sure if this is right"
2. **Complexity**: "This is more complex than expected"
3. **Scope Creep**: "This is expanding beyond the original task"
4. **Impact**: "This could affect other features"
5. **Trade-offs**: "There are multiple valid approaches"
6. **Risk**: "This might break something"
7. **Time**: "This is taking longer than expected"
8. **Guidance Needed**: "I need direction on approach"

**Escalation Template:**
```
I've encountered a situation that needs your input:

**Situation:**
[Describe the issue]

**Options:**
1. [Option A] - [pros and cons]
2. [Option B] - [pros and cons]

**My Assessment:**
[What I think is best and why]

**Question for You:**
[Specific thing I need your decision on]
```

## Code Quality Standards

### Before Any PR

Verify these checks pass (repository currently supports):

```bash
# 1. Builds without errors
npm run build

# 2. All tests pass (note: mcp-core currently has placeholder tests)
npm run test

# 3. Version consistency
npm run version:sync

# 4. Security audit
npm audit
```

**Note**: The repository currently does not have:
- Root-level TypeScript configuration (only in mcp-core workspace)
- Linting/formatting scripts at root level
- Comprehensive test coverage (tests are placeholders)

These should be added as the project matures. For now, focus on:
- Documentation updates for any changes
- Consistency with existing patterns
- CHANGELOG.md updates
- Version header maintenance

### Pull Request Quality Checklist

- [ ] **Title**: Clear, descriptive, follows [type] format
- [ ] **Description**: Explains what and why, not just what
- [ ] **Changes**: Minimal and focused on single concern
- [ ] **Tests**: Test additions where applicable (note: full coverage pending test framework setup)
- [ ] **Documentation**: Updated README, docs, comments if needed
- [ ] **CHANGELOG**: Entry added for user-facing changes
- [ ] **Version Headers**: Present in new/modified docs
- [ ] **No Breaking Changes**: Unless explicitly intended and documented
- [ ] **Git History**: Clean, logical commits
- [ ] **Ready for Review**: Not a draft, passes available checks (`npm run build`, `npm run test`, `npm run version:sync`)

### Code Review Self-Checklist

Before creating PR, review your own code:

- [ ] Does it follow the repository conventions?
- [ ] Are variable names clear and descriptive?
- [ ] Are there any obvious bugs or logic errors?
- [ ] Is error handling appropriate?
- [ ] Are there any security concerns?
- [ ] Is the code DRY (Don't Repeat Yourself)?
- [ ] Are there comments explaining WHY, not WHAT?
- [ ] Does it pass all tests?
- [ ] Are there any console.log or debug statements?

## CI/CD Expectations

### Continuous Integration

All PRs go through CI checks:

1. **Build Check**: Code compiles without errors
2. **Test Suite**: All tests pass
3. **Type Check**: TypeScript passes strict mode
4. **Security Scan**: No known vulnerabilities
5. **Linting**: Code style compliance (if configured)

### Handling CI Failures

**If CI fails:**
1. Read the error message carefully
2. Reproduce locally: `npm run build && npm run test`
3. Fix the issue
4. Test the fix locally
5. Push the fix (don't just re-run CI)
6. Never force-push or close/reopen to reset CI

**When CI Failure is Not Your Fault:**
1. Verify it also fails on main branch
2. Check if it's a known issue
3. Report the issue with evidence
4. Ask user how to proceed

## Git Workflow Guidelines

### Branch Creation

**Always create from main:**
```bash
git checkout main
git pull origin main
git checkout -b {type}/{descriptor}
```

**Branch Name Examples:**
```
feature/new-skill-antislapp
fix/skill-registry-bug
docs/update-integration-guide
refactor/marketplace-registry-structure
claude/documentation-reorganization-skills
```

### Commits

**Format:**
```
[type] Brief description (max 72 chars)

Detailed explanation if helpful.

Affected Files:
- path/to/file1
- path/to/file2
```

**Types:**
- `[feat]` - New feature or skill
- `[fix]` - Bug fix
- `[docs]` - Documentation only
- `[refactor]` - Code reorganization
- `[test]` - Test additions
- `[chore]` - Maintenance

**Keep commits atomic:** One logical change per commit

### Pull Requests

**Title Format:**
```
[type] Brief description
```

**Description:**
1. Summary of changes
2. Why this change is needed
3. How to test/verify
4. Any related issues or PRs
5. Checklist of verification

**Never:**
- ❌ Merge your own PR without review
- ❌ Force-push to main or shared branches
- ❌ Commit directly to main
- ❌ Leave draft PRs open indefinitely
- ❌ Merge with CI failures

## Testing Requirements

### Test Coverage Goals

**Target state** (as project matures):
- **Unit tests**: >80% coverage for new code
- **Integration tests**: For skills and tools
- **Regression tests**: For bug fixes
- **Type safety**: Full TypeScript coverage

**Current state**: The repository is transitioning from placeholder tests. Focus on:
- Adding meaningful tests when creating new skills
- Writing regression tests for bug fixes
- Documenting test expectations in PR descriptions

### Writing Tests

**Test File Naming:**
```
skill-name/tests/{unit|integration}/feature.test.ts
```

**Test Structure:**
```typescript
describe('Skill Name', () => {
  describe('Feature Name', () => {
    it('should do specific thing', () => {
      // Arrange
      const input = {...};
      
      // Act
      const result = skill.execute('tool', input);
      
      // Assert
      expect(result).toEqual(...);
    });
  });
});
```

### Running Tests

```bash
# All tests
npm run test

# Specific workspace
npm run test --workspace=skill-name

# Watch mode
npm run test -- --watch

# Coverage report
npm run test -- --coverage
```

## Handling Uncertain Situations

### Scenario: "I don't know the right approach"

**Action:**
1. Research similar patterns in codebase
2. Read relevant docs
3. If still unclear, escalate with findings

**Escalation:**
```
I've researched this and found:
- Pattern A used in [file]
- Pattern B used in [file]

I'm unsure which to use here because [reason].

Can you help me decide?
```

### Scenario: "Tests are failing but I can't debug"

**Action:**
1. Run tests with verbose output
2. Isolate failing test
3. Review test expectations
4. Check if test needs updating
5. If still stuck, escalate with details

**Escalation:**
```
This test is failing and I can't determine why:

Test: [test name]
Error: [full error message]
Expected: [what should happen]
Actual: [what's happening]

I've tried:
- [approach 1]
- [approach 2]

Can you help debug this?
```

### Scenario: "Change affects multiple systems"

**Action:**
1. Map all affected systems
2. Assess impact on each
3. Create comprehensive PR description
4. Link to any related issues
5. Escalate with impact analysis

**Escalation:**
```
This change affects multiple areas:

1. System A - [impact]
2. System B - [impact]
3. System C - [impact]

I propose [solution] because [reasoning].

Do you approve this approach?
```

## Proactive Agent Responsibilities

Agents should proactively:

### Daily Checks (if working actively)

1. **Check Repository Health**
   ```bash
   npm run version:sync
   npm audit
   npm outdated
   ```

2. **Verify CI Status**
   - Check latest builds
   - Report any failures
   - Escalate if blocking

3. **Review PRs**
   - Track open PRs
   - Check for review requests
   - Monitor CI status

### Weekly Checks (if working actively)

1. **Dependency Updates**
   ```bash
   npm outdated
   npm update
   ```

2. **Documentation Review**
   - Check for broken links
   - Verify examples work
   - Update if outdated

3. **Test Coverage**
   - Run full test suite
   - Check coverage trends
   - Add missing tests

### When Taking On New Task

1. ✅ Read this file (AGENTS.md)
2. ✅ Review SKILL.md
3. ✅ Review CHANGELOG.md recent entries
4. ✅ Understand task scope
5. ✅ Identify known issues
6. ✅ Plan approach before coding
7. ✅ Ask if scope is unclear

## Escalation Contacts & Process

### When to Escalate

- Architectural questions
- Breaking changes
- Scope expansion
- Uncertainty on approach
- Blocked by external issues
- Time/resource constraints

### Escalation Template

```
**ESCALATION NEEDED:**

**Issue:**
[Brief description]

**Context:**
[Background information]

**Options Considered:**
1. [Option A] - [pros/cons]
2. [Option B] - [pros/cons]

**My Recommendation:**
[What I think should happen]

**Question:**
[Specific thing I need your decision on]

**Urgency:**
[High/Medium/Low]
```

## Success Metrics for Agents

### Quality Metrics

- ✅ 0 failing CI checks at merge
- ✅ Tests pass (comprehensive coverage pending test framework setup)
- ✅ 0 security vulnerabilities introduced
- ✅ Documentation complete for all changes
- ✅ CHANGELOG updated
- ✅ No breaking changes (unless intended)

### Process Metrics

- ✅ Follows branch naming conventions
- ✅ Commit messages follow format
- ✅ PRs are focused and reviewable
- ✅ Tests pass locally before pushing
- ✅ No force-pushes to shared branches
- ✅ Escalates appropriately

### Communication Metrics

- ✅ Clear PR descriptions
- ✅ Proactive communication of blockers
- ✅ Asks for clarification when needed
- ✅ Provides context for decisions
- ✅ Updates status regularly

## Common Pitfalls to Avoid

### ❌ Don't Do These

1. **Committing Secrets**
   - No API keys in code
   - No private credentials
   - No internal hostnames
   - Check before pushing!

2. **Breaking CI Without Fixing**
   - Always run tests locally
   - Don't push "experimental" code
   - Don't blame "flaky" tests
   - Fix it or revert it

3. **Wide-Ranging Changes**
   - One concern per PR
   - Don't mix refactoring with features
   - Don't "clean up" unrelated code
   - Keep PRs focused

4. **Ignoring Documentation**
   - Don't skip README updates
   - Don't forget CHANGELOG
   - Don't remove version headers
   - Don't break links

5. **Force-Pushing Shared Branches**
   - Never `git push --force` to main
   - Never `git push --force` to PR branches others use
   - Use `git push --force-with-lease` only when necessary
   - Ask before force-pushing anything

6. **Making Decisions Alone**
   - Don't decide architecture alone
   - Don't choose major dependencies alone
   - Don't change APIs alone
   - Ask when uncertain

## Quick Reference for Agents

| Need | Action |
|------|--------|
| Start a task | Read AGENTS.md, SKILL.md, CLAUDE.md |
| Create a skill | Follow docs/guides/development-guide.md |
| Fix a bug | Use bug fix pattern, autonomy level 3 |
| Update docs | Use doc update pattern, autonomy level 3 |
| Update dependency | Check version number, autonomy varies |
| Architectural decision | Ask first, autonomy level 1 |
| Unsure approach | Research, escalate if still unsure |
| CI failure | Debug locally, fix or ask for help |
| Broken tests | Reproduce, fix or ask for help |
| Long-running task | Schedule check-in, don't go idle |

## Summary

### Remember

- **Read this file first** (AGENTS.md)
- **Read SKILL.md for conventions**
- **Read CLAUDE.md for Claude-specific setup**
- **Ask if uncertain** (no penalty for asking)
- **Test before pushing** (always)
- **Update documentation** (always)
- **Update CHANGELOG.md** (always)
- **Keep changes focused** (one concern per PR)
- **Escalate appropriately** (when unclear)

### Your Job

As an agent:
1. **Deliver Quality**: Ensure tests pass and docs are complete
2. **Follow Conventions**: Match established patterns
3. **Communicate Clearly**: Explain decisions in PR descriptions
4. **Escalate Wisely**: Ask when uncertain
5. **Stay Focused**: One concern per PR
6. **Help Others**: Your code should be clear and well-documented

### When in Doubt

1. Reread AGENTS.md (this file)
2. Check SKILL.md for conventions
3. Review recent PRs for patterns
4. Look at git history for examples
5. Ask the user for clarification

---

**Last Updated**: 2026-09-30  
**Current Version**: 1.0.1  
**Repository**: https://github.com/Fused-Gaming/skills  
**License**: Apache-2.0 + Non-Commercial v1.0

**Agent Remember:** Autonomy is earned through consistency. The more you follow conventions and escalate wisely, the more autonomy you'll have in future tasks.

