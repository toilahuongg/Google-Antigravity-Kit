---
activation: model_decision
description: Apply when working with git commits, version control, or commit messages
---

# Git Commit Rules

## Commit Message Format

Use Conventional Commits format with required scope:

```
<type>(<scope>): <description>

[optional body]

[optional footer]
```

### Types

| Type | Description |
|------|-------------|
| `feat` | New feature |
| `fix` | Bug fix |
| `docs` | Documentation changes |
| `style` | Code style (formatting, semicolons, etc.) |
| `refactor` | Code refactoring (no feature/fix) |
| `perf` | Performance improvements |
| `test` | Adding or updating tests |
| `chore` | Maintenance tasks (deps, configs) |
| `ci` | CI/CD changes |

### Scopes (required)

Use the component or area being modified:
- `app` - Main application code
- `api` - API routes and controllers
- `settings` - Settings features
- `wishlist` - Wishlist functionality
- `email` - Email marketing features
- `web-components` - Frontend web components
- `deps` - Dependencies
- `config` - Configuration files

### Rules

1. **Language**: Write commit messages in English
2. **Scope required**: Always include a scope in parentheses
3. **Description**: Use imperative mood ("add" not "added" or "adds")
4. **Length**: Keep first line under 72 characters
5. **No period**: Don't end description with a period

### Examples

✅ Correct:
```
feat(wishlist): add product variant support
fix(api): handle null response from Shopify
refactor(settings): extract validation logic
docs(readme): update installation steps
chore(deps): upgrade prisma to v5.0
```

❌ Avoid:
```
updated wishlist                    # No type, no scope
feat: add feature                   # Missing scope
feat(wishlist): Added new feature.  # Past tense, has period
Fix bug                             # Wrong case, no scope
```
