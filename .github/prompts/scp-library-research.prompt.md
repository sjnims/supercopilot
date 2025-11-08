# /scp-library-research

Research and evaluate libraries, frameworks, or tools for a specific use case with comprehensive comparison and recommendations.

## Workflow

### Phase 1: Requirements Gathering (Before Execution)

1. **Clarify the Need**
   - Ask what problem needs to be solved
   - Identify specific requirements and must-haves
   - Determine constraints (size, dependencies, license, etc.)
   - Confirm acceptable trade-offs (features vs simplicity, etc.)

2. **Define Evaluation Criteria**
   - Ask what factors matter most (performance, DX, community, etc.)
   - Identify deal-breakers or red flags
   - Confirm if comparing specific libraries or discovering options
   - Determine if production-ready or experimental is acceptable

3. **Understand Context**
   - Ask about existing tech stack and compatibility needs
   - Identify similar libraries already in use
   - Confirm team expertise level (beginner-friendly vs advanced)
   - Determine project timeline (need stable vs can use cutting-edge)

### Phase 2: Discovery (During Execution)

4. **Find Candidate Libraries**
   - Use Tavily to search for libraries matching the use case
   - Use Context7 to access official documentation for known options
   - Search for "awesome lists" and curated collections
   - Identify 3-5 strong candidates
   - Show progress: "Discovering library options for [use case]..."

5. **Gather Current Information**
   - Check latest versions and release frequency
   - Review GitHub stars, forks, and recent activity
   - Look for download/usage statistics
   - Identify if actively maintained or abandoned
   - Show progress: "Gathering metadata for candidate libraries..."

6. **Research Community & Ecosystem**
   - Check issue response times and quality
   - Look for security advisories or critical bugs
   - Find tutorials, guides, and learning resources
   - Identify ecosystem plugins or extensions
   - Show progress: "Evaluating community health..."

### Phase 3: Technical Evaluation (During Execution)

7. **Analyze Technical Fit**
   - Use Context7 to review official documentation and APIs
   - Check TypeScript support and type quality
   - Review bundle size and performance characteristics
   - Examine dependencies and transitive dependencies
   - Assess testing and code quality
   - Show progress: "Analyzing technical characteristics..."

8. **Check Integration Requirements**
   - Use Serena to analyze how it would integrate with existing code
   - Identify required configuration or setup
   - Check framework compatibility (React, Vue, Node.js, etc.)
   - Assess migration effort from current solution (if applicable)
   - Show progress: "Evaluating integration with existing codebase..."

9. **Compare Options Systematically**
   - Use Sequential Thinking to create structured comparison
   - Score each library against defined criteria
   - Identify unique strengths and weaknesses
   - Note any surprising findings or concerns
   - Show progress: "Creating systematic comparison..."

### Phase 4: Deliverables (After Execution)

10. **Generate Research Report**
    Output structured markdown with:

    **Research Overview**
    - Use case: [problem being solved]
    - Evaluation date: [current date]
    - Libraries compared: [list]

    **Requirements Summary**
    - Must-have features: [list]
    - Constraints: [list]
    - Evaluation criteria: [list with weights/priorities]

    **Library Comparison**

    ### Option 1: [Library Name] `⭐ Recommended` (if applicable)

    **Overview**
    - Version: [latest version]
    - License: [license type]
    - Bundle size: [size]
    - Weekly downloads: [count]
    - Last updated: [date]

    **Strengths**
    - ✅ [Strength 1]
    - ✅ [Strength 2]
    - ✅ [Strength 3]

    **Weaknesses**
    - ⚠️ [Weakness 1]
    - ⚠️ [Weakness 2]

    **Community Health**
    - GitHub stars: [count]
    - Open issues: [count]
    - Recent commits: [activity level]
    - Maintenance: [Active/Stable/Maintenance mode]

    **Integration Notes**
    - Setup complexity: [Low/Medium/High]
    - Framework compatibility: [list]
    - Migration effort: [if applicable]

    **Code Example**
    ```typescript
    // Quick example of basic usage
    ```

    **Documentation Quality**
    - Official docs: [Excellent/Good/Fair/Poor]
    - Examples: [Comprehensive/Adequate/Limited]
    - API reference: [Complete/Partial]

    ### Option 2: [Library Name]
    [Same structure as Option 1]

    ### Option 3: [Library Name]
    [Same structure as Option 1]

    **Decision Matrix**

    | Criteria | Weight | Option 1 | Option 2 | Option 3 |
    |----------|--------|----------|----------|----------|
    | Feature completeness | High | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐ |
    | Performance | High | ⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐ |
    | Bundle size | Medium | ⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ |
    | DX/API quality | High | ⭐⭐⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐⭐ |
    | Community | Medium | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐ |
    | TypeScript | High | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐ |

    **Recommendation**

    **Primary Choice: [Library Name]**
    - **Rationale:** [Why this is the best fit]
    - **Confidence:** [High/Medium/Low]
    - **Best for:** [Specific use cases where it excels]
    - **Avoid if:** [Situations where it's not ideal]

    **Alternative: [Library Name]**
    - **When to choose:** [Scenarios where alternative is better]

    **Implementation Checklist**
    - [ ] Add dependency: `npm install [library]`
    - [ ] Review official getting started guide
    - [ ] Set up basic configuration
    - [ ] Create proof-of-concept implementation
    - [ ] Add tests for integration
    - [ ] Document usage patterns for team

    **Resources**
    - [Library 1 documentation](url)
    - [Library 2 documentation](url)
    - [Comparison article](url)
    - [Example implementation](url)

11. **Offer Follow-up Actions**
    - "Would you like me to create a spike plan to test the recommended library?"
    - "Should I research any specific aspect in more depth?"
    - "Would you like me to create a migration plan if switching from current solution?"
    - "Should I draft integration code for the recommended library?"

## Context Awareness

**When file is selected:**
- Focus on libraries that integrate with that file's patterns
- Consider existing patterns and conventions

**When code is selected:**
- Treat selection as the use case or problem to solve
- Find libraries that can replace or enhance selected code

**When in project root:**
- Consider project-wide library choices
- Evaluate impact on entire codebase

**When no context:**
- Ask for the specific use case or problem area

## Example Usage

### Example 1: Form Library Research
```
User: /scp-library-research form validation for React
Assistant: I'll research form validation libraries for React. Let me understand your needs:

1. What's the complexity of your forms? (simple contact forms vs complex multi-step wizards)
2. Do you need schema validation? (Zod, Yup, etc.)
3. Performance priority? (large forms, re-render concerns)
4. Team familiarity with any specific libraries?
5. Acceptable bundle size budget?

[Uses Tavily to find current popular React form libraries...]
[Uses Context7 to review official docs for React Hook Form, Formik, React Final Form...]
[Creates detailed comparison with code examples...]

**Recommendation: React Hook Form**
- Rationale: Best performance (uncontrolled), excellent TS support, Zod integration, minimal re-renders
- Bundle size: 8.6KB (vs Formik 38KB)
- DX: Excellent with intuitive API
```

### Example 2: State Management Research
```
User: [selects complex component] /scp-library-research state management
Assistant: I see you have a complex component with state management challenges. Let me research solutions.

Questions:
1. Just this component or app-wide state management?
2. Need for time-travel debugging or dev tools?
3. Server state involved or just client state?
4. Team's Redux experience level?

[Uses Serena to analyze current state patterns...]
[Uses Tavily to research modern state management approaches...]
[Compares Zustand, Jotai, Redux Toolkit, XState...]
```

### Example 3: Build Tool Research
```
User: /scp-library-research we need a faster build tool than webpack
Assistant: I'll research modern build tools that could replace Webpack. Let me understand the context:

1. What's your current build taking? (dev server start, production build time)
2. Framework? (React, Vue, vanilla, etc.)
3. Special requirements? (module federation, micro-frontends, etc.)
4. Team comfortable with configuration migration effort?
5. Must support IE11 or can use modern browsers only?

[Uses Tavily to research Vite, esbuild, Turbopack, Rspack...]
[Uses Context7 to review official migration guides...]
[Uses Serena to analyze current webpack config...]

**Decision Matrix shows Vite as top choice for React + modern browsers**
**Includes migration checklist with estimated 4-8 hours effort**
```

## MCP Tools Usage Priority

1. **Tavily** - Primary tool for discovering libraries and best practices
2. **Context7** - Access official documentation for candidate libraries
3. **Sequential Thinking** - Systematically compare options
4. **Serena** - Analyze integration with existing codebase
5. **Filesystem-with-morph** - (Not used - research only, no code changes)

## Output Format

- **Structured markdown** with clear sections and comparisons
- **Comparison tables** and decision matrices
- **Actionable checklist** for implementation
- **Interactive prompts** for next steps
- Code examples showing basic usage
- Links to documentation and resources
