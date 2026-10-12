# TODO

## Recently completed

- Added `smithery.yaml` configuration for automated installation via Smithery CLI (`npx -y @smithery/cli install @apratsunrthd/refhealth-feed-triage`).
- Added shebang to `mcp/server.mjs` for direct CLI process execution.
- Updated `README.md` with multi-client installation guides (Smithery, Claude Desktop, Cursor, Windsurf) and cross-links to HDAIOS and `refhealth-dbt-healthcare-checks`.

## For Codex or Claude

- Version 0.1.2 adds an optional investigation-guide link when issues are found. The Anthropic directory submission still contains 0.1.1; update its package if the listing is accepted.
- Keep the public source, downloadable `.mcpb`, and manifest version aligned for each release.
- Monitor the desktop extension directory review and update listing status if Anthropic responds.
- Use feedback from actual feed investigations to prioritize any additional checks.

## For a human

- Review any follow-up from Anthropic at `contact@refhealth.consulting`.
- Try the extension on an approved de-identified feed and report which findings changed a decision or question.
