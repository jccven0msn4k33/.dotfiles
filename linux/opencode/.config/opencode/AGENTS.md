# Global Agent Instructions

These rules apply across all opencode sessions on this machine.
Edit this file via `dotfiles-opencode-wizard` → Edit Instructions, or directly with your editor.

## General Behaviour

- Be concise and direct. Avoid over-explaining.
- Ask clarifying questions before making large or irreversible changes.
- Prefer editing existing code over creating new files.
- Follow the existing code style of the project at hand.

## Code Quality

- Apply KISS & DRY principles, but prioritise consistency with existing code.
- No N+1 queries. Add indexes for columns used in queries.
- Validate at system boundaries (user input, external APIs) only.
- Do not add comments or docstrings to code you didn't change.

## Security (OWASP)

- Parameterised queries always — no raw SQL string interpolation.
- Sanitise and validate all user input.
- Use least-privilege access patterns.
- Strip sensitive fields (passwords, tokens) from logs.

## Git & PRs

- Do not commit or push automatically unless explicitly asked.
- Keep PRs ≤ 200 lines where possible.
- Scope changes to the ticket/story — no unrelated refactoring.

## MCP Hints

- When you need up-to-date library docs, use `context7` tools.
- When you need GitHub repo/PR/issue context, use `github` tools (requires token).
