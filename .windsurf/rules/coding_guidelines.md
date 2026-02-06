---
trigger: always_on
---

## Goal
These guidelines exist to keey work safe, consistent and easy to review.  They also guide AI-assisted changes (Windsurf) to produce small, maintainable diffs.

## Operation Mode
- Prefer small, incremental changes over large rewrites.
- Preserve existing behavior unless the task explicitly says otherwise.
- Optimize for readability and reviewability.
---

## Rules for AI-Assisted Changes

### 1) Default to Minimal Change
- Touch the fewest files possible.
- Avoid reformatting unrelated code.
- Do not rename public interfaces unless explicitly asked.

### 2) Work in Steps
When doing non-trivial work:
- Propose a short plan (2–5 bullets)
- Implement in small chunks
- Re-run tests / add tests as needed

### 3) Don’t Invent Things
- Don’t assume modules, configs, environment variables, or APIs exist.
- If something is missing/unclear, state assumptions in comments or PR notes.

### 4) Keep Behavior Stable
- Refactoring should not change output, side effects, or external interfaces.
- If behavior must change, call it out clearly and add/update tests.

### 5) Keep It Simple, Not Clever
- Prefer clear names and straightforward control flow.
- Avoid overly abstract patterns during refactors unless there’s a clear payoff.

## Code Style
- Follow the existing style in the codebase.
- Ensure all code follows established linting rules
- Keep functions small when practical; extract helpers only when it reduces duplication.


## Error Handling
- Fail loudly rather than silently.
- Don’t swallow exceptions without a reason.
- Error messages should be actionable and not leak sensitive info.

## Testing Expectations
- If a refactor touches logic, try to add/adjust at least one test that proves behavior is unchanged.
- Prefer tests that validate behavior, not implementation details.
- If the project has no tests yet, add small characterization tests around refactored areas.

## Documentation
- Update comments if a change makes existing docs misleading.
- Add a short note in the PR or commit message explaining the intent of the update.

## Optional Prompting Pattern
When asking Windsurf for help, prefer prompts like:
- “Make the smallest change to refactor X without changing behavior.”
- “Follow patterns already used in `<file/module>`.”
- “Return a diff and explain what changed and why.”
- “Add characterization tests before refactoring.”

## Repo Notes
- Programming Language: Typescript 
- Platform: Twilio Flex
- Reference Template Documentation: https://twilio-professional-services.github.io/flex-project-template/ 
- Test runner: jest
- Formatter/linter (if any): none