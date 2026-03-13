# Rahul's Plan → Build → Punch It Pipeline

## When to Use This

You have a well-organized Linear backlog with clear tickets and want a systematic, sequential end-to-end workflow. Use this when you need high confidence that each feature moves from planning through implementation to validation with minimal rework.

## Prerequisites

- Linear board set up with tickets that include clear acceptance criteria
- Access to Claude with Plan, Build, and Punch It skills (or equivalent agent capabilities)
- Project with backend (Pydantic models, business logic, database routes) and frontend components
- Test infrastructure: Playwright MCP available, pre-commit hooks configured
- CI/CD pipeline capable of running tests

## The Three-Skill Pipeline

### Skill 1: Plan

**Trigger:** Linear ticket ID

**What happens:**
1. Agent switches to plan mode
2. Reads the ticket and all acceptance criteria
3. Breaks down ALL work into concrete steps:
   - Data model changes needed
   - Business logic required
   - Database schema updates
   - API routes to implement
   - Frontend screens/components to build
   - Tests required
4. Creates a detailed implementation roadmap
5. Asks for confirmation before proceeding

**Example output:**
```
Ticket: PROJ-42 "Add invoice filtering"
Breakdown:
- Create PydanticModel Invoice with filter fields
- Add database migration for new columns
- Implement /api/invoices/filter route
- Add OpenAPI schema generation
- Build FilterPanel component with form controls
- Write unit tests for filter logic
- Write E2E test with Playwright
Ready to proceed? (yes/no)
```

### Skill 2: Build

**Trigger:** Confirmed plan from Skill 1

**Workflow:**
1. **Pydantic Models:** Define data structures with validation
2. **Business Logic:** Implement core feature logic
3. **Database Routes:** Create migrations and query handlers
4. **OpenAPI Schema:** Generate or update API documentation automatically
5. **Frontend Code:** Build UI components based on API contract
6. **Tests:** Write unit and integration tests as you go
7. **Agent Browser Testing:** Use agent browser to visually validate implementation

**Key principle:** Work end-to-end for each small piece, not layer-by-layer. Build one filter feature completely before moving to the next.

**Checkpoints:**
- After models: confirm structure with original plan
- After routes: test endpoints manually
- After frontend: visual validation with agent browser
- After tests: all pass locally

### Skill 3: Punch It

**Trigger:** Build skill completes, code ready for validation

**Validation sequence:**
1. **Pre-commit tests:** Run pre-commit hooks (linting, formatting)
2. **Local execution:** Run code locally, verify no runtime errors
3. **Playwright MCP testing:** Run end-to-end tests with agent browser interaction
4. **CI tests:** Run full CI pipeline
5. **Auto-fix:** If issues found, agent automatically fixes them and retests

**If tests fail:**
- Agent analyzes failure
- Attempts fix
- Re-runs tests
- Reports back on resolution

## Sequential Ticket Flow

1. Create ticket in Linear with acceptance criteria
2. Run Plan Skill → get breakdown
3. Confirm breakdown (or iterate)
4. Run Build Skill → implements everything
5. Run Punch It Skill → validates everything
6. Merge to main

Each ticket is independent. Complete one fully before starting the next.

## Model Selection

- **Sonnet for:** Quick iteration on straightforward features, smaller tickets
- **Opus for:** Complex business logic, major architectural decisions, multi-component features

Consider switching mid-pipeline: use Sonnet for Build, Opus for complex Plan breakdown.

## Tips & Gotchas

**Tip:** Keep Linear tickets granular (1-2 day estimates). Smaller tickets reduce planning overhead and increase parallelization potential.

**Gotcha:** If Plan breakdown seems incomplete, don't skip confirmation. Ask the agent to expand the breakdown before proceeding — incomplete plans cause expensive rework in Build.

**Tip:** Use the agent browser in Build phase to catch visual bugs early. Screenshots catch issues that console logs miss.

**Gotcha:** Pre-commit hooks must be reliable. If they're flaky, fix them before running Punch It. Punch It will fail repeatedly on the same false positives.

**Tip:** Set up custom linting rules beyond ESLint. Pattern-specific rules catch domain logic errors better than general lint rules.

## Sample Workflow Session

```
$ /plan PROJ-47

[Agent analyzes ticket, creates breakdown]
Ticket: PROJ-47 "User dashboard export"
1. Add export_format field to User model
2. Create ExportService with CSV/JSON generation
3. Add /api/users/{id}/export POST endpoint
4. Add Export button to dashboard UI
5. Write tests for format generation
6. Write E2E test for button click → file download
Proceed? (y/n)

$ y

[Agent confirms, passes to build]

$ /build

[Agent implements all 6 components...]
[Uses agent browser to validate UI...]
Build complete. Ready for validation.

$ /punch

[Runs pre-commit, local tests, playwright, CI...]
All tests pass. Code ready to merge.
```
