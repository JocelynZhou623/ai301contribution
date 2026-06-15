# ai301contribution
CodePath AI301 open source contribution

# Contribution [#]: [Adapter: Cloudflare Workers AI Model Provider]

**Contribution Number:** [1 / 2 / 3]  
**Student:** [Jocelyn Zhou]  
**Issue:** [https://github.com/orthogonalhq/nous-core/issues/322]  
**Status:** [Phase I / Phase II / Phase III / Phase IV] [In Progress / Complete]

---

## Why I Chose This Issue
I chose this issue because it involves TypeScript, which aligns with my experience, and the scope is well-defined — implement one new file following an existing pattern. Cloudflare Workers AI is a growing edge AI platform, making this contribution relevant to current industry trends. The issue has clear acceptance criteria and reference implementations to follow. I'm also interested in learning how AI model routing and provider interfaces are designed in a production agent framework.

## Understanding the Issue
The Nous AI agent framework currently lacks a Cloudflare Workers AI model provider adapter. This means users cannot route tasks to Cloudflare's AI inference service through the Nous subcortex layer. The fix requires implementing the IModelProvider interface for Cloudflare Workers AI, including invoke, stream, and getConfig methods, following the same pattern as existing adapters like openai-provider.ts and anthropic-provider.ts.

### Problem Description

The nous-core subcortex layer is missing a Cloudflare Workers AI model provider adapter. Users cannot route tasks to Cloudflare's AI inference service through the Nous model routing system.

### Expected Behavior

Users should be able to configure Cloudflare Workers AI as a model provider in Nous and route tasks to it via the subcortex layer, just like OpenAI or Anthropic.

### Current Behavior

No cloudflare-workers-ai-provider.ts exists in self/subcortex/providers/src/. The Cloudflare Workers AI model cannot be used within Nous.

### Affected Components
- self/subcortex/providers/src/ (new file to be created)
- self/subcortex/providers/src/index.ts (needs export)
- self/subcortex/providers/src/__tests__/ (new test file)

---

## Reproduction Process

### Environment Setup
Cloned nous-core repository locally. Installed dependencies with pnpm install (Node.js 22+, pnpm 10+). Navigated to self/subcortex/providers/src/ to review existing adapter structure.

### Steps to Reproduce
1. Clone the nous-core repository
2. Navigate to self/subcortex/providers/src/
3. List existing provider files — confirmed openai-provider.ts, ollama-provider.ts, and anthropic-provider.ts exist
4. Confirmed no cloudflare-workers-ai-provider.ts exists
5. Reviewed openai-provider.ts to understand the IModelProvider interface structure

### Reproduction Evidence

- **Commit showing reproduction:** [Link to commit in your fork]
- **Screenshots/logs:** [If applicable]
- **My findings:** [What you discovered during reproduction]

---

## Solution Approach

### Analysis

The provider is simply missing. The IModelProvider interface and pattern already exist in the codebase via openai-provider.ts and anthropic-provider.ts. A new adapter file needs to be created following the same pattern, using Cloudflare Workers AI's OpenAI-compatible /v1/chat/completions API endpoint.

### Proposed Solution

Create a new cloudflare-workers-ai-provider.ts file implementing the IModelProvider interface, using Cloudflare Workers AI's API endpoint and Bearer token authentication, following the exact same pattern as openai-provider.ts.

### Implementation Plan

Using UMPIRE framework (adapted):

**Understand:** he nous-core framework is missing a Cloudflare Workers AI adapter. Users cannot use Cloudflare's AI models through Nous.

**Match:**  openai-provider.ts and anthropic-provider.ts in self/subcortex/providers/src/ implement the IModelProvider interface and serve as direct reference implementations.

**Plan:** [Step-by-step implementation plan]
1. Create self/subcortex/providers/src/cloudflare-workers-ai-provider.ts
2. Implement IModelProvider interface (invoke, stream, getConfig)
3. Validate input against TextModelInputSchema
4. Handle streaming responses correctly
5. Export from self/subcortex/providers/src/index.ts
6. Write tests in self/subcortex/providers/src/__tests__/

**Implement:** [Link to your branch/commits as you work]

**Review:** [Self-review checklist - does it follow the project's contribution guidelines?]

**Evaluate:** [How will you verify it works?]Tests will verify invoke and stream methods work correctly. Existing tests should continue to pass.

---

## Testing Strategy

### Unit Tests

- [ ] Test case 1: [Description]
- [ ] Test case 2: [Description]
- [ ] Test case 3: [Description]

### Integration Tests

- [ ] Integration scenario 1
- [ ] Integration scenario 2

### Manual Testing

[What you tested manually and results]

---

## Implementation Notes

### Week [X] Progress

[What you built this week, challenges faced, decisions made]

### Week [Y] Progress

[Continue documenting as you work]

### Code Changes

- **Files modified:** [List]
- **Key commits:** [Links to important commits]
- **Approach decisions:** [Why you chose certain approaches]

---

## Pull Request

**PR Link:** [GitHub PR URL when submitted]

**PR Description:** [Draft or final PR description - much of the content above can be adapted]

**Maintainer Feedback:**
- [Date]: [Summary of feedback received]
- [Date]: [How you addressed it]

**Status:** [Awaiting review / Iterating / Approved / Merged]

---

## Learnings & Reflections

### Technical Skills Gained

[What you learned technically]

### Challenges Overcome

[What was hard and how you solved it]

### What I'd Do Differently Next Time

[Reflection on your process]

---

## Resources Used

- [Link to helpful documentation]
- [Tutorial or Stack Overflow post that helped]
- [GitHub issues or discussions that helped]
