# /scp-concept-explain

Provide comprehensive, in-depth explanations of programming concepts, patterns, architectures, or technical topics with practical examples.

## Workflow

### Phase 1: Topic Scoping (Before Execution)

1. **Clarify the Concept**
   - Ask what specific concept needs explanation
   - Identify the context (language, framework, domain)
   - Determine current understanding level (complete beginner vs gaps in knowledge)
   - Confirm specific aspects of interest or confusion

2. **Understand the Goal**
   - Ask why this concept is being explored (learning, implementing, debugging, etc.)
   - Identify if explanation is for self or teaching others
   - Determine preferred depth (overview vs deep dive)
   - Confirm if practical examples or theory is more valuable

3. **Gather Context**
   - Ask if there's specific code or use case to relate to
   - Identify related concepts already understood
   - Determine what analogies or comparisons would help
   - Confirm if comparison to alternatives is useful

### Phase 2: Research & Synthesis (During Execution)

4. **Research Comprehensive Information**
   - Use Tavily to find high-quality explanations and tutorials
   - Use Context7 to access official documentation and specifications
   - Find expert blog posts, videos, and authoritative sources
   - Identify common misconceptions and pitfalls
   - Show progress: "Researching comprehensive explanation for [concept]..."

5. **Gather Practical Examples**
   - Use Tavily to find real-world usage examples
   - Search for code samples and implementations
   - Find use cases and common scenarios
   - Identify good vs bad examples
   - Show progress: "Gathering practical examples..."

6. **Analyze Codebase Usage**
   - Use Serena to find if concept is already used in codebase
   - Identify existing examples to reference
   - Find opportunities to apply the concept
   - Document current usage patterns (if any)
   - Show progress: "Analyzing codebase for existing usage..."

7. **Structure Explanation Systematically**
   - Use Sequential Thinking to organize information logically
   - Build from fundamentals to advanced concepts
   - Identify prerequisite knowledge
   - Plan progression of examples
   - Show progress: "Structuring comprehensive explanation..."

### Phase 3: Explanation Development (During Execution)

8. **Create Layered Explanation**
   - Start with simple analogy or mental model
   - Build up to technical details
   - Include visual metaphors where helpful
   - Address common misconceptions explicitly
   - Show progress: "Developing layered explanation..."

9. **Develop Practical Examples**
   - Create simple illustrative examples
   - Progress to realistic use cases
   - Include anti-patterns and what to avoid
   - Show evolution from basic to advanced
   - Show progress: "Creating code examples..."

### Phase 4: Deliverables (After Execution)

10. **Generate Comprehensive Explanation**
    Output structured markdown with:

    **Concept Overview**
    - Name: [Concept name]
    - Category: [Pattern/Architecture/Language feature/etc.]
    - Related concepts: [List]
    - Prerequisites: [What you should know first]

    **The Simple Explanation** 🎯

    [1-2 paragraph explanation in plain language]

    **Real-World Analogy**

    [Relatable analogy that captures the essence]

    ---

    **The Technical Explanation** 🔧

    ### What It Is
    [Formal definition and technical description]

    ### Why It Exists
    - **Problem it solves:** [What pain point does this address]
    - **History:** [Brief context on how/why it was created]
    - **When to use:** [Appropriate scenarios]
    - **When NOT to use:** [Situations where it's overkill or wrong choice]

    ### How It Works
    [Step-by-step breakdown of the mechanism]

    1. [Step 1 with explanation]
    2. [Step 2 with explanation]
    3. [Step 3 with explanation]

    **Key Principles**
    - **Principle 1:** [Explanation]
    - **Principle 2:** [Explanation]
    - **Principle 3:** [Explanation]

    ---

    **Practical Examples** 💻

    ### Example 1: Basic Usage
    ```typescript
    // Simple, clear example showing the core concept
    // Well-commented to explain what's happening
    ```

    **What's happening:**
    - [Explanation of key parts]

    ### Example 2: Real-World Scenario
    ```typescript
    // More realistic example showing practical application
    ```

    **Why this works:**
    - [Explanation of benefits and design choices]

    ### Example 3: Advanced Pattern
    ```typescript
    // Advanced usage showing power and flexibility
    ```

    **Trade-offs:**
    - ✅ Benefits: [list]
    - ⚠️ Costs: [list]

    ---

    **Common Misconceptions** ❌

    ### Misconception 1: [Common wrong belief]
    **Reality:** [Correct understanding]
    **Why this matters:** [Impact of misunderstanding]

    ### Misconception 2: [Another common mistake]
    **Reality:** [Correct understanding]

    ---

    **Comparison with Alternatives** ⚖️

    | Aspect | [This Concept] | Alternative 1 | Alternative 2 |
    |--------|----------------|---------------|---------------|
    | Complexity | [rating] | [rating] | [rating] |
    | Use case | [description] | [description] | [description] |
    | Performance | [rating] | [rating] | [rating] |
    | Learning curve | [rating] | [rating] | [rating] |

    **When to choose [This Concept]:**
    - [Scenario 1]
    - [Scenario 2]

    **When to choose alternatives:**
    - Alternative 1: [Scenario]
    - Alternative 2: [Scenario]

    ---

    **In Your Codebase** 📁

    **Current usage:**
    - ✅ Found in: [file paths where it's used]
    - Examples: [brief description of how it's currently used]

    OR

    - ❌ Not currently used
    - **Opportunities:** [Where it could be beneficial]

    ---

    **Anti-Patterns** 🚫

    ### Anti-Pattern 1: [Common mistake]
    ```typescript
    // Code showing what NOT to do
    ```
    **Why it's bad:** [Explanation]
    **Instead do:**
    ```typescript
    // Correct approach
    ```

    ### Anti-Pattern 2: [Another common mistake]
    [Same structure]

    ---

    **Learning Path** 📚

    **If you're new to this:**
    1. Start with: [Resource or simpler concept]
    2. Then explore: [Next step]
    3. Practice by: [Hands-on exercise suggestion]

    **To deepen your understanding:**
    1. Read: [Advanced resource]
    2. Implement: [Challenge project]
    3. Compare: [Related pattern or approach]

    **Resources**
    - [Official documentation](url)
    - [Excellent tutorial or blog post](url)
    - [Video explanation](url)
    - [Interactive example or playground](url)

    ---

    **Quick Reference Card** 📋

    **Key Points:**
    - [Essential point 1]
    - [Essential point 2]
    - [Essential point 3]

    **When to use:** [Quick checklist]
    **When to avoid:** [Quick checklist]
    **Common gotcha:** [Main thing to watch out for]

11. **Offer Follow-up Actions**
    - "Would you like me to show you how to implement this in your codebase?"
    - "Should I explain related concepts ([concept A], [concept B])?"
    - "Would you like me to create a practical example for your specific use case?"
    - "Should I find more resources or examples for any particular aspect?"

## Context Awareness

**When file is selected:**
- Relate explanation to patterns in that file
- Show how concept applies to that specific code
- Suggest refactoring opportunities

**When code is selected:**
- Explain concept in context of selected code
- Show how selected code does or doesn't follow the pattern
- Provide refactored example

**When in project root:**
- Show project-wide applications
- Find examples throughout codebase
- Suggest architecture-level opportunities

**When no context:**
- Provide general explanation
- Use common scenarios for examples

## Example Usage

### Example 1: Design Pattern Explanation
```
User: /scp-concept-explain dependency injection
Assistant: I'll explain dependency injection comprehensively. Let me understand your context:

1. Have you encountered this in code or learning it from scratch?
2. What language/framework? (affects specific examples)
3. Specific aspect confusing? (the "why", the "how", or when to use it)
4. Need to implement it or just understand existing code?

[Uses Tavily to find excellent DI explanations...]
[Uses Context7 to check framework-specific DI patterns...]
[Uses Serena to find DI usage in codebase...]

**The Simple Explanation:**
Dependency Injection is like ordering at a restaurant instead of cooking yourself. You declare what you need (dependencies), and something else provides it to you.

**The Technical Explanation:**
Instead of a class creating its own dependencies (tight coupling), dependencies are "injected" from outside (loose coupling)...

[Provides layered explanation with examples progressing from simple to advanced...]
[Shows existing DI usage in their codebase...]
```

### Example 2: Language Feature Explanation
```
User: [selects async function] /scp-concept-explain how async/await really works
Assistant: I'll explain async/await in depth, focusing on this function you've selected.

Questions:
1. Comfortable with Promises, or should I explain those first?
2. Specific confusion? (error handling, execution flow, performance, etc.)
3. Need to understand internals or just practical usage?

[Uses Context7 for official JavaScript documentation...]
[Uses Tavily for visualization and mental models...]

**Real-World Analogy:**
async/await is like ordering food for delivery. You place the order (start async operation), do other things while waiting (non-blocking), and get notified when it arrives (await the result)...

[Shows how their selected function works step-by-step...]
[Explains event loop, microtasks, etc. with diagrams...]
```

### Example 3: Architecture Concept
```
User: /scp-concept-explain microservices vs monolith
Assistant: I'll explain these architectural patterns and help you understand the trade-offs.

Context questions:
1. Is this for a new project or considering migration?
2. Current team size and structure?
3. Specific concerns? (scaling, deployment, complexity, etc.)

[Uses Tavily to research modern architectural patterns...]
[Uses Sequential Thinking to create systematic comparison...]

**Comparison Table:**
[Detailed comparison of characteristics, trade-offs, use cases...]

**In Your Context:**
[Analyzes current architecture with Serena...]
[Provides specific recommendations based on project size, team, requirements...]
```

## MCP Tools Usage Priority

1. **Tavily** - Find high-quality explanations, tutorials, and examples
2. **Context7** - Access official documentation and specifications
3. **Sequential Thinking** - Structure complex explanations logically
4. **Serena** - Find examples and usage in existing codebase
5. **Filesystem-with-morph** - (Not used - explanation only)

## Output Format

- **Structured markdown** with progressive complexity
- **Code examples** from simple to advanced
- **Analogies and mental models** for clarity
- **Comparison tables** for related concepts
- **Interactive prompts** for deeper exploration
- Visual diagrams where helpful (ASCII or described)
- Links to authoritative resources
