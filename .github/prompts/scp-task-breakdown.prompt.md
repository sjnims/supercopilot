# /scp-task-breakdown

Break complex tasks into actionable, prioritized steps with clear dependencies and estimates.

## Workflow

### Phase 1: Task Understanding (Before Execution)

1. **Clarify Task Scope**
   - Ask what the high-level task or goal is
   - Identify success criteria and definition of "done"
   - Determine constraints (time, resources, dependencies)
   - Confirm if this is a bug fix, feature, refactor, or other type

2. **Gather Context**
   - Ask which files or modules are involved (if known)
   - Identify existing attempts or related work
   - Confirm priority level and urgency
   - Ask about preferred approach or must-have requirements

### Phase 2: Analysis (During Execution)

3. **Analyze Current State**
   - Use Serena to map relevant code structure
   - Identify all affected files and symbols
   - Document current behavior and state
   - Find related tests and documentation
   - Show progress: "Analyzing current implementation..."

4. **Research Approach**
   - Use Context7 for library-specific patterns if applicable
   - Use Tavily for best practices if unfamiliar territory
   - Review similar tasks in the codebase
   - Show progress: "Researching approaches..."

5. **Evaluate Complexity**
   - Use Sequential Thinking to assess complexity dimensions
   - Identify technical challenges and unknowns
   - Determine if task needs to be split into smaller parts
   - Assess risk areas that need extra attention
   - Show progress: "Evaluating complexity and risks..."

### Phase 3: Breakdown & Sequencing (During Execution)

6. **Create Task Hierarchy**
   - Break into logical subtasks (aim for <4 hours each)
   - Group related tasks into phases
   - Identify atomic tasks that can't be split further
   - Label tasks by type (research, implementation, testing, docs)
   - Show progress: "Creating task breakdown..."

7. **Map Dependencies**
   - Identify which tasks must be done sequentially
   - Find tasks that can be parallelized
   - Highlight blocking tasks (must be done first)
   - Note external dependencies (APIs, libraries, etc.)

8. **Estimate Effort**
   - Provide T-shirt sizes (S/M/L/XL) or hour estimates
   - Account for testing and documentation
   - Add buffer for unknowns and risks
   - Highlight high-uncertainty estimates

### Phase 4: Deliverables (After Execution)

9. **Generate Task Breakdown**
   Output structured markdown with:

   **Task Overview**
   - Goal and success criteria
   - Scope and constraints
   - Affected areas of codebase

   **Phase 1: [Phase Name]** (e.g., "Foundation & Setup")
   - [ ] Task 1.1: [Description] `[Estimate]` `[Type]`
     - Dependencies: None
     - Details: [specific steps if needed]
   - [ ] Task 1.2: [Description] `[Estimate]` `[Type]`
     - Dependencies: Task 1.1
     - Details: [specific steps if needed]

   **Phase 2: [Phase Name]** (e.g., "Core Implementation")
   - [ ] Task 2.1: [Description] `[Estimate]` `[Type]`
     - Dependencies: Phase 1 complete
     - Risk: [if applicable]

   **Phase 3: [Phase Name]** (e.g., "Testing & Documentation")
   - [ ] Task 3.1: [Description] `[Estimate]` `[Type]`

   **Critical Path**
   - Task 1.1 → Task 1.2 → Task 2.3 → Task 3.1

   **Parallel Work Opportunities**
   - Tasks 2.1, 2.2 can be done in parallel
   - Task 2.4 can start while 2.3 is in progress

   **Risks & Unknowns**
   - [List technical uncertainties]
   - [List dependency risks]

   **Total Estimate**
   - Optimistic: [X hours]
   - Realistic: [Y hours]
   - Pessimistic: [Z hours]

10. **Offer Follow-up Actions**
    - "Would you like me to dive deeper into any specific task?"
    - "Should I create a spike plan for any high-risk tasks?"
    - "Would you like me to start working on the first task?"

## Context Awareness

**When file is selected:**
- Focus breakdown on changes to that file
- Identify related files that may need changes

**When code is selected:**
- Treat selection as the area to modify
- Create tasks specific to that code block

**When in project root:**
- Provide project-level task breakdown
- Consider all affected areas

**When no context:**
- Ask for the task area or starting point

## Example Usage

### Example 1: Breaking Down a Feature Task
```
User: /scp-task-breakdown implement user notifications
Assistant: I'll help break down the notification feature. Let me understand the scope:

1. What types of notifications? (email, in-app, push, SMS, etc.)
2. Should they be real-time or batch processed?
3. Are there existing notification patterns in the codebase?
4. What's the priority? (MVP vs full-featured)

[After getting answers...]
[Uses Serena to analyze existing notification code if any...]
[Uses Sequential Thinking to evaluate implementation approaches...]
[Creates detailed phase-by-phase breakdown with estimates...]
```

### Example 2: Breaking Down a Bug Fix
```
User: [selects buggy function] /scp-task-breakdown fix memory leak in data processing
Assistant: I'll analyze this function and create a breakdown for fixing the memory leak.

First, let me clarify:
1. Do you know what's causing the leak (event listeners, closures, etc.)?
2. How critical is this? (production emergency vs scheduled fix)
3. Are there tests I should run to verify the fix?

[Uses Serena to find all usages of this function...]
[Creates breakdown including: reproduce bug, identify root cause, implement fix, add tests, verify in production...]
```

### Example 3: Breaking Down Refactoring Work
```
User: /scp-task-breakdown refactor authentication system to use JWT
Assistant: That's a significant refactoring. Let me ask:

1. Are you migrating from session-based auth?
2. Need to support both systems during transition?
3. Are there mobile clients or just web?
4. What's the timeline? (big-bang vs gradual rollout)

[Uses Serena to map all auth-related code...]
[Uses Sequential Thinking to plan migration strategy...]
[Creates multi-phase breakdown with rollback points...]

**Phase 1: Preparation & Setup** (can't break production)
- [ ] Research JWT libraries and best practices `2h` `research`
- [ ] Add JWT dependencies `30m` `setup`
- [ ] Create JWT utility functions `3h` `implementation`
- [ ] Add JWT tests `2h` `testing`

**Phase 2: Parallel Implementation** (run both systems)
- [ ] Implement JWT middleware `4h` `implementation`
- [ ] Update login endpoint to issue JWT `2h` `implementation`
...
```

## MCP Tools Usage Priority

1. **Serena** - Analyze code structure and dependencies
2. **Sequential Thinking** - Evaluate complexity and approach
3. **Context7** - Research library-specific patterns
4. **Tavily** - Find best practices for unfamiliar tasks
5. **Filesystem-with-morph** - (Not used - planning only, no code changes)

## Output Format

- **Structured markdown** with clear phases and task hierarchy
- **Actionable checklists** with checkboxes for tracking
- **Task metadata** (estimates, types, dependencies, risks)
- **Interactive prompts** for next steps
- Dependency graphs or critical paths where helpful
