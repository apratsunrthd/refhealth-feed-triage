# Healthcare Feed Triage

A free, local Claude Desktop extension that checks whether a healthcare event feed has the timing and quality signals needed to investigate an operational use case. It inspects CSV event feeds or FHIR Bundles through one read-only MCP tool. The [product page](https://refhealth.consulting/feed-triage.html) has a ready-to-install download and example findings.

## Install and try it

1. Download [`refhealth-feed-triage.mcpb`](https://refhealth.consulting/refhealth-feed-triage.mcpb).
2. In Claude Desktop, open Settings → Extensions → Advanced settings → Install extension and select the file.
3. Ask: “Use Healthcare Feed Triage on its included synthetic sample. Could this feed support a 24-hour follow-up trigger? Show the evidence and what I should ask the data owner.”

Claude may ask you to allow the tool call. The bundled sample contains synthetic events, including a late delivery, duplicate, and invalid clock ordering.

Other prompts:

- “Inspect `/absolute/path/to/events.csv` against a 48-hour delivery target. Which rows need investigation?”
- “Inspect `/absolute/path/to/bundle.json` and explain what the FHIR checks can and cannot tell me.”

Use only synthetic or approved de-identified files. The extension reads the file you name and returns aggregate counts and row-numbered findings to Claude. It makes no network requests. It does not establish clinical suitability, consent, cohort coverage, or outreach success. See the [privacy notice](https://refhealth.consulting/feed-triage-privacy.html) and [input reference](mcp/README.md).

## Build and test

Requires Node.js 20 or later for development; Claude Desktop supplies its own Node.js runtime for the installed package.

```bash
npm ci --prefix mcp
npm test --prefix mcp
./scripts/build-feed-bundle.sh
```

The build writes `refhealth-feed-triage.mcpb` in the repository root. To inspect or run it without Claude Desktop, see `mcp/test/server.test.mjs` for an MCP client example. Source is MIT licensed. For support or contributions, open an issue or pull request here; do not attach patient data.
