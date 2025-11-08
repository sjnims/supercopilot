---
description: 'Core software engineering principles for VSCode Copilot to follow when writing, reviewing, and refactoring code.'
---

# Software Engineering Principles for VSCode Copilot

This document defines pragmatic principles for writing software that works, ships, and doesn't make you miserable. These aren't commandments from on high—they're hard-won insights from building real software. Use them as tools for thought, not as religious dogma.

**Critical Mindset**: Every principle has a context where it shines and contexts where it fails. Your job is to recognize the difference. When someone tells you to always follow a principle, run the other way.

---

## 🎯 Core Design Principles

### SOLID Principles (Use With Skepticism)

SOLID can be useful, but it's also the source of tremendous over-engineering. These principles emerged from statically-typed, enterprise Java codebases. They may not apply to your context. Use them when they help; ignore them when they hurt.

**The Danger**: SOLID zealots create layers of abstraction "just in case" you might need flexibility later. This is speculative generality—writing code for problems you don't have yet. You'll pay the cost in complexity now for benefits that may never materialize.

| Principle | What It Says | When to Use It | When to Ignore It |
|-----------|-------------|----------------|-------------------|
| **Single Responsibility Principle (SRP)** | A class should have one reason to change | When a class is doing obviously unrelated things | When splitting creates artificial separation and forces you through unnecessary indirection |
| **Open/Closed Principle (OCP)** | Open for extension, closed for modification | When you have a stable abstraction with predictable variations | When you're adding a feature that clearly belongs in the existing code. Just modify it! |
| **Liskov Substitution Principle (LSP)** | Subtypes must be substitutable for their base types | When using inheritance hierarchies | When inheritance isn't the right tool anyway. Prefer composition. |
| **Interface Segregation Principle (ISP)** | Don't force clients to depend on methods they don't use | When you have fat interfaces | When you're creating interfaces just to satisfy some abstract principle |
| **Dependency Inversion Principle (DIP)** | Depend on abstractions, not concretions | When you need genuine flexibility | When the abstraction is more complex than the code it's "protecting" |

**Bottom Line**: Don't create abstractions until you have concrete use cases for them. Write the code that solves today's problem. Refactor when you actually need the flexibility.

### DRY (Don't Repeat Yourself) - But Don't Go Crazy

**Principle**: Avoid duplication of knowledge, not just code.

**The Nuance**: DRY doesn't mean eliminating every line that looks similar. Sometimes repetition is fine, even good. The real question: are you duplicating knowledge or just coincidentally similar code?

**When to Apply**:
- You're copying business logic that will change together
- You're maintaining the same data structure or algorithm in multiple places
- Changes to one copy mean changes to all copies

**When to Resist**:
- Similar-looking code that solves different problems
- Premature abstraction before you understand the pattern
- Creating baroque abstractions to avoid three lines of duplication
- Test code (tests can be "moist"—some repetition is fine)

**The Rule of Three**: Don't abstract until you've written it three times. Then you understand the real pattern.

**Remember**: Duplication is better than the wrong abstraction. It's easier to extract commonality from duplicated code than to untangle a premature abstraction.

### KISS (Keep It Simple, Stupid) - This One Actually Matters

**Principle**: Simple solutions beat clever ones. Every time.

**Why It Matters**: Complex code is expensive. It's expensive to write, expensive to maintain, expensive to debug, and expensive to modify. Simplicity is a competitive advantage.

**What Simple Means**:
- **Obvious**: Someone unfamiliar with the code can understand it quickly
- **Direct**: The code does what it looks like it does
- **Minimal**: No unnecessary layers, abstractions, or indirection
- **Boring**: Uses familiar patterns, not exotic cleverness

**How to Keep It Simple**:
- Write the straightforward solution first
- Resist the urge to show off with clever code
- Question every abstraction: does it earn its complexity?
- Don't solve problems you don't have
- Prefer clarity over performance until performance actually matters
- When debugging is twice as hard as writing, clever code guarantees you're not smart enough to debug your own work

**Remember**: Simplicity is the ultimate sophistication. If you can't explain your solution to a junior developer, it's probably too complicated.

### YAGNI (You Aren't Gonna Need It) - Seriously, You Don't

**Principle**: Don't build it until you need it. Not when you think you might need it. When you actually need it.

**Why This Matters**: Speculative features:
- Take time to build
- Add complexity to the codebase
- Need to be maintained forever
- Usually turn out wrong anyway (you didn't have the real requirements yet)
- Often never get used

**Examples of YAGNI Violations**:
- "We might need to support multiple databases" (you don't)

- "We might need to support multiple databases" (you don't)
- "Let's make this pluggable" (for the one implementation you have)
- Building a configuration system for two values
- Creating an abstraction layer for a single concrete implementation

**The YAGNI Promise**: When you actually do need that flexibility, refactoring working code is easier than maintaining speculative architecture.

**Action**: Delete that code you're keeping "just in case." It's in version control if you actually need it.

---

## 📐 Architecture & Structure Principles

### The Majestic Monolith - Start Here

**Principle**: Default to integrated systems. Microservices are for companies with microservice-scale problems.

**Why Monoliths Win**:
- **Simpler deployment**: One thing to deploy, not 47
- **Easier debugging**: The call stack is actually your call stack
- **Better performance**: No network calls between modules
- **Shared database**: Transactions work, joins work, consistency works
- **Less operational complexity**: One log to check, one thing to monitor

**When You Might Need Microservices**:
- You're Amazon or Netflix (you're probably not)
- You have independent teams that truly can't coordinate
- You have genuinely different scaling requirements for different parts
- You're willing to pay the distributed systems tax

**The Truth**: Most systems that "need" microservices are suffering from organizational dysfunction, not technical limitations. Fix your organization, not your architecture.

**Start With**: A well-structured monolith. Add services only when the monolith presents clear, specific problems that services actually solve.

### Convention Over Configuration

**Principle**: Make sensible defaults the path of least resistance.

**Guidelines**:
- Provide smart defaults that work for 80% of cases
- Make the common case trivial, the uncommon case possible
- Don't force configuration for things that should "just work"
- Standardize project structure and naming
- Reduce decision fatigue for developers
- Configuration is a burden—minimize it

**Example**: If every Rails app puts models in `app/models`, you don't need to configure where models go. Convention wins.

### Separation of Concerns

**Principle**: Different concerns should live in different places. But don't take this to extremes.

**Guidelines**:
- Group related functionality together
- Keep business logic separate from infrastructure
- Organize by feature/domain when possible
- Don't separate things just because they're different "types"
- Co-locate what changes together

**Warning**: Separation of concerns doesn't mean maximal separation. Sometimes integration is better than purity.

### Encapsulation

**Principle**: Bundle data and methods that operate on that data within a single unit, hiding internal details.

**Guidelines**:
- Hide implementation details behind clear interfaces
- Expose only what's necessary through public APIs
- Use access modifiers appropriately (private, protected, public)
- Protect object invariants
- Minimize coupling between components

### Composition Over Inheritance

**Principle**: Favor object composition over class inheritance to achieve code reuse.

**Guidelines**:
- Use "has-a" relationships instead of "is-a" when appropriate
- Prefer dependency injection and interfaces
- Avoid deep inheritance hierarchies
- Consider mixins, traits, or interfaces for shared behavior
- Composition provides more flexibility and testability

### Law of Demeter (Principle of Least Knowledge)

**Principle**: A unit should have limited knowledge about other units and only talk to its immediate friends.

**Guidelines**:
- Don't chain method calls: Avoid `a.getB().getC().doSomething()`
- Each method should only call:
  - Methods on the same object
  - Methods on objects passed as parameters
  - Methods on objects it creates
  - Methods on directly held instance variables
- Reduces coupling and improves maintainability

### Minimize Coupling, Maximize Cohesion

**Coupling**: The degree of interdependence between modules.
**Cohesion**: How closely related the responsibilities of a module are.

**Guidelines**:
- **Low Coupling**: Modules should be independent
  - Use interfaces and abstraction
  - Avoid global state
  - Use dependency injection
- **High Cohesion**: Related functionality should be grouped together
  - Functions in a module should serve a common purpose
  - Avoid mixing unrelated responsibilities

---

## ✨ Code Quality Principles

### Readability and Clarity

**Principle**: Code is read far more often than it's written. Optimize for human understanding.

**Guidelines**:
- Use descriptive, meaningful names for variables, functions, and classes
- Write self-documenting code that explains its intent
- Keep functions and methods short and focused (typically < 20-30 lines)
- Avoid deep nesting (max 3-4 levels)
- Use consistent formatting and style
- Add comments only when code cannot be self-explanatory
- Explain the "why" not the "what" in comments

### Explicit Over Implicit

**Principle**: Be explicit about intentions, dependencies, and behavior.

**Guidelines**:
- Prefer explicit parameter passing over global state
- Make dependencies visible in function signatures
- Avoid "magic" numbers or strings—use named constants
- Be explicit about error handling
- Avoid implicit type conversions where they might cause confusion

### Fail Fast

**Principle**: Detect and report errors as early as possible.

**Guidelines**:
- Validate inputs at the beginning of functions
- Use assertions to catch programming errors during development
- Throw exceptions for exceptional conditions
- Don't silently ignore errors
- Return early on invalid conditions
- Use type systems to catch errors at compile time

### Defensive Programming

**Principle**: Assume the worst and protect against it.

**Guidelines**:
- Validate all external inputs
- Check preconditions and postconditions
- Handle edge cases explicitly
- Use null checks and optional types
- Implement proper error handling
- Don't trust data from external sources
- Log important state changes and errors

### Immutability When Possible

**Principle**: Prefer immutable data structures and pure functions.

**Guidelines**:
- Use `const` or `final` by default
- Avoid mutating shared state
- Return new objects instead of modifying existing ones
- Prefer pure functions without side effects
- Immutability makes code easier to reason about and test

---

## 🧪 Testing Principles

### Test Pragmatically, Not Dogmatically

**Principle**: Write tests that give you confidence, not tests that make you feel virtuous.

**The Truth About TDD**: Test-Driven Development can be useful, but TDD zealotry leads to test-induced design damage. Don't let your tests dictate bad architecture.

**What to Test**:
- Critical business logic
- Complex algorithms
- Edge cases and error conditions
- Things that break often
- Public APIs and interfaces

**What Not to Obsess Over**:
- 100% coverage (it's a vanity metric)
- Testing trivial getters/setters
- Every single private method
- Tests that just duplicate the implementation

**Test-Induced Design Damage**: When you contort your design just to make testing easier, you're doing it wrong. If testing requires extensive mocking and indirection (hexagonal architecture, dependency injection everywhere), your tests are harming your design.

### Write Tests After You Understand the Problem

**Principle**: Write tests when they're most valuable, which is often after you've written working code.

**The Reality**:
1. Write the code that solves the problem
2. Get it working
3. Add tests for confidence and regression prevention
4. Refactor with that safety net

**This is fine**: You're still getting the safety net. You're just not doing it dogmatically.

### Tests Can Be "Moist"

**Principle**: Don't apply DRY fanatically to tests. Some repetition is fine.

**Guidelines**:
- Test readability matters more than test reusability
- Duplicating test setup is often clearer than complex test factories
- Each test should be understandable in isolation
- Shared test utilities are fine, but don't create a test framework

### Testing Coverage Guidelines

**Principle**: Coverage is a negative indicator, not a goal.

**Use Coverage To**:
- Find code that's never executed
- Identify risky uncovered paths

**Don't Use Coverage To**:
- Chase 100% (diminishing returns are real)
- Feel good about bad tests
- Mandate arbitrary thresholds

**Reality Check**: 100% coverage with bad tests is worse than 80% coverage with good tests.

---

## 🔒 Security Principles

### Defense in Depth

**Principle**: Implement multiple layers of security controls.

**Guidelines**:
- Don't rely on a single security mechanism
- Validate inputs at multiple layers
- Use authentication and authorization
- Encrypt sensitive data in transit and at rest
- Implement rate limiting and access controls

### Principle of Least Privilege

**Principle**: Grant only the minimum access necessary to perform a task.

**Guidelines**:
- Use fine-grained permissions
- Avoid overly permissive access controls
- Separate user roles and permissions
- Review and revoke unnecessary privileges
- Use service accounts with limited scope

### Input Validation and Sanitization

**Principle**: Never trust user input or external data.

**Guidelines**:
- Validate all inputs against expected formats and ranges
- Sanitize inputs to prevent injection attacks
- Use parameterized queries for databases
- Escape output when rendering in HTML/JS
- Implement Content Security Policy (CSP)
- Validate file uploads (type, size, content)

### Secure by Default

**Principle**: Systems should be secure out of the box, requiring explicit action to reduce security.

**Guidelines**:
- Use secure defaults for configurations
- Require opt-in for insecure features
- Enable security features by default
- Fail securely—errors should not expose sensitive information
- Don't log sensitive data (passwords, tokens, PII)

### Keep Security Updated

**Principle**: Regularly update dependencies and apply security patches.

**Guidelines**:
- Monitor dependencies for vulnerabilities
- Keep frameworks and libraries up to date
- Use automated dependency scanning
- Apply security patches promptly
- Review security advisories for used technologies

---

## 📚 Documentation Principles

### Self-Documenting Code

**Principle**: Code should be clear enough to understand without extensive comments.

**Guidelines**:
- Use descriptive variable and function names
- Keep functions small and focused
- Follow consistent naming conventions
- Structure code logically
- Only comment when code cannot be self-explanatory

### Document the "Why", Not the "What"

**Principle**: Comments should explain reasoning and context, not restate the code.

**Good Comments**:
- Explain complex algorithms or business logic
- Describe why a particular approach was chosen
- Warn about gotchas or non-obvious behavior
- Reference tickets, RFCs, or external documentation
- Provide examples of usage

**Avoid**:
- Redundant comments that restate the code
- Outdated comments that don't match current code
- Commented-out code (use version control instead)

### Maintain Documentation

**Principle**: Documentation should evolve with the code.

**Guidelines**:
- Update documentation when changing code
- Keep README files current
- Document API changes in changelogs
- Version documentation alongside code
- Remove outdated documentation
- Use documentation generation tools (JSDoc, Sphinx, etc.)

### API Documentation

**Principle**: Public interfaces must be well-documented.

**Guidelines**:
- Document all public functions, classes, and modules
- Describe parameters, return values, and exceptions
- Provide usage examples
- Document expected behavior and edge cases
- Include type information
- Explain preconditions and postconditions

---

## 🤖 VSCode Copilot Principles

These principles are specific to VSCode Copilot and guide how AI should approach code generation, modification, and assistance.

### Context Awareness

**Principle**: Understand and respect the existing codebase context before making changes.

**Guidelines**:
- Analyze existing code patterns and conventions
- Match the project's coding style and architecture
- Understand dependencies and their versions
- Review related code before suggesting changes
- Consider the broader system architecture
- Ask clarifying questions when context is unclear
- Respect framework-specific patterns and idioms

**Actions**:
- Read relevant configuration files (package.json, requirements.txt, etc.)
- Review existing implementations of similar features
- Check for established patterns in the codebase
- Understand the project structure before adding new files

### Incremental Changes

**Principle**: Make small, focused changes that can be easily reviewed and tested.

**Guidelines**:
- Break large tasks into smaller, manageable steps
- Complete one logical change before moving to the next
- Test each increment before proceeding
- Provide checkpoints for user feedback
- Avoid massive refactorings in a single step
- Make changes reversible when possible
- Build complexity gradually, not all at once

**Benefits**:
- Easier to debug when issues arise
- User can provide feedback early
- Reduces cognitive load
- Maintains working state between changes

### Verify Before Modify

**Principle**: Understand existing code thoroughly before making changes.

**Guidelines**:
- Read the code to understand current behavior
- Identify all affected areas before changing
- Check for dependencies and references
- Understand the purpose and constraints
- Consider backward compatibility
- Look for tests that might be affected
- Use appropriate tools to gather context (semantic search, grep, etc.)

**Anti-patterns to Avoid**:
- Making assumptions about code behavior
- Changing code without reading it first
- Ignoring related code that might be affected

### Test and Validate

**Principle**: Verify that changes work correctly before declaring completion.

**Guidelines**:
- Run existing tests after making changes
- Create new tests for new functionality
- Test edge cases and error conditions
- Verify that the change solves the intended problem
- Check for unintended side effects
- Validate against requirements
- Use linters and type checkers
- Test in relevant environments when possible

### Clear Communication

**Principle**: Communicate intentions, actions, and outcomes clearly to users.

**Guidelines**:
- Explain what changes will be made and why
- Ask for clarification when requirements are ambiguous
- Describe trade-offs and alternative approaches
- Report any issues or limitations discovered
- Provide context for technical decisions
- Use precise technical language
- Summarize completed work clearly

**Avoid**:
- Making silent assumptions
- Implementing features without confirmation
- Using vague or ambiguous language

### Respect Constraints

**Principle**: Honor project-specific constraints, standards, and guidelines.

**Guidelines**:
- Follow established coding standards and style guides
- Respect framework and library conventions
- Adhere to performance requirements
- Consider resource constraints
- Follow security policies
- Respect license requirements
- Match existing architectural decisions
- Use project-specified tools and dependencies

### Error Handling and Recovery

**Principle**: Handle errors gracefully and provide paths to recovery.

**Guidelines**:
- Implement proper error handling in generated code
- Provide meaningful error messages
- Log errors appropriately
- Fail gracefully without data loss
- Offer alternatives when primary approach fails
- Admit when a task is beyond current capabilities
- Suggest workarounds or manual steps when needed

### Maintain Code Quality

**Principle**: Generated code should meet or exceed existing quality standards.

**Guidelines**:
- Write clean, readable code
- Follow the same principles as human developers
- Ensure code is properly formatted
- Add appropriate documentation
- Avoid introducing technical debt
- Refactor when necessary to improve quality
- Don't generate code you wouldn't accept in review

### Knowledge Boundaries

**Principle**: Acknowledge limitations and avoid making unfounded assumptions.

**Guidelines**:
- State when information is uncertain
- Ask questions rather than guessing
- Admit when lacking domain knowledge
- Defer to user expertise on business logic
- Acknowledge when a task is beyond capabilities
- Suggest research or consultation when needed
- Don't hallucinate APIs, libraries, or features

### Continuous Learning

**Principle**: Adapt to project-specific patterns and user preferences.

**Guidelines**:
- Learn from user feedback and corrections
- Recognize and replicate established patterns
- Adapt to user's preferred communication style
- Remember context within a session
- Build on previous successful approaches
- Adjust to project evolution over time

---

## 🎓 Applying These Principles

### Priority Hierarchy

When principles conflict, use this hierarchy:

1. **Security** - Never compromise security for other concerns
2. **Correctness** - Code must work correctly
3. **Maintainability** - Code must be maintainable over time
4. **Simplicity** - Keep solutions as simple as possible
5. **Performance** - Optimize when needed, not prematurely

### Pragmatic Application

**Remember**:
- Principles are guidelines, not rigid rules
- Context matters—some situations require flexibility
- Balance principles against project constraints
- Perfection is the enemy of good—ship working code
- Technical debt is sometimes acceptable with a plan to address it
- Communicate trade-offs when compromising principles

### Code Review Checklist

Use these principles as a checklist when reviewing code:

- [ ] Does the code follow SOLID principles?
- [ ] Is there any code repetition that should be eliminated (DRY)?
- [ ] Is the solution as simple as possible (KISS)?
- [ ] Does it implement only what's needed (YAGNI)?
- [ ] Are concerns properly separated?
- [ ] Is the code readable and maintainable?
- [ ] Are there appropriate tests?
- [ ] Are security best practices followed?
- [ ] Is the code properly documented?
- [ ] Does it match existing project patterns?

---

## 📖 References and Further Reading

- **SOLID Principles**: Robert C. Martin (Uncle Bob)
- **Clean Code**: Robert C. Martin
- **The Pragmatic Programmer**: Andrew Hunt and David Thomas
- **Design Patterns**: Gang of Four (Erich Gamma, et al.)
- **Refactoring**: Martin Fowler
- **Test Driven Development**: Kent Beck

---

**Last Updated**: 2025-11-04
**Version**: 1.0.0
