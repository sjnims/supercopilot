# /scp-refactor

Guide comprehensive code refactoring with analysis, planning, and structured execution to improve code quality while preserving behavior.

## Workflow

### Phase 1: Refactoring Scope (Before Execution)

1. **Define What to Refactor**
   - Ask what code should be refactored (function, class, module, entire feature)
   - Identify the primary goal (readability, performance, testability, maintainability)
   - Determine if this is opportunistic refactoring or addressing technical debt
   - Confirm if refactoring new code or legacy code

2. **Understand Current Issues**
   - Ask what problems exist with current code
   - Identify pain points (hard to test, hard to understand, performance issues, etc.)
   - Determine trigger for refactoring (new feature, bug fix, code review feedback)
   - Confirm if code is working correctly or has bugs

3. **Set Constraints**
   - Ask about time constraints and priority
   - Determine if API/interface can change or must stay compatible
   - Confirm test coverage expectations
   - Identify risk tolerance (aggressive vs conservative refactoring)

### Phase 2: Analysis (During Execution)

4. **Analyze Current Code**
   - Use Serena to map code structure, dependencies, and usages
   - Identify all files and functions that depend on code being refactored
   - Document current behavior and responsibilities
   - Find existing tests
   - Show progress: "Analyzing current code structure and dependencies..."

5. **Identify Code Smells**
   - Long functions or classes
   - Duplicated code
   - Complex conditionals
   - Tight coupling
   - Low cohesion
   - Poor naming
   - Mixed abstraction levels
   - Show progress: "Identifying code smells and anti-patterns..."

6. **Research Better Patterns**
   - Use Context7 to find framework-recommended patterns
   - Use Tavily to research modern approaches if needed
   - Find similar well-written examples
   - Review @PRINCIPLES.instructions.md for guidance
   - Show progress: "Researching better patterns and approaches..."

7. **Evaluate Refactoring Approaches**
   - Use Sequential Thinking to compare refactoring strategies
   - Consider: Extract Method, Extract Class, Introduce Parameter Object, etc.
   - Evaluate trade-offs (complexity vs clarity, performance vs maintainability)
   - Choose appropriate design patterns
   - Show progress: "Evaluating refactoring strategies..."

### Phase 3: Planning (During Execution)

8. **Create Refactoring Plan**
   - Break refactoring into safe, incremental steps
   - Identify which refactorings can be automated safely
   - Plan test strategy (write tests first if missing)
   - Determine backwards compatibility approach
   - Plan rollback strategy if issues arise
   - Show progress: "Creating step-by-step refactoring plan..."

9. **Assess Risk**
   - Identify high-risk changes
   - Plan validation steps
   - Determine if feature flag is needed
   - Consider gradual migration vs big-bang approach
   - Show progress: "Assessing refactoring risks..."

### Phase 4: Execution Guidance (During Execution)

10. **Provide Refactoring Steps**
    Output structured markdown with:

    **Refactoring Overview**
    - Code to refactor: [file/function/module]
    - Primary goal: [readability/performance/testability/etc.]
    - Approach: [strategy name]
    - Risk level: [Low/Medium/High]

    **Current State Analysis**

    **Code Location:**
    `[file_path]:[line_numbers]`

    **Current Issues:**
    - 🔴 [Critical issue 1]
    - 🟡 [Medium issue 2]
    - 🟡 [Medium issue 3]

    **Dependencies:**
    - Called by: [list of files/functions]
    - Calls: [list of dependencies]
    - Impact radius: [X files affected]

    **Current Code:**
    ```typescript
    // Current implementation with issues highlighted
    ```

    **Complexity Metrics:**
    - Lines of code: [count]
    - Cyclomatic complexity: [number]
    - Number of responsibilities: [count]
    - Test coverage: [percentage]

    ---

    **Refactored Code Design**

    **Target State:**
    ```typescript
    // Proposed refactored code
    // Well-structured and commented
    ```

    **Improvements:**
    - ✅ [Improvement 1]
    - ✅ [Improvement 2]
    - ✅ [Improvement 3]

    **Design Decisions:**
    - **Pattern used:** [pattern name]
    - **Why this approach:** [rationale]
    - **Trade-offs:** [what we gain vs what we lose]

    ---

    **Step-by-Step Refactoring Plan**

    ### Preparation Phase

    #### Step 0: Add Tests (if missing) `[Estimate]`
    **Why:** Ensure we don't break existing behavior

    - [ ] Add test for current behavior
    - [ ] Verify tests pass with current implementation
    - [ ] Achieve [X]% coverage before refactoring

    **Tests to add:**
    ```typescript
    // Test cases to ensure behavior preservation
    ```

    ---

    ### Refactoring Phase (Each step preserves working code)

    #### Step 1: [Refactoring technique name] `[Estimate]`
    **Technique:** [Extract Method/Rename Variable/etc.]
    **Risk:** [Low/Medium/High]
    **Automated:** [Yes/No]

    **Before:**
    ```typescript
    // Code before this step
    ```

    **After:**
    ```typescript
    // Code after this step
    ```

    **Why this step:**
    [Explanation of what this achieves]

    **Validation:**
    - [ ] Tests still pass
    - [ ] [Specific behavior still works]

    **If using Filesystem-with-morph:**
    ```
    This step can be safely automated with morph tool
    ```

    ---

    #### Step 2: [Next refactoring technique] `[Estimate]`
    [Same structure as Step 1]

    ---

    #### Step 3: [Next refactoring technique] `[Estimate]`
    [Same structure]

    ---

    ### Cleanup Phase

    #### Step N: Final Cleanup `[Estimate]`
    - [ ] Remove dead code
    - [ ] Update documentation
    - [ ] Update related comments
    - [ ] Check code style consistency

    ---

    **Files to Modify**

    ### Primary Changes
    - `[file_path]` - [description of changes]
    - `[file_path]` - [description of changes]

    ### Dependent Changes
    - `[file_path]` - [update imports/calls]
    - `[file_path]` - [update types/interfaces]

    ### New Files (if applicable)
    - `[file_path]` - [new module/class extracted]

    ---

    **Testing Strategy**

    ### Before Refactoring
    - [ ] Run existing tests - all should pass
    - [ ] Add missing tests for current behavior
    - [ ] Document edge cases

    ### During Refactoring
    - [ ] Run tests after each step
    - [ ] Add tests for new extracted functions
    - [ ] Verify no regression

    ### After Refactoring
    - [ ] Full test suite passes
    - [ ] Code coverage maintained or improved
    - [ ] Manual testing of critical paths

    **New Tests Needed:**
    ```typescript
    // Additional tests for refactored code
    ```

    ---

    **Migration Plan** (if API changes)

    ### Option A: Direct Replacement (if no API changes)
    - Refactor implementation
    - Tests ensure no behavior change
    - Deploy

    ### Option B: Gradual Migration (if API changes)

    #### Phase 1: Introduce new API alongside old
    ```typescript
    // Old function (deprecated)
    // New function (recommended)
    ```

    #### Phase 2: Migrate consumers
    - [ ] Update call site 1 `[file_path]`
    - [ ] Update call site 2 `[file_path]`
    - [ ] Update call site 3 `[file_path]`

    #### Phase 3: Remove old API
    - [ ] Verify no usages remain
    - [ ] Remove deprecated code
    - [ ] Update documentation

    ---

    **Risk Assessment**

    ### High-Risk Areas
    - ⚠️ [Area with high risk and mitigation]
    - ⚠️ [Another risky area and mitigation]

    ### Mitigation Strategies
    - Feature flag for gradual rollout
    - Extra monitoring during deployment
    - Easy rollback plan

    ### Rollback Plan
    If issues arise:
    1. [Immediate action]
    2. [Rollback steps]
    3. [How to verify system is healthy]

    ---

    **Before & After Comparison**

    | Aspect | Before | After | Improvement |
    |--------|--------|-------|-------------|
    | Lines of code | [X] | [Y] | [Z% reduction] |
    | Cyclomatic complexity | [X] | [Y] | [Z% reduction] |
    | Number of responsibilities | [X] | [Y] | [improvement] |
    | Test coverage | [X%] | [Y%] | [+Z%] |
    | Maintainability | [rating] | [rating] | [better] |

    ---

    **Implementation Checklist**

    **Pre-refactoring:**
    - [ ] Review current code and understand behavior `[Estimate]`
    - [ ] Add tests if missing `[Estimate]`
    - [ ] Create feature branch `5min`
    - [ ] Backup/commit current state `5min`

    **Refactoring steps:**
    - [ ] Step 1: [description] `[Estimate]`
    - [ ] Step 2: [description] `[Estimate]`
    - [ ] Step 3: [description] `[Estimate]`
    [etc.]

    **Post-refactoring:**
    - [ ] Run full test suite `[Estimate]`
    - [ ] Update documentation `[Estimate]`
    - [ ] Code review `[Estimate]`
    - [ ] Deploy to staging `[Estimate]`
    - [ ] Monitor for issues `[Estimate]`

    **Total Estimated Effort:** [X hours/days]

    ---

    **Common Refactoring Patterns Applied**

    ### [Pattern 1 Name]
    **What:** [Description]
    **Why:** [Benefit]
    **Where:** [file_path]:[line_number]

    ### [Pattern 2 Name]
    [Same structure]

    ---

    **Resources**
    - [Refactoring pattern documentation](url)
    - [Related pattern example](url)

11. **Offer Follow-up Actions**
    - "Would you like me to implement the refactoring now using morph tool?"
    - "Should I start with Step 1 and proceed incrementally?"
    - "Would you like me to write the missing tests first?"
    - "Should I explain any specific refactoring pattern in detail?"

## Context Awareness

**When file is selected:**
- Refactor the entire file
- Analyze file structure and organization
- Suggest file-level refactoring

**When function/class is selected:**
- Focus refactoring on selected code
- Show before/after for selection
- Minimize changes outside selection

**When multiple files selected:**
- Refactor across files (rename, extract shared code, etc.)
- Ensure consistency across files
- Plan coordinated changes

**When no context:**
- Ask what code needs refactoring

## Example Usage

### Example 1: Function Refactoring
```
User: [selects long complex function] /scp-refactor
Assistant: I'll help refactor this function. Let me analyze it first.

Questions:
1. What's your primary concern? (too long, hard to test, performance, etc.)
2. Can the function signature change?
3. Is this function well-tested?

[Uses Serena to find all usages of this function...]

**Current State Analysis:**
- Function: calculateOrderTotal
- Lines: 156 (should be <50)
- Cyclomatic complexity: 14 (should be <10)
- Responsibilities: 5 (should be 1)
- Tests: None found

**Issues:**
🔴 Multiple responsibilities (validation, calculation, formatting, logging, error handling)
🟡 Deeply nested conditionals (4 levels)
🟡 Duplicated discount logic

**Refactoring Approach: Extract Method + Strategy Pattern**

**Step-by-Step Plan:**
1. Add tests for current behavior (2h)
2. Extract validation into validateOrder() (30m)
3. Extract calculation into separate calculator class (1h)
4. Extract discount logic into strategy pattern (1.5h)
5. Simplify main function to orchestrator (30m)
6. Add tests for new extracted functions (1h)

[Detailed before/after code with full refactoring plan...]
```

### Example 2: Module Refactoring
```
User: /scp-refactor the user service is becoming too complex
Assistant: I'll analyze the user service and create a refactoring plan.

Questions:
1. What makes it complex? (too many responsibilities, hard to test, etc.)
2. Can we break it into multiple services?
3. Timeline for this refactoring?

[Uses Serena to analyze entire user service module...]

**Module Analysis:**
- Files: 1 (UserService.ts - 847 lines)
- Responsibilities: 8 (auth, profile, settings, notifications, etc.)
- Dependencies: 12 direct imports
- Depended on by: 23 files

**Refactoring Approach: Extract Service Classes**

**Target Structure:**
```
services/
├── AuthService.ts (authentication logic)
├── ProfileService.ts (profile management)
├── SettingsService.ts (user settings)
├── NotificationService.ts (notifications)
└── UserService.ts (orchestrator, 50 lines)
```

**Migration Plan:**
Phase 1: Extract without breaking API (2 days)
Phase 2: Migrate callers to new services (3 days)
Phase 3: Remove old UserService (1 day)

[Detailed step-by-step extraction plan...]
```

### Example 3: Performance Refactoring
```
User: [selects slow data processing function] /scp-refactor this is too slow
Assistant: I'll refactor for performance while maintaining readability.

Questions:
1. How slow is it currently? (processing time, data volume)
2. What's the target performance?
3. Can we change the algorithm or just optimize current one?

[Analyzes current implementation...]

**Performance Analysis:**
- Current: O(n²) complexity
- Processing 10,000 items in 8.5 seconds
- Target: <1 second

**Refactoring Approach: Algorithm Optimization + Caching**

**Step-by-Step:**
1. Add performance tests (baseline) (1h)
2. Replace nested loops with Map lookup (2h)
   - Complexity: O(n²) → O(n)
3. Add memoization for repeated calculations (1h)
4. Use streaming for large datasets (2h)

**Expected improvement: 8.5s → 0.3s (28x faster)**

[Detailed before/after with performance benchmarks...]
```

## MCP Tools Usage Priority

1. **Serena** - Primary tool for analyzing code structure, dependencies, and usages
2. **Sequential Thinking** - Evaluate refactoring strategies systematically
3. **Context7** - Find framework-recommended patterns
4. **Tavily** - Research refactoring patterns and techniques
5. **Filesystem-with-morph** - Can be used for safe refactoring execution (if user approves)

## Output Format

- **Structured markdown** with clear before/after states
- **Step-by-step plan** with estimates
- **Code examples** showing each refactoring step
- **Testing strategy** for validation
- **Actionable checklist** for implementation
- **Interactive prompts** for execution
- Risk assessment and mitigation
- Comparison tables showing improvements
