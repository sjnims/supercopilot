# /scp-feature-plan

Plan a new feature from concept to implementation with comprehensive analysis and structured breakdown.

## Workflow

### Phase 1: Context Discovery (Before Execution)

1. **Clarify Requirements**
   - Ask clarifying questions about the feature's purpose and goals
   - Identify target users and use cases
   - Determine success criteria and constraints
   - Confirm scope and boundaries

2. **Confirm Analysis Scope**
   - Identify which files/modules need to be analyzed
   - Confirm the depth of analysis required
   - Ask if there are specific areas of concern

### Phase 2: Research & Analysis (During Execution)

3. **Research Best Practices**
   - Use Tavily to find modern approaches for similar features
   - Use Context7 to check official documentation for relevant libraries
   - Document industry standards and patterns
   - Show progress: "Researching best practices for [feature type]..."

4. **Analyze Current Architecture**
   - Use Serena to map relevant code structure and symbols
   - Identify existing patterns and conventions in the codebase
   - Find similar existing features for consistency
   - Document architectural constraints
   - Show progress: "Analyzing codebase architecture..."

5. **Evaluate Implementation Approaches**
   - Use Sequential Thinking to compare multiple approaches
   - Consider trade-offs (complexity, maintainability, performance)
   - Align with principles from @PRINCIPLES.instructions.md
   - Identify dependencies and integration points
   - Show progress: "Evaluating implementation strategies..."

### Phase 3: Planning & Design (During Execution)

6. **Create Feature Breakdown**
   - Break feature into phases or milestones
   - Identify tasks for each phase with estimates
   - Determine order of implementation
   - Highlight risks and unknowns
   - Show progress: "Creating detailed task breakdown..."

7. **Design Technical Approach**
   - Define data structures and interfaces
   - Plan file/module organization
   - Identify new dependencies needed
   - Consider testing strategy
   - Document security considerations

8. **Plan Integration Points**
   - Map how feature integrates with existing code
   - Identify files that need modification
   - Plan backwards compatibility approach
   - Consider migration or rollout strategy

### Phase 4: Deliverables (After Execution)

9. **Generate Comprehensive Plan**
   Output structured markdown with:

   **Feature Overview**
   - Purpose and goals
   - Target users and use cases
   - Success criteria

   **Research Findings**
   - Best practices discovered
   - Relevant documentation
   - Similar implementations

   **Technical Approach**
   - Chosen architecture and rationale
   - Key design decisions
   - Trade-offs considered

   **Implementation Plan**
   - [ ] Phase 1 tasks (with estimates)
   - [ ] Phase 2 tasks (with estimates)
   - [ ] Phase 3 tasks (with estimates)

   **Integration Requirements**
   - Files to modify
   - New files to create
   - Dependencies to add

   **Risks & Considerations**
   - Technical risks
   - Security considerations
   - Performance implications

   **Testing Strategy**
   - Unit test approach
   - Integration test needs
   - Manual testing checklist

10. **Offer Follow-up Actions**
    - "Would you like me to create implementation tasks for any specific phase?"
    - "Should I research any particular aspect in more depth?"
    - "Would you like me to start with a spike for [risky component]?"

## Context Awareness

**When file is selected:**
- Plan feature relative to the selected file/module
- Focus on integration with that specific area

**When code is selected:**
- Treat selection as example or starting point
- Plan feature that extends or modifies selected code

**When in project root:**
- Plan feature at project level
- Consider full application architecture

**When no context:**
- Ask for the feature area or starting point

## Example Usage

### Example 1: Planning User Authentication Feature
```
User: /scp-feature-plan
Assistant: I'll help you plan this feature. Let me ask a few questions:
1. What type of authentication are you planning? (OAuth, JWT, session-based, etc.)
2. What are the main use cases? (login, registration, password reset, etc.)
3. Are there existing auth patterns in the codebase I should follow?
4. What's the scope? (just backend, full-stack, including social auth, etc.)

[After getting answers, proceeds with research and analysis...]
```

### Example 2: Planning with File Context
```
User: [selects src/api/users.ts] /scp-feature-plan add user profile customization
Assistant: I see you've selected the users API file. I'll plan a user profile customization feature that integrates here.

Let me clarify a few things:
1. What aspects of the profile should be customizable? (avatar, bio, preferences, etc.)
2. Should this be real-time or saved changes?
3. Any specific UI/UX requirements?

[Proceeds with Serena analysis of users.ts and related files, then creates plan...]
```

### Example 3: Complex Feature Planning
```
User: /scp-feature-plan implement real-time collaborative editing
Assistant: That's a complex feature! Let me break this down carefully.

Before I start, I need to understand:
1. How many concurrent users do you expect?
2. What type of content will be edited? (text, code, documents, etc.)
3. Do you have preferences for the sync approach? (OT, CRDT, server-authoritative)
4. Are there latency or offline requirements?

[Uses Tavily for research on collaborative editing approaches...]
[Uses Sequential Thinking to evaluate OT vs CRDT...]
[Uses Serena to analyze current editor implementation...]
[Creates comprehensive multi-phase implementation plan...]
```

## MCP Tools Usage Priority

1. **Tavily** - Research modern approaches and best practices
2. **Context7** - Check official library documentation
3. **Serena** - Analyze codebase structure and patterns
4. **Sequential Thinking** - Evaluate approaches and trade-offs
5. **Filesystem-with-morph** - (Not used - planning only, no code changes)

## Output Format

- **Structured markdown** with clear headings and sections
- **Actionable checklists** for implementation tasks
- **Interactive prompts** for follow-up actions
- Code examples where helpful
- Links to research sources
