---
name: documentation-first-setup
description: Use to create and maintain comprehensive documentation that helps agents navigate code effectively. Document directory structure, file purposes, architectural relationships, and design decisions so agents can work independently.
---

# Documentation-First Setup

## Overview

The Documentation-First Setup Skill creates and maintains comprehensive documentation that helps agents navigate code effectively. Agents navigate codebases via semantic search and tree-walking. Without good docs, they get lost, make assumptions, and produce lower-quality work. Humans traditionally don't maintain documentation because it's tedious. But agents should do it—their time is cheaper than ours.

**Core principle:** Well-documented code lets agents navigate independently and make architecture-aware decisions. Poorly documented code makes agents ask basic questions instead of shipping features.

**Dependency:** Claude Code CLI with access to read files and create documentation.

## When to Use

- New project setup: Establish documentation foundations from day one
- Onboarding new agents: Before assigning complex tasks
- After significant refactors: Update documentation to reflect new structure
- Before parallel work: Ensure agents have clear understanding of architecture
- Code review time: When you notice agents are confused about how things work
- Quarterly maintenance: Refresh documentation to match current codebase state

## When NOT to Use

- Small, trivial projects (single file, obvious structure)
- When nobody will ever touch the code again
- For third-party or generated code (document around it, not within it)

## Common Mistakes

| Mistake | Why it's wrong |
|---------|---------------|
| Over-documenting obvious things | "The User class represents a user" wastes time. Focus on *why* and *how*, not *what*. |
| Not documenting design decisions | Agents and humans both ask "why is this structured this way?" Design decisions are the most valuable documentation. |
| Letting documentation drift | Docs that don't match code become lies. Update docs as part of code changes, not later. |
| Making READMEs longer than code | If your README is longer than the code, you're documenting the wrong things. |
| Orphaning cross-references | If A mentions B, B should mention A. If links are broken, documentation becomes useless. |

## The Documentation Process

### Step 1: Scan Directory Structure

Start by understanding what we're documenting:

```bash
find [target-directory] -type f -name "*.py" -o -name "*.js" -o -name "*.ts" -o -name "*.go" | head -50
tree -L 3 -I "node_modules|__pycache__|venv|build"
```

Document:
- **Directory structure**: What's in each folder?
- **File count**: How many files total?
- **Technology**: What languages/frameworks?

Create a mental map:
```
Project/
├── src/
│   ├── core/        (core logic)
│   ├── api/         (external interfaces)
│   ├── utils/       (shared utilities)
│   └── models/      (data structures)
├── tests/           (test suite)
├── docs/            (documentation)
└── config/          (configuration)
```

### Step 2: File-Level Documentation

For **every significant file** that's missing a header comment:

**For code files**, add a comment block at the top that includes:
1. **Module name**: Exactly as it appears in imports
2. **Purpose**: One sentence of what this file does
3. **Key responsibilities**: 3-5 bullet points
4. **Key design decisions**: Why is it structured this way?
5. **Related files**: Other files this depends on or is used by
6. **Usage example**: How do you use this module?

Python example:
```python
"""
Module: user_service.py
Purpose: Handles user account management operations

Key responsibilities:
  - User authentication and session management
  - Profile CRUD operations
  - Permission checks and authorization

Key design decisions:
  - Uses dependency injection for database connections
  - Caches user profiles in Redis for 1 hour
  - All database operations are async

Related files:
  - database/user_repository.py: Database access layer
  - auth/jwt_handler.py: Token generation and validation
  - cache/redis_client.py: Cache backend

Usage example:
  service = UserService(db, cache)
  user = await service.get_user(user_id)
"""
```

JavaScript example:
```javascript
/**
 * Module: userService.js
 * Purpose: Handles user account management operations
 *
 * Key responsibilities:
 *   - User authentication and session management
 *   - Profile CRUD operations
 *   - Permission checks and authorization
 *
 * Key design decisions:
 *   - Uses dependency injection for database connections
 *   - Caches user profiles in Redis for 1 hour
 *   - All database operations are async (Promises)
 *
 * Related files:
 *   - database/userRepository.js: Database access layer
 *   - auth/jwtHandler.js: Token generation and validation
 *   - cache/redisClient.js: Cache backend
 *
 * Usage example:
 *   const service = new UserService(db, cache);
 *   const user = await service.getUser(userId);
 */
```

For complex classes/functions, add inline comments explaining "why," not just "what."

### Step 3: Folder-Level README.md

For **every directory** that doesn't have a README.md, create `[directory]/README.md`:

```markdown
# [Folder Name]

## Purpose
[One paragraph: What does this folder contain? Why is it organized this way?]

## Structure
What's in this directory:

- **[file/subfolder]**: [One sentence purpose]
- **[file/subfolder]**: [One sentence purpose]

## Architecture Notes
[How do the pieces relate? What's the design philosophy?]

Example for a `src/models/` directory:
- **base.py**: BaseModel abstract class with common patterns
- **user.py**: User model, extends BaseModel
- **team.py**: Team model, extends BaseModel
- **validators.py**: Shared validation functions used by all models

All models follow the Active Record pattern, handle their own validation,
and inherit from BaseModel which provides database save/load functionality.

## How to Use This Folder
[What should developers/agents do when they need something from here?]

When you need to:
- Define a new data model: Create a file here, extend BaseModel
- Add validation: Update validators.py or add model-specific methods
- Work with existing models: Import from the specific model file

## Key Design Decisions
- [Decision 1]: Why did we choose this approach?
- [Decision 2]: What problem does this solve?

## Dependencies
- Depends on: [what this folder uses]
- Used by: [what uses this folder]

## Testing
Tests for this folder are in: `tests/models/`

## Related Folders
- [Related folder]: How it relates
- [Related folder]: How it relates
```

### Step 4: Cross-Reference Documentation

Create (or update) `docs/ARCHITECTURE.md` or `ARCHITECTURE.md` at project root:

```markdown
# Architecture Overview

## System Components

### [Component Name]
Location: `src/component_name/`
Purpose: [What does it do?]
Key files: [List key files]

### [Component Name]
Location: `src/component_name/`
Purpose: [What does it do?]
Key files: [List key files]

## Data Flow
[Describe how data moves through the system]

Example for ML pipeline:
```
Raw Data (data/raw/)
  → Preprocessing (src/preprocessing/pipeline.py)
  → Feature Engineering (src/features/engineer.py)
  → Training (src/training/train.py)
  → Evaluation (src/evaluation/metrics.py)
  → Model Artifacts (models/)
```

## Key Design Patterns
- [Pattern 1]: Used in [component], solves [problem]
- [Pattern 2]: Used in [component], solves [problem]

## External Dependencies
- [Library]: Used for [purpose], located in [component]
- [Library]: Used for [purpose], located in [component]

## Database Schema
[Link to schema or embed key entity relationships]

## API Endpoints
[Link to API docs or list key endpoints]

## Configuration
Key configuration in: `[location]`
Important settings:
- [Setting]: [What it does]
- [Setting]: [What it does]

## Deployment
[How is this system deployed?]

## Scaling Considerations
[What scales easily? What doesn't? What are the bottlenecks?]
```

### Step 5: Handle Special Cases

**For generated code**: Don't document individual generated files. Instead, document:
- The generator (what creates these files)
- What the output is for
- How to regenerate
- Any manual customizations to watch for

Example:
```markdown
# Generated: Database Models (auto-generated)

These files are generated from `schema/models.sql` using SQLAlchemy's declarative generator.

**Generator**: `scripts/generate_models.py`
**Frequency**: Run this whenever you change `schema/models.sql`
**Manual customizations**: None (these are purely generated)

If you need to add business logic to a model, add it to `src/models/mixins/` instead.
```

**For third-party code**: Don't document it. Instead, document:
- Why you're using it
- What you're using from it
- Where it's configured
- Any custom extensions

Example:
```markdown
# FastAPI Configuration
Location: `src/api/app.py`
Third-party: FastAPI (web framework)

We use FastAPI for:
- REST API endpoints
- Request validation
- Automatic OpenAPI docs

Key customizations:
- Custom error handler in `src/api/middleware/error_handler.py`
- JWT authentication middleware in `src/api/middleware/auth.py`
```

### Step 6: Update During Code Changes

When you make code changes:
1. If you rename/move files: Update all references in documentation
2. If you add files: Add file-level header and update folder README
3. If you change architecture: Update ARCHITECTURE.md
4. If you change APIs: Update relevant documentation

**Important**: Update documentation as part of the code change, not in a separate step.

### Step 7: Validation Checklist

Before marking documentation complete:

- [ ] Every `.py`, `.js`, `.ts`, `.go` file has a header comment explaining purpose
- [ ] Every folder has a README.md
- [ ] ARCHITECTURE.md or docs/ARCHITECTURE.md exists
- [ ] All cross-references are accurate (README links, file mentions, etc.)
- [ ] No "TODO: document this" or similar placeholders
- [ ] Related files links are reciprocal (if A mentions B, B mentions A)
- [ ] Code examples in docs are accurate and would work
- [ ] Configuration and setup instructions are clear
- [ ] A new developer could understand the system from docs + code

## Output Format

Provide a summary:

```
## Documentation Setup Complete

### Files Documented
- [count] Python files
- [count] JavaScript files
- [count] configuration files
- etc.

### Documentation Created
- [ ] File-level headers added to [count] files
- [ ] README.md created for [count] folders
- [ ] ARCHITECTURE.md created or updated
- [ ] Cross-references checked

### Validation
- [count] files with clear header comments
- [count] README.md files in place
- All internal references verified

### Ready for Use
YES - Agents can now navigate this codebase effectively
```

## Configuration Notes

### Language-Specific Customization

**Python**:
```python
# Use """module docstring""" at top of file
# Standard: triple-quoted docstrings following Google/NumPy style
```

**JavaScript/TypeScript**:
```javascript
// Use JSDoc format for files
// /** module docs */ or use TSDoc for TypeScript
```

**Go**:
```go
// Use standard Go package documentation format
// godoc will extract these automatically
```

### Project-Specific Customization

1. **Add your tech stack to scanning**:
   ```
   Add file extensions: .scala, .java, .rs, .rb, etc.
   ```

2. **Customize folder categories**:
   ```
   Your project probably has:
   - Source code directory (src/, lib/, etc.)
   - Test directory (tests/, __tests__, spec/)
   - Configuration directory (config/, etc.)
   - Docs directory (docs/, doc/, etc.)
   Update to match your structure.
   ```

3. **Add required documentation sections**:
   ```
   If your project requires:
   - Security considerations
   - Performance characteristics
   - Database migration guides
   - Monitoring/logging approach
   Add these as required sections in folder READMEs
   ```

## How to Invoke

Run once at project setup:
```
/documentation-first-setup

Directory: [target directory or "."]
```

Update after significant changes:
```
/documentation-first-setup

Directory: src/
Update type: "refresh" (all files) or "new files only"
```

## Tips from Practitioners

**When to run this**: Best done early in a project, then maintained incrementally. Running it on an existing project can be valuable but requires more effort.

**Don't over-document**: You don't need multi-paragraph descriptions for simple files. One sentence of purpose + key design decision is often enough.

**Make documentation specific**: "Handles user data" is bad. "Manages user authentication tokens, validates JWT claims, and handles session expiry" is good. Agents benefit from specificity.

**Update as you code**: Don't let documentation drift. When you rename a function, update the docs immediately. When you refactor, update the architecture description.

**Cross-references matter**: When a file references another file, document that relationship. When Agent A looks at file A and doesn't understand it, they should be able to follow the "Related files" link to understand it.

**Code examples**: Include real usage examples in documentation. Agents and humans both learn faster from concrete examples.

**Red flags that documentation is missing**:
- Agents ask you "how does X work?" questions
- Agents make assumptions about code structure that are wrong
- Agents spend time reading through code trying to understand relationships
- Documentation would answer these questions

**Pro tip**: Have agents write documentation about code they encounter. They'll ask good questions and surface ambiguities that humans miss.

## Key Principles

1. **Documentation enables agent independence.** Agents with good docs ship features. Agents without docs ask basic questions.
2. **Design decisions are the most valuable docs.** Code shows *what* and *how*. Documentation explains *why*.
3. **Update docs with code changes.** Docs that drift become lies. Update as part of the code change.
4. **Be specific and concrete.** Agents learn from specific examples and clear relationships, not abstract descriptions.
5. **Cross-references reduce navigation overhead.** If A depends on B, A should mention B. If A is used by B, B should mention A.

## Attribution

Based on techniques from the Coding Agents Lunch & Learn Series. Rob Ennals (Anthropic) contributed the core insight: "The reason why humans don't normally do that is because it's a ton of work. But the great thing about agents is their time is cheaper than ours. So we should just have agents write and maintain documentation."
