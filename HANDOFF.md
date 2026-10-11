# Handoff

Start with `README.md`, then `TODO.md`. The source is in `mcp/`; `mcp/feed-core.mjs` implements deterministic CSV and FHIR checks, `mcp/server.mjs` exposes `inspect_healthcare_feed`, and `mcp/test/` exercises both rules and MCP protocol. `scripts/build-feed-bundle.sh` packages the extension.

Run `npm ci --prefix mcp`, `npm test --prefix mcp`, and `./scripts/build-feed-bundle.sh`. Test the bundled synthetic CSV in Claude Desktop with the first prompt in `README.md`. Do not add real patient data to examples, issues, or tests. Public site download and repository source should be updated together for each release.

The server reads only the absolute file path passed to it (or its bundled sample), caps input at 10 MB and 20,000 rows/entries, and returns aggregate findings. Claude receives the tool response. The package is local and makes no network calls.

The 0.1.1 package was submitted to Anthropic's desktop extension directory on 2026-10-11. Monitor `contact@refhealth.consulting` for a review response; a submission does not guarantee listing.
