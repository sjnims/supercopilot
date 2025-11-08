---
description: 'Guidelines for generating git commit messages following Conventional Commits specification'
---

# Git Commit Message Guidelines

When generating git commit messages in the VSCode Source Control panel, follow the **Conventional Commits** specification to ensure consistency, clarity, and machine-readability.

## Commit Message Format

```
<type>[(optional scope)]: <description>

[optional body]

[optional footer(s)]
```

### Structure Rules

1. **Subject Line** (first line):
   - Format: `<type>[(scope)]: <description>`
   - Maximum 50 characters (strict)
   - Use **imperative mood** (e.g., "add" not "added" or "adds")
   - Start with lowercase letter
   - No period at the end
   - Think: "If applied, this commit will `<description>`"

2. **Body** (optional):
   - Separate from subject with a **blank line**
   - Wrap at 72 characters per line
   - Explain **what** and **why**, not **how**
   - Use when changes are complex or non-obvious

3. **Footer** (optional):
   - Separate from body with a **blank line**
   - Use for breaking changes and issue references
   - Format: `<token>: <value>` or `<token> #<value>`

## Commit Types

| Type | Description | When to Use |
|------|-------------|-------------|
| `feat` | New feature | Adding new functionality or capabilities |
| `fix` | Bug fix | Fixing a bug or error |
| `docs` | Documentation | Changes to README, comments, or docs |
| `style` | Formatting | Code style changes (whitespace, formatting, semicolons) - no logic change |
| `refactor` | Code restructuring | Refactoring code without changing behavior |
| `perf` | Performance | Performance improvements |
| `test` | Testing | Adding or modifying tests |
| `build` | Build system | Changes to build process, dependencies, or tools |
| `ci` | CI/CD | Changes to CI configuration files and scripts |
| `chore` | Maintenance | Other changes that don't modify src or test files |
| `revert` | Revert | Reverting a previous commit |

## Scope (Optional but Recommended)

The scope provides additional context about what part of the codebase is affected:

- Use parentheses: `feat(auth): add OAuth2 support`
- Common scopes: component names, file names, feature areas, modules
- Examples: `(api)`, `(ui)`, `(database)`, `(auth)`, `(parser)`
- Omit if change is global or scope is unclear

## Breaking Changes

Indicate breaking changes in **two ways**:

1. Add `!` after type/scope: `feat(api)!: remove deprecated endpoints`
2. Add footer: `BREAKING CHANGE: explanation of what broke and migration path`

Both methods can be used together for clarity.

## Examples

### Simple Commits

```
feat: add user authentication
fix: resolve null pointer in payment processor
docs: update installation instructions
style: format code with prettier
refactor: extract validation logic to separate module
test: add unit tests for user service
chore: update dependencies
```

### Commits with Scope

```
feat(auth): implement JWT token refresh
fix(ui): correct button alignment on mobile
docs(api): add OpenAPI specification
perf(database): optimize query for large datasets
build(deps): upgrade react to v18.2.0
```

### Commits with Body

```
fix(parser): handle edge case in date parsing

The parser was failing when encountering dates in ISO 8601 format
with timezone offsets. Updated the regex pattern to accommodate
these formats and added corresponding test cases.
```

### Breaking Changes

```
feat(api)!: redesign authentication endpoints

BREAKING CHANGE: The /auth/login endpoint now returns a different
response structure. Update your client code to use the new format:
{ "token": "...", "user": {...} } instead of { "accessToken": "..." }
```

### With Issue References

```
fix(checkout): prevent duplicate order submissions

Adds a debounce mechanism to prevent users from accidentally
submitting the same order multiple times by clicking rapidly.

Fixes #234
Closes #235
```

## Guidelines for AI-Generated Commits

When analyzing staged changes to generate commit messages:

1. **Analyze the diff** to determine:
   - What type of change was made (feat, fix, refactor, etc.)
   - What scope/component was affected
   - The core purpose of the change

2. **Identify the primary intent**:
   - If multiple types apply, choose the most significant
   - If changes span multiple areas, consider breaking into multiple commits

3. **Write clear descriptions**:
   - Be specific but concise
   - Focus on the business/functional impact
   - Avoid implementation details in the subject line

4. **Add body when**:
   - The change is complex or has multiple steps
   - There's important context about why the change was made
   - There are breaking changes or migration notes
   - The reasoning isn't obvious from the code

5. **Use appropriate scope**:
   - Infer from file paths (e.g., changes in `src/auth/` → `(auth)`)
   - Use component or module names when clear
   - Omit if too broad or unclear

## Special Cases

### Initial Commit
```
chore: initial commit
```

### Merge Commits
VSCode handles merge commits automatically - don't override the default merge message.

### Dependency Updates
```
build(deps): upgrade lodash to v4.17.21
chore(deps): update development dependencies
```

### Documentation Only
```
docs: add contributing guidelines
docs(readme): update installation steps for Windows
```

### Reverting Commits
```
revert: feat(auth): add OAuth2 support

This reverts commit abc123def456.
Reason: OAuth2 implementation caused performance issues in production.
```

## Anti-Patterns to Avoid

❌ **Don't**:
- Use past tense: ~~`added feature`~~
- End with period: ~~`fix: update parser.`~~
- Be vague: ~~`fix: fix bug`~~
- Capitalize: ~~`Fix: Update Parser`~~
- Exceed 50 chars: ~~`feat: add a really long description that explains everything in the subject line`~~
- Mix multiple unrelated changes in one commit

✅ **Do**:
- Use imperative mood: `add feature`
- Keep it concise: `fix: update parser`
- Be specific: `fix: handle null values in user profile`
- Use lowercase: `fix: update parser`
- Stay under 50 chars for subject
- Make atomic commits (one logical change per commit)

## Quick Reference

**Format**: `type(scope): description`

**Common Types**: feat, fix, docs, style, refactor, test, chore

**Subject Rules**: imperative, lowercase, no period, ≤50 chars

**Body**: blank line + wrapped at 72 chars + explain what/why

**Footer**: blank line + breaking changes + issue refs

---

*Based on [Conventional Commits v1.0.0](https://www.conventionalcommits.org/)*
