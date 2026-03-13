# Demetrios' Playground Debugging Flow

## When to Use This

You see a bug but can't easily articulate what's wrong. The bug is visual, architectural, or involves complex state. Use this flow when:
- You can point at the problem but words fail you
- You need to show WHERE in the codebase the issue manifests
- UI design tweaks needed (colors, spacing, interactions)
- Architecture is complex and you need to visualize component relationships

## Prerequisites

- Playground Skill available (interactive visualization generator)
- Repository with clear architecture or visual interface
- Ability to capture screenshots or interact with visualization
- Claude or agent that can process visual context

## The Problem: Bugs Are Easier to See Than Explain

**Classic workflow:**
- You see: "The filter button doesn't work"
- You try to explain: "The filter button in the dashboard doesn't filter the results. I clicked it with 'priority=high' and it still shows all items."
- Agent interprets: "Ah, filter button on a dashboard. Let me find all filter buttons..."
- Agent misses: The specific filter, the state management, the API contract

**The gap:** Seeing a bug ≠ explaining it. Agent doesn't have the same visual context you do.

## The Playground Debugging Flow

### Step 1: Invoke the Playground Skill

When you encounter a bug:

```
/playground
```

Or in conversation:
"I'm seeing something wrong, can you generate a visualization of this repo?"

### Step 2: Agent Generates Visual Map

Playground Skill analyzes the repository and produces an **interactive visualization** showing:
- File structure and relationships
- Component hierarchy (if applicable)
- Data flow
- State management flow (Redux, Context, etc.)
- API endpoints and consumers
- Database schema and relationships

**Example output (text representation):**
```
Repository Visualization
═══════════════════════════════════════

📦 Frontend
  ├── 📄 Dashboard.tsx
  │   ├── 📍 FilterPanel.tsx
  │   │   └── 🔗 /api/items/filter POST
  │   └── 📍 ItemList.tsx
  │       └── 🔗 /api/items GET
  │
  └── 📄 Filter Redux
      ├── Actions: setFilter, clearFilter
      └── State: { activeFilters: {}, results: [] }

📦 Backend
  ├── 🔗 /api/items GET → ItemController.list()
  ├── 🔗 /api/items/filter POST → ItemController.filter()
  │   └── 🗄️ database.query(filterOptions)
  │
  └── 📦 Services
      └── FilterService (applies business logic)

📦 Database
  ├── 📋 items (id, name, priority, status)
  └── 📋 filters (user_id, criteria, saved_at)
```

Interactive version allows you to click/expand sections.

### Step 3: Identify & Click the Problem Area

Using the visualization, click on the suspected problem location:

1. Click FilterPanel → see its implementation
2. Click /api/items/filter → see the endpoint
3. Click Filter Redux state → see current state shape
4. Click ItemList → see what it's rendering

Each click reveals:
- The relevant code snippet
- Current data passing through that component
- Tests (if any)
- Related files

### Step 4: Narrow Down with Interaction

If visual inspection isn't enough, **interact** with the visualization:

- Click "Show data flow" → trace how filter values flow from UI to backend
- Click "Show state changes" → see how Redux dispatches affect the visualization
- Click "Highlight consumers" → see everything that depends on FilterPanel

**Example interaction:**
```
You click: FilterPanel → Show data flow
Playground highlights in sequence:
  FilterPanel (user clicks filter)
    ↓ dispatch(setFilter(criteria))
    ↓ Redux store updates
    ↓ ItemList re-renders
    ↓ calls /api/items/filter
    ↓ Backend receives request
    ↓ Database query executes
    ↓ Results returned
    ↓ ItemList displays results

[Visualization shows each step. You can see where it breaks.]
```

### Step 5: Agent Generates Hyperspecific Prompt

Once you've identified the problem location, Playground Skill generates a **hyperspecific debugging prompt** with:

1. **Exact file paths and line numbers** of suspected issue
2. **Code snippets** from all relevant files
3. **Current behavior** vs **expected behavior**
4. **Data shape** at each step
5. **Related tests** that might clarify expectations

**Example generated prompt:**

```
BUG: Filter button not working

Location: src/frontend/Dashboard/FilterPanel.tsx (lines 42-67)

Problem manifests at:
- FilterPanel dispatches setFilter action correctly (Redux logs confirm)
- ItemList receives new Redux state (I can see it updates)
- But ItemList.tsx doesn't re-render properly

Code snapshot:
── FilterPanel.tsx (lines 42-67)
const handleFilterClick = (criteria) => {
  dispatch(setFilter(criteria));  // ← This works
}

── ItemList.tsx (lines 18-45)
function ItemList() {
  const items = useSelector(state => state.filter.results);

  useEffect(() => {
    fetchItems();  // ← Problem: never called when filter updates!
  }, []);  // ← Missing dependency: should depend on filter state
}

── API call
POST /api/items/filter
Request: { priority: "high" }
Response: ✓ Correct filtered results returned

Hypothesis: ItemList.useEffect() doesn't re-run when filter changes.
Fix: Add filter dependency to useEffect dependencies array.
```

You copy this prompt and send it to Claude:

```
Claude, here's a bug prompt from Playground:
[paste hyperspecific prompt]

Fix it.
```

Claude now has:
- Exact locations (not "somewhere in the filter code")
- Code context (not paraphrased)
- Relationships between components (not separate pieces)
- What's working vs what's not (not guesses)

## UI Design Use Case

Playground works great for design iteration too:

```
"The dashboard color scheme looks off."

/playground
[Visualization of all color-using components]
[Click color picker on each]
[Adjust values]
[See changes in real-time]
[Export updated theme variables]
```

Better than describing: "Make the header less blue and borders more subtle."

## Tips & Gotchas

**Tip:** Use Playground early in bug investigation. It's worth 10 minutes of setup to save 30 minutes of back-and-forth explanation.

**Gotcha:** Playground is only as good as your codebase structure. Spaghetti code with hidden dependencies won't visualize well. If visualization is hard to follow, your code structure needs work.

**Tip:** For complex bugs, take a screenshot of the visualization and annotate it with arrows/circles pointing to the problem. That's your visual debugging artifact.

**Gotcha:** Playground can't always infer data flow automatically. If your state management is unclear or distributed, add comments to your code to help it understand.

**Tip:** Keep visualizations as part of your debugging notes. In code reviews or incident reports, "here's the visualization highlighting the bug" is more convincing than paragraphs.

**Gotcha:** Don't rely on Playground to find bugs. Use it to EXPLAIN bugs you've already spotted. It's a communication tool, not a static analyzer.

**Tip:** Generate Playground visualizations for new contributors. It's a faster onboarding tool than any documentation.

## Why It Works

**Quote from Leo:** "A picture is worth 1000 words, at least 1000 tokens."

- **Traditional debugging:** Agent reads 20 files, builds mental model of architecture, guesses where problem is
- **Playground debugging:** You and agent see the same architecture, you point at the problem, agent fixes it

The visualization shortens the "building shared context" phase from 10 minutes to 2 minutes.

## Sample Session

```
[You're testing the dashboard]
[Filter button click doesn't update list]
[You can see the button respond, but list doesn't change]

You: /playground

[Playground generates interactive visualization]
[Shows: FilterPanel → Redux → ItemList → API]

You: Click ItemList component

[Code appears:]
function ItemList() {
  const filter = useSelector(s => s.filter);
  useEffect(() => {
    api.fetchItems();
  }, []); // ← Missing dependency
}

You: Ah, there's the bug.

[You select the useEffect code and send to Claude]

You: "Here's code from /playground. Fix the useEffect dependency array to respond to filter changes."

Claude: Fixed. New code:
useEffect(() => {
  api.fetchItems();
}, [filter]); // ← Now depends on filter

[Push fix, test, done]
```

## When NOT to Use Playground

- Simple typo bugs (use grep instead)
- Performance issues (need profiling, not visualization)
- Binary/external service issues (nothing to visualize)
- One-line fixes (overkill)
