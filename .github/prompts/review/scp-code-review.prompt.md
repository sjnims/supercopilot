# /scp-code-review

Perform comprehensive code quality review analyzing readability, maintainability, performance, and adherence to best practices.

## Workflow

### Phase 1: Review Scoping (Before Execution)

1. **Define Review Scope**
   - Ask what code should be reviewed (file, module, PR, entire project)
   - Identify specific concerns or focus areas
   - Determine review depth (quick pass vs thorough analysis)
   - Confirm if looking for specific issue types or general review

2. **Understand Context**
   - Ask about the code's purpose and criticality
   - Identify if this is new code, refactored code, or legacy code
   - Determine if code is working or has known issues
   - Confirm team's experience level and code standards

3. **Set Review Priorities**
   - Ask what matters most (readability, performance, security, testability, etc.)
   - Identify known pain points or technical debt
   - Determine if blocking issues only or all findings
   - Confirm if suggestions should include fixes or just identify issues

### Phase 2: Code Analysis (During Execution)

4. **Analyze Code Structure**
   - Use Serena to map code structure and dependencies
   - Identify complexity hotspots and coupling issues
   - Find circular dependencies or architectural concerns
   - Document code organization and patterns
   - Show progress: "Analyzing code structure and dependencies..."

5. **Review Against Principles**
   - Use Sequential Thinking to systematically check against @PRINCIPLES.instructions.md
   - Evaluate SOLID principles compliance
   - Check for DRY, KISS, YAGNI adherence
   - Assess separation of concerns
   - Review error handling patterns
   - Show progress: "Reviewing against engineering principles..."

6. **Check Code Quality**
   - Assess readability (naming, comments, clarity)
   - Evaluate maintainability (modularity, testability)
   - Check for code smells and anti-patterns
   - Review TypeScript usage and type safety
   - Assess function/class size and complexity
   - Show progress: "Analyzing code quality metrics..."

7. **Evaluate Performance**
   - Identify obvious performance issues
   - Check for inefficient algorithms or data structures
   - Look for unnecessary re-renders or computations
   - Find potential memory leaks
   - Review async/await and promise usage
   - Show progress: "Evaluating performance characteristics..."

8. **Research Best Practices**
   - Use Context7 to verify framework-specific patterns
   - Use Tavily to check current best practices if needed
   - Compare against industry standards
   - Identify outdated patterns or deprecated APIs
   - Show progress: "Checking against current best practices..."

### Phase 3: Issue Categorization (During Execution)

9. **Categorize Findings**
   - Group issues by severity (critical, high, medium, low)
   - Organize by category (bugs, security, performance, style, etc.)
   - Prioritize by impact and effort
   - Identify quick wins vs major refactoring
   - Show progress: "Categorizing findings..."

### Phase 4: Deliverables (After Execution)

10. **Generate Review Report**
    Output structured markdown with:

    **Code Review Summary**
    - Code reviewed: [files/scope]
    - Review date: [current date]
    - Reviewer: AI Assistant
    - Focus areas: [list priorities]

    **Overall Assessment**
    - **Quality Score:** [X/10]
    - **Readability:** [Excellent/Good/Fair/Poor]
    - **Maintainability:** [Excellent/Good/Fair/Poor]
    - **Test Coverage:** [Excellent/Good/Fair/Poor]
    - **Performance:** [Excellent/Good/Fair/Poor]

    **Summary:**
    [2-3 sentence overview of code quality and main findings]

    ---

    **Critical Issues** 🚨 (Must fix)

    ### Issue 1: [Issue title]
    **File:** `[file_path]:[line_number]`

    **Problem:**
    ```typescript
    // Current problematic code
    ```

    **Why it's critical:**
    - [Explanation of impact - security, bugs, data loss, etc.]

    **Recommendation:**
    ```typescript
    // Suggested fix
    ```

    **Impact:** [What breaks/improves with this change]
    **Effort:** [X hours/days]

    ---

    **High Priority** ⚠️ (Should fix soon)

    ### Issue 2: [Issue title]
    **File:** `[file_path]:[line_number]`

    **Problem:**
    [Description]

    **Impact:** [Performance degradation, maintainability issue, etc.]

    **Recommendation:**
    [Suggested approach]

    **Effort:** [Estimate]

    ---

    **Medium Priority** 💡 (Improve when possible)

    ### Issue 5: [Issue title]
    [Same structure]

    ---

    **Low Priority / Code Smells** 📝 (Nice to have)

    ### Issue 8: [Issue title]
    [Same structure]

    ---

    **Positive Observations** ✅

    - [Well-implemented pattern or practice]
    - [Good design decision]
    - [Clean, readable code section]

    ---

    **Detailed Analysis by Category**

    ### Architecture & Design
    - **Strengths:**
      - [What's done well]
    - **Concerns:**
      - [file_path]:[line_number] - [Issue description]

    ### Code Quality
    - **Readability issues:**
      - [List with file references]
    - **Complexity concerns:**
      - [List with file references]
    - **Naming improvements:**
      - [List with file references]

    ### Performance
    - **Bottlenecks identified:**
      - [file_path]:[line_number] - [Issue and impact]
    - **Optimization opportunities:**
      - [List]

    ### Error Handling
    - **Missing error handling:**
      - [List with file references]
    - **Improvements needed:**
      - [List]

    ### Testing
    - **Coverage gaps:**
      - [Areas lacking tests]
    - **Test quality:**
      - [Assessment of existing tests]

    ### TypeScript Usage
    - **Type safety issues:**
      - [List of any violations]
    - **Improvements:**
      - [Better typing opportunities]

    ---

    **Refactoring Opportunities**

    ### Opportunity 1: [Refactoring name]
    **Affected files:** [list]
    **Description:** [What to refactor and why]
    **Benefits:**
    - [Benefit 1]
    - [Benefit 2]
    **Effort:** [Estimate]
    **Priority:** [High/Medium/Low]

    ---

    **Action Items Checklist**

    **Immediate (Critical):**
    - [ ] Fix [critical issue 1] in [file] `[Estimate]`
    - [ ] Fix [critical issue 2] in [file] `[Estimate]`

    **Short-term (High Priority):**
    - [ ] Address [high priority issue 1] `[Estimate]`
    - [ ] Address [high priority issue 2] `[Estimate]`

    **Medium-term (Improvements):**
    - [ ] Refactor [area] for [reason] `[Estimate]`
    - [ ] Add tests for [component] `[Estimate]`

    **Long-term (Technical Debt):**
    - [ ] [Larger refactoring or improvement] `[Estimate]`

    ---

    **Metrics**
    - Total issues found: [count]
      - Critical: [count]
      - High: [count]
      - Medium: [count]
      - Low: [count]
    - Files reviewed: [count]
    - Lines of code: [count]
    - Estimated fix effort: [hours/days]

11. **Offer Follow-up Actions**
    - "Would you like me to fix any specific issues?"
    - "Should I create a refactoring plan for [identified opportunity]?"
    - "Would you like me to focus on any particular category of issues?"
    - "Should I review related files or modules?"

## Context Awareness

**When file is selected:**
- Review that specific file in detail
- Consider file's role in overall architecture
- Compare to similar files in project

**When code is selected:**
- Deep dive on selected code section
- Show specific improvements for selection
- Provide refactored version

**When in PR context:**
- Review PR changes specifically
- Compare before/after
- Focus on new/modified code

**When in project root:**
- Review overall project structure
- Identify architectural issues
- Suggest project-wide improvements

**When no context:**
- Ask for specific files or areas to review

## Example Usage

### Example 1: File Review
```
User: [selects user-service.ts] /scp-code-review
Assistant: I'll perform a comprehensive code review of user-service.ts.

Let me clarify focus:
1. Any specific concerns about this file?
2. Is this new code or existing code being reviewed?
3. What matters most? (performance, readability, security, etc.)

[Uses Serena to analyze file structure and dependencies...]
[Uses Sequential Thinking to check against principles...]

**Overall Assessment:**
Quality Score: 7/10 - Good code with some improvement opportunities

**Critical Issues: 0** 🎉

**High Priority: 2**
1. user-service.ts:45 - SQL injection vulnerability in search function
2. user-service.ts:112 - Memory leak in event listener

[Detailed review with specific fixes...]
```

### Example 2: PR Review
```
User: /scp-code-review review my PR changes
Assistant: I'll review the changes in your pull request.

Questions:
1. What's the PR's purpose? (feature, bugfix, refactor, etc.)
2. Any particular concerns?
3. Want full review or just changes?

[Uses Serena to analyze changed files...]
[Reviews new code against best practices...]

**PR Review Summary:**
Files changed: 5
Lines added: 234
Lines removed: 89

**Findings:**
- 1 critical security issue in auth.ts
- 3 suggestions for improved error handling
- 2 opportunities for better typing

[Detailed findings with recommendations...]
```

### Example 3: Project-wide Review
```
User: /scp-code-review review the entire API module
Assistant: I'll perform a comprehensive review of the API module.

This is a large scope. Let me clarify:
1. Quick pass or thorough analysis?
2. Specific focus? (security, performance, architecture, etc.)
3. Looking for quick wins or comprehensive technical debt assessment?

[Uses Serena to map entire API module structure...]
[Systematically reviews each file...]

**Module Assessment:**
Files reviewed: 23
Overall quality: 6.5/10
Main concerns: Inconsistent error handling, missing tests, some tight coupling

**Top 3 Refactoring Opportunities:**
1. Consolidate error handling (affects 15 files) - 8 hours
2. Add integration tests (covers 80% of endpoints) - 16 hours
3. Extract shared validation logic - 4 hours

[Comprehensive review with prioritized action plan...]
```

## MCP Tools Usage Priority

1. **Serena** - Primary tool for analyzing code structure and dependencies
2. **Sequential Thinking** - Systematically review against principles and standards
3. **Context7** - Verify framework-specific best practices
4. **Tavily** - Research current best practices for unfamiliar patterns
5. **Filesystem-with-morph** - (Not used - analysis only, no changes)

## Output Format

- **Structured markdown** with clear severity levels and categories
- **Code snippets** showing problems and solutions
- **File references** with line numbers for easy navigation
- **Actionable checklist** for addressing issues
- **Interactive prompts** for follow-up actions
- Metrics and summary for quick overview
