# /scp-architecture-review

Review software architecture, design patterns, code organization, and structural decisions for maintainability and scalability.

## Workflow

### Phase 1: Architecture Scoping (Before Execution)

1. **Define Review Scope**
   - Ask what should be reviewed (entire project, specific module, feature architecture)
   - Identify architectural concerns or questions
   - Determine if reviewing existing architecture or planning new one
   - Confirm scope boundaries (backend, frontend, full-stack, etc.)

2. **Understand Context**
   - Ask about project goals and requirements
   - Identify scalability and performance requirements
   - Determine team size and expertise level
   - Confirm constraints (technical, timeline, resources)

3. **Set Review Focus**
   - Ask what architectural aspects matter most (scalability, maintainability, testability, etc.)
   - Identify known pain points or bottlenecks
   - Determine if comparing alternatives or reviewing current state
   - Confirm if looking for incremental improvements or major refactoring

### Phase 2: Architecture Analysis (During Execution)

4. **Map System Structure**
   - Use Serena to analyze codebase structure and organization
   - Identify modules, layers, and major components
   - Map dependencies and relationships
   - Document current architectural patterns
   - Show progress: "Mapping system architecture..."

5. **Analyze Architectural Patterns**
   - Use Sequential Thinking to identify design patterns in use
   - Evaluate pattern appropriateness and implementation
   - Check for consistency across codebase
   - Identify missing or misused patterns
   - Show progress: "Analyzing architectural patterns..."

6. **Research Best Practices**
   - Use Tavily to find modern architectural approaches
   - Use Context7 to check framework-recommended architectures
   - Research industry standards for similar systems
   - Find successful examples of similar architectures
   - Show progress: "Researching architectural best practices..."

7. **Evaluate Structural Quality**
   - Assess separation of concerns
   - Check modularity and coupling
   - Evaluate layer separation (presentation, business logic, data)
   - Review dependency direction and organization
   - Assess code reusability and DRYness
   - Show progress: "Evaluating structural quality..."

8. **Assess Scalability**
   - Identify scalability bottlenecks
   - Evaluate horizontal and vertical scaling potential
   - Check for single points of failure
   - Assess data access patterns
   - Review caching strategies
   - Show progress: "Assessing scalability characteristics..."

9. **Review Maintainability**
   - Evaluate code organization and discoverability
   - Check consistency in patterns and conventions
   - Assess testability of architecture
   - Review documentation and knowledge sharing
   - Identify technical debt and friction points
   - Show progress: "Reviewing maintainability aspects..."

### Phase 3: Assessment & Recommendations (During Execution)

10. **Compare Against Principles**
    - Check alignment with @PRINCIPLES.instructions.md
    - Evaluate SOLID principles at architecture level
    - Assess pragmatism vs dogmatism balance
    - Identify principle violations with significant impact
    - Show progress: "Evaluating against architectural principles..."

11. **Generate Improvement Plan**
    - Prioritize architectural improvements
    - Create phased refactoring approach
    - Identify quick wins vs long-term changes
    - Plan backwards compatibility approach
    - Show progress: "Creating improvement recommendations..."

### Phase 4: Deliverables (After Execution)

12. **Generate Architecture Review Report**
    Output structured markdown with:

    **Architecture Review Summary**
    - System reviewed: [project/module name]
    - Review date: [current date]
    - Scope: [what was reviewed]
    - Focus areas: [list]

    **Executive Summary**
    - **Overall Architecture Score:** [X/10]
    - **Strengths:** [Top 2-3 strengths]
    - **Key Concerns:** [Top 2-3 concerns]
    - **Recommended Actions:** [High-level priorities]

    ---

    **Current Architecture Overview**

    ### System Structure
    ```
    [ASCII diagram or description of major components and layers]
    ```

    ### Components Identified
    - **[Component 1]:** [Purpose and responsibilities]
    - **[Component 2]:** [Purpose and responsibilities]
    - **[Component 3]:** [Purpose and responsibilities]

    ### Current Patterns in Use
    - [Pattern 1] - [Where used]
    - [Pattern 2] - [Where used]
    - [Pattern 3] - [Where used]

    ### Technology Stack
    - Framework: [name and version]
    - Key libraries: [list]
    - Infrastructure: [description]

    ---

    **Detailed Assessment**

    ### Separation of Concerns
    **Score:** [X/10]

    **Strengths:**
    - ✅ [What's well separated]
    - ✅ [Good example of separation]

    **Concerns:**
    - ⚠️ [file_path] - [Mixed responsibilities issue]
    - ⚠️ [area] - [Coupling issue]

    **Recommendation:**
    [How to improve separation]

    ### Modularity & Coupling
    **Score:** [X/10]

    **Dependencies Analysis:**
    - Tight coupling found: [list of problematic dependencies]
    - Circular dependencies: [count and examples]
    - Module cohesion: [assessment]

    **Concerns:**
    - ⚠️ [Module A] tightly coupled to [Module B]
    - ⚠️ Circular dependency: [A → B → C → A]

    **Recommendation:**
    [How to reduce coupling and improve modularity]

    ### Layering & Organization
    **Score:** [X/10]

    **Current Layer Structure:**
    ```
    [Diagram or description of layers]
    ```

    **Strengths:**
    - ✅ [Well-structured layer]

    **Concerns:**
    - ⚠️ Layer violations: [examples of broken layer boundaries]
    - ⚠️ Missing layer: [what's missing]

    **Recommendation:**
    [How to improve layering]

    ### Scalability
    **Score:** [X/10]

    **Current Limitations:**
    - **Horizontal scaling:** [assessment]
    - **Vertical scaling:** [assessment]
    - **Database scaling:** [assessment]
    - **Caching strategy:** [assessment]

    **Bottlenecks Identified:**
    - 🚨 [Critical bottleneck 1]
    - ⚠️ [Potential bottleneck 2]

    **Recommendation:**
    [Scalability improvements]

    ### Testability
    **Score:** [X/10]

    **Current State:**
    - Unit test ease: [Easy/Moderate/Difficult]
    - Integration test ease: [Easy/Moderate/Difficult]
    - Mocking requirements: [Minimal/Moderate/Extensive]

    **Concerns:**
    - ⚠️ [Component] difficult to test due to [reason]
    - ⚠️ Tight coupling makes mocking complex

    **Recommendation:**
    [How to improve testability]

    ### Performance Architecture
    **Score:** [X/10]

    **Strengths:**
    - ✅ [Performance strength]

    **Concerns:**
    - ⚠️ [Performance concern with architectural impact]

    **Recommendation:**
    [Architectural changes for better performance]

    ### Security Architecture
    **Score:** [X/10]

    **Current Approach:**
    - Authentication: [description]
    - Authorization: [description]
    - Data protection: [description]

    **Concerns:**
    - 🚨 [Critical security architecture issue]
    - ⚠️ [Security improvement opportunity]

    **Recommendation:**
    [Security architecture improvements]

    ---

    **Design Patterns Review**

    ### Patterns Used Well ✅
    - **[Pattern 1]** in [location] - [Why it works well]
    - **[Pattern 2]** in [location] - [Why it works well]

    ### Patterns Misused ⚠️
    - **[Pattern 3]** in [location] - [What's wrong and how to fix]

    ### Missing Patterns 💡
    - **[Pattern 4]** would help with [problem] in [location]

    ---

    **Anti-Patterns Detected** ❌

    ### Anti-Pattern 1: [Name]
    **Location:** [where found]
    **Impact:** [how it hurts the system]
    **Refactoring effort:** [estimate]
    **Priority:** [High/Medium/Low]

    **Current:**
    ```
    [Description or diagram of anti-pattern]
    ```

    **Should be:**
    ```
    [Better approach]
    ```

    ---

    **Comparison with Best Practices**

    | Aspect | Current | Best Practice | Gap |
    |--------|---------|---------------|-----|
    | Layer separation | Partial | Clear boundaries | [description] |
    | Dependency management | Ad-hoc | DI container | [description] |
    | Error handling | Inconsistent | Centralized | [description] |
    | Data access | Mixed | Repository pattern | [description] |

    ---

    **Recommended Architecture Evolution**

    ### Phase 1: Foundation (Immediate) `[Estimate]`
    **Goal:** Fix critical issues and establish patterns

    - [ ] Task 1: [Fix critical anti-pattern] `[Estimate]`
      - Impact: [description]
      - Files affected: [list]

    - [ ] Task 2: [Establish clear layer boundaries] `[Estimate]`
      - Impact: [description]
      - Files affected: [list]

    ### Phase 2: Structural Improvements (Short-term) `[Estimate]`
    **Goal:** Reduce coupling and improve modularity

    - [ ] Task 3: [Extract shared logic into services] `[Estimate]`
    - [ ] Task 4: [Implement dependency injection] `[Estimate]`

    ### Phase 3: Scalability (Medium-term) `[Estimate]`
    **Goal:** Enable horizontal scaling

    - [ ] Task 5: [Refactor for stateless services] `[Estimate]`
    - [ ] Task 6: [Implement caching layer] `[Estimate]`

    ### Phase 4: Advanced Improvements (Long-term) `[Estimate]`
    **Goal:** Optimize for performance and maintainability

    - [ ] Task 7: [Consider microservices for [module]] `[Estimate]`
    - [ ] Task 8: [Implement event-driven patterns] `[Estimate]`

    ---

    **Alternative Architecture Approaches**

    ### Alternative 1: [Architecture name]
    **When to consider:**
    - [Scenario where this would be better]

    **Pros:**
    - [Advantage 1]
    - [Advantage 2]

    **Cons:**
    - [Disadvantage 1]
    - [Disadvantage 2]

    **Migration effort:** [Estimate]

    ### Alternative 2: [Architecture name]
    [Same structure]

    ---

    **Risk Assessment**

    ### High Risk Items 🚨
    - [Risk 1]: [Description and mitigation]
    - [Risk 2]: [Description and mitigation]

    ### Medium Risk Items ⚠️
    - [Risk 3]: [Description and mitigation]

    ---

    **Resources & References**
    - [Architecture pattern documentation](url)
    - [Best practices article](url)
    - [Example of similar architecture](url)

13. **Offer Follow-up Actions**
    - "Would you like me to create a detailed refactoring plan for [component]?"
    - "Should I design the architecture for [alternative approach]?"
    - "Would you like me to dive deeper into [specific architectural aspect]?"
    - "Should I create a migration plan to address the key concerns?"

## Context Awareness

**When file is selected:**
- Review file's architectural role
- Analyze file's dependencies and relationships
- Suggest architectural improvements for that component

**When code is selected:**
- Evaluate selected component's architecture
- Show how it fits (or doesn't fit) overall architecture
- Suggest better structural patterns

**When in project root:**
- Review entire project architecture
- Analyze high-level structure and organization
- Provide comprehensive architectural assessment

**When no context:**
- Ask for specific module or area to review

## Example Usage

### Example 1: Full Project Architecture Review
```
User: /scp-architecture-review
Assistant: I'll review the entire project architecture. Let me understand the context:

1. What type of system? (web app, API, microservices, etc.)
2. Current pain points or scaling challenges?
3. Team size and how fast is the codebase growing?
4. Any specific architectural concerns?

[Uses Serena to map entire codebase structure...]
[Uses Sequential Thinking to evaluate patterns systematically...]
[Uses Tavily to research modern architecture patterns...]

**Overall Architecture Score: 7/10**

**Key Findings:**
- Strong layer separation in backend
- Frontend lacking consistent state management pattern
- Some circular dependencies between modules
- Good testability overall

**Top 3 Recommendations:**
1. Introduce state management library (6h effort, high impact)
2. Break circular dependency in auth/user modules (4h effort, medium impact)
3. Extract shared validation into middleware (3h effort, quick win)

[Detailed assessment with phased improvement plan...]
```

### Example 2: Module Architecture Review
```
User: [selects /src/api folder] /scp-architecture-review
Assistant: I'll review the API module architecture.

Questions:
1. Is this REST, GraphQL, or mixed?
2. Any performance or scaling concerns?
3. How critical is this module (traffic level)?

[Uses Serena to analyze API module structure...]

**API Module Architecture Assessment:**

**Strengths:**
✅ Clear route organization
✅ Consistent middleware usage
✅ Good error handling patterns

**Concerns:**
⚠️ Business logic mixed with route handlers
⚠️ No clear service layer
⚠️ Tight coupling to database models

**Recommended Pattern: Service Layer + Repository**
[Shows refactoring to separate concerns...]
```

### Example 3: Architecture for New Feature
```
User: /scp-architecture-review I want to add real-time collaboration features
Assistant: I'll review the current architecture and recommend how to integrate real-time collaboration.

Let me understand:
1. What type of collaboration? (document editing, chat, presence, etc.)
2. Expected concurrent users?
3. Current architecture: REST API with [discovered stack]
4. Preference for WebSockets, SSE, or polling?

[Uses Serena to analyze current architecture...]
[Uses Tavily to research real-time collaboration architectures...]

**Current Architecture Compatibility: 6/10**

**Challenges:**
- Stateless API design conflicts with WebSocket connections
- No pub/sub infrastructure currently
- Database not optimized for real-time updates

**Recommended Architectural Changes:**
1. Add WebSocket layer (separate service or same server)
2. Introduce Redis for pub/sub and session management
3. Implement operational transformation or CRDT for conflict resolution

**Architecture Evolution Plan:**
[Phased approach to add real-time capabilities...]
```

## MCP Tools Usage Priority

1. **Serena** - Primary tool for mapping architecture and dependencies
2. **Sequential Thinking** - Systematically evaluate architectural decisions
3. **Tavily** - Research modern architectural patterns and approaches
4. **Context7** - Check framework-recommended architectures
5. **Filesystem-with-morph** - (Not used - analysis only, no changes)

## Output Format

- **Structured markdown** with clear assessment sections
- **ASCII diagrams** or descriptions of architecture
- **Scoring system** for objective assessment
- **Phased improvement plan** with estimates
- **Actionable checklist** for addressing issues
- **Interactive prompts** for follow-up
- Comparison tables for alternatives
- Risk assessment for proposed changes
