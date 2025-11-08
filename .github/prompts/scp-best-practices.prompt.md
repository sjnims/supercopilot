# /scp-best-practices

Discover and document best practices, patterns, and conventions for specific technologies, architectures, or development approaches.

## Workflow

### Phase 1: Topic Clarification (Before Execution)

1. **Define the Scope**
   - Ask what specific area or pattern needs best practices
   - Identify the context (language, framework, architecture, etc.)
   - Determine the goal (learning, improving existing code, or planning new code)
   - Confirm experience level (beginner, intermediate, advanced)

2. **Understand Current State**
   - Ask about current approach or implementation (if applicable)
   - Identify pain points or specific concerns
   - Determine if comparing multiple approaches or deep-diving one
   - Confirm if project-specific or general best practices

3. **Set Expectations**
   - Ask what format is most useful (checklist, guide, examples, etc.)
   - Determine depth needed (quick overview vs comprehensive guide)
   - Identify if code examples are needed
   - Confirm if this is for documentation or implementation

### Phase 2: Research & Discovery (During Execution)

4. **Research Current Best Practices**
   - Use Tavily to find recent articles, guides, and expert opinions
   - Search for official style guides and recommendations
   - Find community consensus and common patterns
   - Identify industry standards and specifications
   - Show progress: "Researching current best practices for [topic]..."

5. **Access Official Documentation**
   - Use Context7 to review official framework/library documentation
   - Check for official best practices or patterns guides
   - Review API documentation for recommended usage
   - Find official examples and starter templates
   - Show progress: "Reviewing official documentation..."

6. **Analyze Existing Implementation**
   - Use Serena to analyze current codebase patterns (if applicable)
   - Identify what's already being done well
   - Find inconsistencies or anti-patterns
   - Document current conventions
   - Show progress: "Analyzing existing codebase patterns..."

### Phase 3: Synthesis & Analysis (During Execution)

7. **Evaluate Practices Systematically**
   - Use Sequential Thinking to organize findings
   - Categorize practices by area (security, performance, maintainability, etc.)
   - Distinguish must-do vs nice-to-have practices
   - Identify trade-offs and when to break rules
   - Show progress: "Synthesizing best practices..."

8. **Align with Project Principles**
   - Cross-reference with @PRINCIPLES.instructions.md
   - Identify practices already followed
   - Find gaps in current approach
   - Note any conflicts or adjustments needed
   - Show progress: "Aligning with project principles..."

9. **Create Actionable Guidance**
   - Organize practices by priority and category
   - Add rationale for each practice (the "why")
   - Include anti-patterns to avoid
   - Provide concrete examples
   - Show progress: "Creating actionable guidance..."

### Phase 4: Deliverables (After Execution)

10. **Generate Best Practices Guide**
    Output structured markdown with:

    **Best Practices Overview**
    - Topic: [specific area]
    - Context: [language/framework/architecture]
    - Last updated: [current date]
    - Sources: [key references]

    **Critical Practices** ⚠️ (Must follow)

    ### 1. [Practice Name]
    **Why:** [Rationale and benefits]

    **Do:**
    ```typescript
    // Good example showing the practice
    ```

    **Don't:**
    ```typescript
    // Anti-pattern to avoid
    ```

    **Checklist:**
    - [ ] [Specific action to implement this practice]
    - [ ] [Another action]

    ---

    ### 2. [Practice Name]
    [Same structure]

    **Important Practices** ✅ (Strongly recommended)

    ### 3. [Practice Name]
    [Same structure as above]

    **Helpful Practices** 💡 (Nice to have)

    ### 7. [Practice Name]
    [Same structure]

    **Anti-Patterns to Avoid** ❌

    ### [Anti-Pattern Name]
    **Why it's bad:** [Explanation]

    **Instead do:**
    ```typescript
    // Better approach
    ```

    **Common scenarios:** [When this anti-pattern appears]

    ---

    **Trade-offs & Context** ⚖️

    ### When to break the rules
    - [Practice X] can be skipped if [specific context]
    - [Practice Y] matters less in [specific scenario]

    ### Performance vs Maintainability
    - [Guidance on balancing trade-offs]

    **Current Project Status**

    ✅ **Already following:**
    - [Practice 1] - [evidence from codebase]
    - [Practice 2] - [evidence from codebase]

    ⚠️ **Could improve:**
    - [Practice 3] - [specific gaps found]
    - [Practice 4] - [specific gaps found]

    ❌ **Not currently following:**
    - [Practice 5] - [impact and priority]

    **Implementation Roadmap**

    **Phase 1: Quick Wins** (can do immediately)
    - [ ] [Action item] `[Estimate]`
    - [ ] [Action item] `[Estimate]`

    **Phase 2: Incremental Improvements** (for new code)
    - [ ] [Action item] `[Estimate]`
    - [ ] [Action item] `[Estimate]`

    **Phase 3: Refactoring** (update existing code)
    - [ ] [Action item] `[Estimate]`
    - [ ] [Action item] `[Estimate]`

    **Resources & Further Reading**
    - [Official style guide](url)
    - [Key article or blog post](url)
    - [Video tutorial or conference talk](url)
    - [Example repository](url)

    **Team Onboarding**
    - **Key principle:** [Most important takeaway]
    - **Common mistake:** [What to watch out for]
    - **When in doubt:** [Rule of thumb]

11. **Offer Follow-up Actions**
    - "Would you like me to create linting rules to enforce these practices?"
    - "Should I refactor specific code to follow these best practices?"
    - "Would you like me to dive deeper into any specific practice?"
    - "Should I create a code review checklist based on these practices?"

## Context Awareness

**When file is selected:**
- Focus on best practices for that file's domain
- Analyze file against best practices
- Provide file-specific recommendations

**When code is selected:**
- Evaluate selected code against best practices
- Show exactly what could be improved
- Provide refactored examples

**When in project root:**
- Provide project-level best practices
- Analyze overall codebase patterns
- Recommend architecture-level practices

**When no context:**
- Ask for the specific area or topic

## Example Usage

### Example 1: React Best Practices
```
User: /scp-best-practices React component design
Assistant: I'll research React component design best practices. Let me understand your needs:

1. Using class components or function components?
2. TypeScript or JavaScript?
3. Any specific concerns? (performance, testability, reusability)
4. Experience level of the team?

[Uses Tavily to find current React best practices...]
[Uses Context7 to review official React documentation...]
[Uses Serena to analyze existing React components in codebase...]

**Critical Practices:**
1. Always use TypeScript with proper prop types
2. Keep components small and focused (Single Responsibility)
3. Use composition over prop drilling

**Current Project Status:**
✅ Already following: TypeScript usage, functional components
⚠️ Could improve: Some components > 300 lines, prop drilling in forms
❌ Not following: Consistent error boundary usage

[Provides detailed guide with examples...]
```

### Example 2: API Design Best Practices
```
User: [selects API route file] /scp-best-practices REST API design
Assistant: I'll analyze this API file and provide REST API best practices.

Questions:
1. Is this a public API or internal only?
2. Versioning strategy preference?
3. Any specific concerns? (performance, security, documentation)

[Uses Tavily to research REST API standards...]
[Uses Context7 to check framework-specific best practices...]
[Uses Serena to analyze all API routes in project...]

**Critical Practices:**
1. Use proper HTTP methods (GET, POST, PUT, PATCH, DELETE)
2. Return appropriate status codes
3. Implement proper error handling with consistent structure

**Anti-Patterns Found in Codebase:**
❌ Using GET requests for state-changing operations (found in 3 routes)
❌ Inconsistent error response format

[Provides specific fixes for this file...]
```

### Example 3: Security Best Practices
```
User: /scp-best-practices authentication security
Assistant: I'll research authentication security best practices. This is critical, so let me be thorough:

1. What auth method are you using? (JWT, session, OAuth, etc.)
2. Handling passwords, tokens, or both?
3. Compliance requirements? (GDPR, SOC2, etc.)
4. Mobile clients or web only?

[Uses Tavily to research OWASP authentication recommendations...]
[Uses Context7 for framework-specific security guides...]
[Uses Sequential Thinking to prioritize security practices...]

**Critical Practices (Security):**
1. Never store passwords in plain text (use bcrypt/argon2)
2. Implement rate limiting on auth endpoints
3. Use httpOnly, secure cookies for tokens
4. Implement CSRF protection
5. Use strong password requirements

**Implementation Checklist:**
- [ ] Audit current password hashing (upgrade to argon2) `2h`
- [ ] Add rate limiting middleware `1h`
- [ ] Update cookie settings `30m`
- [ ] Implement CSRF tokens `2h`
- [ ] Add password strength validator `1h`

[Provides detailed security guide with code examples...]
```

## MCP Tools Usage Priority

1. **Tavily** - Primary tool for discovering current best practices and expert opinions
2. **Context7** - Access official documentation and style guides
3. **Serena** - Analyze existing codebase patterns and compliance
4. **Sequential Thinking** - Organize and prioritize practices systematically
5. **Filesystem-with-morph** - (Not used - research/analysis only)

## Output Format

- **Structured markdown** with clear priority levels
- **Code examples** showing do's and don'ts
- **Actionable checklists** for implementation
- **Interactive prompts** for next steps
- Current project status assessment
- Links to authoritative sources
