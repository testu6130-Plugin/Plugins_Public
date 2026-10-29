---
name: review-code
description: Reviews a code change for bugs, security issues, and readability. Use when the user asks to review code, a diff, or a pull request.
---
 
# Review Code
 
Review the code the user provides and report problems that matter. Skip style nitpicks.
 
## Steps
 
1. Work out what the change is supposed to do: from the user's message, the PR description, or the code itself.
2. Read the changed code and the code right around it.
3. Check, in this order:
   - **Correctness:** logic errors, off-by-one mistakes, missing null or empty checks, wrong error handling.
   - **Security:** unvalidated input, injection, hard-coded secrets, logged personal data.
   - **Reliability:** unhandled exceptions, resource leaks, async misuse, missing timeouts.
   - **Tests:** is the changed behavior covered, and do the tests check results?
   - **Readability:** unclear names, functions that are too long, misleading comments.
4. Report only issues you can point to in the code.
 
## Output format
 
Start with a one-line verdict: **Approve**, **Approve with comments**, or **Changes needed**.
 
Then list each finding:
 
| Severity | Location | Problem | Suggested fix |
|---|---|---|---|
| P0 / P1 / P2 | `file:line` | What breaks, in plain words | The concrete change |
 
- **P0:** must fix (data loss, security hole, crash).
- **P1:** should fix (real bug or failure path).
- **P2:** optional improvement.
 
If there are no issues, say so and name what you checked.
 
## Rules
 
- Don't invent line numbers. If you can't find the exact line, quote the code instead.
- Don't rewrite the whole file; suggest the smallest fix.
- If the change's purpose is unclear, ask before reviewing.
 
