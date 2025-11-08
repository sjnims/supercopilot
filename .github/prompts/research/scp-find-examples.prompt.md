# /scp-find-examples

Find real-world code examples, implementation patterns, and reference implementations for specific use cases or technologies.

## Workflow

### Phase 1: Requirements Gathering (Before Execution)

1. **Clarify What to Find**
   - Ask what specific pattern, feature, or use case needs examples
   - Identify the technology stack or language
   - Determine the quality level needed (production vs tutorial examples)
   - Confirm scope (minimal example vs comprehensive implementation)

2. **Define Search Criteria**
   - Ask about specific characteristics wanted (TypeScript, tested, documented, etc.)
   - Identify complexity level (beginner-friendly vs advanced)
   - Determine if comparing multiple approaches or finding one good example
   - Confirm if open source examples or official examples preferred

3. **Understand Context**
   - Ask if this is for learning, reference, or adaptation
   - Identify any constraints (license, dependencies, framework version, etc.)
   - Determine if examples should match current project patterns
   - Confirm what aspects are most important to see

### Phase 2: Discovery (During Execution)

4. **Search for Examples**
   - Use Tavily to find high-quality code examples and implementations
   - Search GitHub repositories, official examples, and tutorial code
   - Look for production codebases using the pattern
   - Find examples from reputable sources and maintainers
   - Show progress: "Searching for examples of [pattern/feature]..."

5. **Access Official Examples**
   - Use Context7 to check official documentation for examples
   - Review framework/library starter templates
   - Find official code samples and snippets
   - Check API documentation for usage examples
   - Show progress: "Checking official documentation and examples..."

6. **Analyze Codebase Patterns**
   - Use Serena to find similar patterns in current codebase
   - Identify existing implementations to reference
   - Find internal examples and conventions
   - Document how similar problems are currently solved
   - Show progress: "Analyzing existing codebase patterns..."

### Phase 3: Evaluation (During Execution)

7. **Evaluate Example Quality**
   - Use Sequential Thinking to assess each example
   - Check code quality, clarity, and best practices
   - Verify examples are current and maintained
   - Assess completeness and documentation
   - Identify potential issues or anti-patterns
   - Show progress: "Evaluating example quality..."

8. **Filter and Curate**
   - Select 3-5 best examples with different approaches
   - Prioritize by relevance and quality
   - Identify unique aspects of each example
   - Note what each example does particularly well
   - Show progress: "Curating top examples..."

9. **Adapt to Project Context**
   - Consider how examples fit project patterns
   - Identify what needs adaptation
   - Check alignment with @PRINCIPLES.instructions.md
   - Note any incompatibilities or concerns
   - Show progress: "Adapting examples to project context..."

### Phase 4: Deliverables (After Execution)

10. **Generate Examples Report**
    Output structured markdown with:

    **Search Summary**
    - Looking for: [pattern/feature/use case]
    - Technology: [stack/language/framework]
    - Examples found: [count]
    - Criteria: [quality requirements]

    ---

    **Example 1: [Name/Description]** ⭐ Recommended

    **Source:** [Repository/Article/Docs]
    - License: [License type]
    - Last updated: [Date]
    - Stars/Popularity: [If GitHub repo]
    - Language: [Language/Framework]

    **What it demonstrates:**
    - [Key aspect 1]
    - [Key aspect 2]
    - [Key aspect 3]

    **Code Sample:**
    ```typescript
    // Relevant portion of the example
    // Well-commented to highlight key patterns
    ```

    **Strengths:**
    - ✅ [What this example does well]
    - ✅ [Another strength]
    - ✅ [Another strength]

    **Considerations:**
    - ⚠️ [Potential issue or adaptation needed]
    - ⚠️ [Another consideration]

    **Adaptation notes:**
    - [How to adapt for your project]
    - [What to change or customize]

    **Full source:** [Link to complete example]

    ---

    **Example 2: [Name/Description]**

    **Source:** [Repository/Article/Docs]
    [Same structure as Example 1]

    **What's different from Example 1:**
    - [Key difference and why it matters]

    ---

    **Example 3: [Name/Description]**
    [Same structure]

    ---

    **Comparison Overview**

    | Aspect | Example 1 | Example 2 | Example 3 |
    |--------|-----------|-----------|-----------|
    | Complexity | Simple | Medium | Advanced |
    | Completeness | Basic | Full-featured | Comprehensive |
    | TypeScript | ✅ | ✅ | ❌ |
    | Tests | ❌ | ✅ | ✅ |
    | Documentation | Good | Excellent | Fair |
    | Best for | Learning | Production use | Advanced patterns |

    **Which to choose:**
    - **Starting out?** Use Example 1 - simplest and clearest
    - **Production code?** Use Example 2 - most complete and tested
    - **Advanced patterns?** Use Example 3 - shows sophisticated techniques

    ---

    **In Your Codebase** 📁

    **Existing similar implementations:**
    ```
    [file_path]:[line_number]
    ```
    ```typescript
    // Your existing code that's similar
    ```

    **How examples compare to current approach:**
    - [Similarity or difference 1]
    - [Similarity or difference 2]

    **Integration considerations:**
    - [How example patterns fit with existing code]
    - [What would need to change]

    ---

    **Implementation Guide** 🛠️

    **If adapting Example [X]:**

    1. **Setup**
       ```bash
       # Commands to install dependencies, etc.
       ```

    2. **Core implementation**
       ```typescript
       // Adapted code for your project
       ```

    3. **Integration points**
       - [Where this fits in your codebase]
       - [What files to modify]

    4. **Testing**
       ```typescript
       // Test examples
       ```

    **Checklist:**
    - [ ] Review full source code `[Estimate]`
    - [ ] Adapt to project patterns `[Estimate]`
    - [ ] Add tests `[Estimate]`
    - [ ] Update documentation `[Estimate]`
    - [ ] Code review with team `[Estimate]`

    ---

    **Additional Resources**
    - [Official documentation](url)
    - [Tutorial or guide](url)
    - [Related examples](url)
    - [Discussion or blog post](url)

    **Related patterns to explore:**
    - [Related pattern 1]
    - [Related pattern 2]

11. **Offer Follow-up Actions**
    - "Would you like me to implement the recommended example in your codebase?"
    - "Should I search for examples of a related pattern?"
    - "Would you like me to create a hybrid approach combining aspects of multiple examples?"
    - "Should I explain any specific aspect of these examples in depth?"

## Context Awareness

**When file is selected:**
- Find examples relevant to that file's domain
- Show how examples could integrate with that file
- Compare to patterns in that file

**When code is selected:**
- Find examples that solve the same problem
- Show alternative implementations
- Compare approaches to selected code

**When in project root:**
- Find examples matching project's tech stack
- Consider architectural consistency
- Show project-wide integration

**When no context:**
- Find general examples
- Ask for more specific context

## Example Usage

### Example 1: Finding Implementation Examples
```
User: /scp-find-examples authentication with refresh tokens
Assistant: I'll find examples of authentication with refresh token implementation. Let me clarify:

1. What stack? (Node.js/Express, Next.js, etc.)
2. Using JWT or another token format?
3. Need mobile app support or web only?
4. Prefer minimal example or full-featured?

[Uses Tavily to search for refresh token implementations...]
[Uses Context7 to check framework-specific auth patterns...]

**Example 1: Express + JWT Refresh Tokens** ⭐ Recommended
Source: [Popular auth tutorial repository]
- Clean separation of auth logic
- Secure httpOnly cookie handling
- Comprehensive error handling

[Shows code with detailed annotations...]
[Compares 3 different approaches...]
```

### Example 2: Finding Pattern Examples
```
User: [selects React component] /scp-find-examples compound component pattern
Assistant: I'll find examples of the compound component pattern in React.

Questions:
1. TypeScript required?
2. Need examples with hooks or class components ok?
3. Complexity level? (simple vs feature-rich)

[Uses Tavily to find compound component examples...]
[Uses Context7 for React documentation examples...]
[Uses Serena to check if pattern exists in codebase...]

**Found 3 excellent examples:**
1. Reach UI's Tabs component (production-grade)
2. React documentation example (simple, clear)
3. Your existing Modal component (already using this pattern!)

[Shows each with analysis...]
```

### Example 3: Finding Library Usage Examples
```
User: /scp-find-examples using Zod with React Hook Form
Assistant: I'll find real-world examples of Zod + React Hook Form integration.

Context:
1. What type of forms? (simple contact vs complex multi-step)
2. Need validation error display patterns too?
3. TypeScript inference examples needed?

[Uses Tavily to find integration examples...]
[Uses Context7 for official docs from both libraries...]

**Example 1: Official React Hook Form + Zod Example**
[Shows official integration...]

**Example 2: Production Form with Complex Validation**
[Shows advanced usage from popular open source project...]

**Example 3: Type-safe Form Builder Pattern**
[Shows TypeScript-first approach with full inference...]

**Adaptation Guide:**
[Shows how to integrate with existing form patterns in codebase...]
```

## MCP Tools Usage Priority

1. **Tavily** - Primary tool for finding code examples and implementations
2. **Context7** - Access official documentation examples
3. **Serena** - Find similar patterns in existing codebase
4. **Sequential Thinking** - Evaluate and compare example quality
5. **Filesystem-with-morph** - (Not used - research only, no changes)

## Output Format

- **Structured markdown** with clear example sections
- **Annotated code samples** showing key patterns
- **Comparison tables** for multiple examples
- **Actionable integration guide** if implementing
- **Interactive prompts** for next steps
- Links to full source code and documentation
