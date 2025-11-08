# /scp-spike

Plan and execute a technical spike or proof-of-concept to explore unknowns, validate approaches, or de-risk technical decisions.

## Workflow

### Phase 1: Spike Scoping (Before Execution)

1. **Define the Unknown**
   - Ask what specific question or uncertainty needs to be answered
   - Identify what decision depends on this spike
   - Determine the "good enough" criteria for the spike
   - Confirm time-box limit (default: 2-4 hours)

2. **Clarify Success Criteria**
   - Ask what would constitute a successful spike
   - Determine what artifacts are needed (code, docs, decision)
   - Identify if comparison of multiple options is needed
   - Confirm acceptable level of "proof" (quick test vs thorough validation)

3. **Set Boundaries**
   - Confirm what's in scope vs out of scope
   - Ask if there are preferred technologies or approaches to try first
   - Identify constraints (can't add dependencies, must work with X, etc.)
   - Determine if code will be throwaway or production-ready

### Phase 2: Research & Discovery (During Execution)

4. **Research Context**
   - Use Tavily to find similar spikes, POCs, or examples
   - Use Context7 to check official documentation for relevant APIs
   - Search for known issues or gotchas
   - Document findings and relevant links
   - Show progress: "Researching [technology/approach]..."

5. **Analyze Existing Code**
   - Use Serena to map relevant parts of codebase
   - Identify integration points and constraints
   - Find similar patterns already in use
   - Document current state and assumptions
   - Show progress: "Analyzing existing codebase constraints..."

6. **Evaluate Options**
   - Use Sequential Thinking to compare approaches systematically
   - List pros/cons of each option
   - Consider alignment with @PRINCIPLES.instructions.md
   - Identify deal-breakers or show-stoppers
   - Show progress: "Evaluating options..."

### Phase 3: Experimentation (During Execution)

7. **Design Minimal Test**
   - Plan smallest possible proof-of-concept
   - Identify exactly what needs to be validated
   - Choose simplest implementation path
   - Plan measurement approach (performance, complexity, etc.)
   - Show progress: "Designing minimal validation test..."

8. **Create Implementation Plan**
   - Break spike into steps
   - Identify quick wins vs time-consuming explorations
   - Plan checkpoints to reassess direction
   - Note where to pivot if approach fails
   - Show progress: "Creating spike execution plan..."

### Phase 4: Deliverables (After Execution)

9. **Generate Spike Summary**
   Output structured markdown with:

   **Spike Overview**
   - Question being answered
   - Decision this informs
   - Time-box: [X hours]

   **Research Findings**
   - Technologies/approaches investigated
   - Relevant documentation and examples
   - Known issues or limitations discovered

   **Options Evaluated**

   **Option A: [Name]**
   - Description and approach
   - Pros:
     - [Advantage 1]
     - [Advantage 2]
   - Cons:
     - [Limitation 1]
     - [Limitation 2]
   - Effort estimate: [X hours]
   - Risk level: [Low/Medium/High]

   **Option B: [Name]**
   - [Same structure]

   **Recommended Approach**
   - **Choice:** [Option X]
   - **Rationale:** [Why this option is best]
   - **Confidence Level:** [High/Medium/Low]
   - **De-risked:** [What unknowns were eliminated]
   - **Remaining Unknowns:** [What still needs investigation]

   **Proof of Concept Plan**
   - [ ] Step 1: [Minimal validation step] `[Estimate]`
   - [ ] Step 2: [Build on validation] `[Estimate]`
   - [ ] Step 3: [Integration test] `[Estimate]`

   **Integration Considerations**
   - Files to modify: [list]
   - New dependencies needed: [list]
   - Breaking changes: [list or "None"]

   **Risks & Open Questions**
   - [Technical risks that remain]
   - [Questions that need further investigation]

   **Next Steps**
   - Immediate: [What to do first]
   - If successful: [Follow-up work]
   - If blocked: [Alternative approaches]

10. **Offer Follow-up Actions**
    - "Would you like me to implement the proof-of-concept now?"
    - "Should I research [specific aspect] in more depth?"
    - "Would you like me to compare additional options?"
    - "Should I create a full feature plan based on this approach?"

## Context Awareness

**When file is selected:**
- Focus spike on integrating with or modifying that file
- Consider file's patterns and conventions

**When code is selected:**
- Treat selection as the area of uncertainty
- Focus spike on that specific code concern

**When in project root:**
- Consider project-wide implications
- Evaluate architecture-level decisions

**When no context:**
- Ask for the area of focus or uncertainty

## Example Usage

### Example 1: Technology Evaluation Spike
```
User: /scp-spike should we use GraphQL or REST for our new API?
Assistant: I'll help you evaluate GraphQL vs REST for your API. Let me understand the context:

1. What type of clients will consume this API? (web, mobile, 3rd party, etc.)
2. How complex is your data model? (many relations, nested data, etc.)
3. Do clients need flexible queries or are endpoints well-defined?
4. What's your team's experience with each approach?
5. Are there performance requirements I should consider?

[Uses Tavily to research modern API design patterns...]
[Uses Sequential Thinking to compare options systematically...]
[Uses Serena to analyze existing API patterns in codebase...]

**Recommended Approach: REST with JSON:API**
- Rationale: Team familiarity, simple data model, well-defined endpoints
- Confidence: High
- De-risked: Scalability concerns (both can scale), tooling availability
- Remaining unknowns: None critical
```

### Example 2: Performance Spike
```
User: [selects slow data processing function] /scp-spike how can we speed this up?
Assistant: I'll spike performance optimization approaches for this function.

Before I start:
1. What's the current performance vs target? (processing 1000 items in 5s, need <1s?)
2. Can processing be async or must it be synchronous?
3. Is this CPU-bound or I/O-bound?
4. Are there memory constraints?

[Uses Serena to analyze data flow and dependencies...]
[Uses Sequential Thinking to evaluate: streaming, worker threads, caching, algorithm changes...]
[Creates POC plan for most promising approach...]
```

### Example 3: Integration Spike
```
User: /scp-spike can we integrate Stripe payments without refactoring our order system?
Assistant: I'll investigate integrating Stripe with minimal changes to your existing order system.

Let me clarify:
1. What payment flows do you need? (one-time, subscriptions, both?)
2. Do you need to support payment methods beyond cards?
3. What's your current order processing flow?
4. Any compliance requirements (PCI, SCA, etc.)?

[Uses Serena to map current order system...]
[Uses Context7 to review Stripe API documentation...]
[Uses Tavily to find integration examples...]

**Proof of Concept Plan:**
- [ ] Create Stripe test account and get API keys `30m`
- [ ] Implement checkout session creation `1h`
- [ ] Add webhook handler for payment confirmation `1.5h`
- [ ] Test with existing order flow (no refactoring) `1h`

**Remaining Unknowns:**
- Webhook reliability (need to test failure scenarios)
- Subscription handling (out of scope for this spike)
```

## MCP Tools Usage Priority

1. **Sequential Thinking** - Systematically compare options and approaches
2. **Tavily** - Research technologies, examples, and best practices
3. **Context7** - Check official documentation for APIs/libraries
4. **Serena** - Analyze existing code and integration points
5. **Filesystem-with-morph** - (Not used - planning/analysis only)

## Output Format

- **Structured markdown** with clear sections and decision rationale
- **Comparison tables** for evaluating options
- **Actionable POC plan** with checkboxes
- **Interactive prompts** for next steps
- Code snippets for proof-of-concept where helpful
- Links to research sources and documentation
