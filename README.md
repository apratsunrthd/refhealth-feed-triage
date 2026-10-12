# Healthcare Feed Triage

A free, local Claude Desktop extension that checks whether a healthcare event feed has the timing and quality signals needed to investigate an operational use case. It inspects CSV event feeds or FHIR Bundles through one read-only MCP tool. The [product page](https://refhealth.consulting/feed-triage.html) has a ready-to-install download and example findings.

## Installation Options

### 1. Smithery CLI (Cursor, Windsurf, Claude)

Install and register automatically via [Smithery](https://smithery.ai):

```bash
npx -y @smithery/cli install @apratsunrthd/refhealth-feed-triage --client claude
```

Or for Cursor:
```bash
npx -y @smithery/cli install @apratsunrthd/refhealth-feed-triage --client cursor
```

### 2. Claude Desktop Extension (`.mcpb`)

1. Download [`refhealth-feed-triage.mcpb`](https://refhealth.consulting/refhealth-feed-triage.mcpb).
2. In Claude Desktop, open Settings → Extensions → Advanced settings → Install extension and select the file.

### 3. Manual Process Config (`stdio`)

Add to your `claude_desktop_config.json` or IDE MCP configuration:

```json
{
  "mcpServers": {
    "refhealth-feed-triage": {
      "command": "node",
      "args": ["/path/to/refhealth-feed-triage/mcp/server.mjs"]
    }
  }
}
```

## Try it with Claude or Cursor

Claude may ask you to allow the tool call. The bundled sample contains synthetic events, including a late delivery, duplicate, and invalid clock ordering.

Other prompts:

- “Inspect `/absolute/path/to/events.csv` against a 48-hour delivery target. Which rows need investigation?”
- “Inspect `/absolute/path/to/bundle.json` and explain what the FHIR checks can and cannot tell me.”

Use only synthetic or approved de-identified files. The extension reads the file you name and returns aggregate counts and row-numbered findings to Claude. It makes no network requests. It does not establish clinical suitability, consent, cohort coverage, or outreach success. See the [privacy notice](https://refhealth.consulting/feed-triage-privacy.html) and [input reference](mcp/README.md).

Results with findings include an optional [investigation guide](https://refhealth.consulting/feed-triage.html#investigate) link. Claude may show it after the check; the extension never opens it automatically.

## Build and test

Requires Node.js 20 or later for development; Claude Desktop supplies its own Node.js runtime for the installed package.

```bash
npm ci --prefix mcp
npm test --prefix mcp
./scripts/build-feed-bundle.sh
```

The build writes `refhealth-feed-triage.mcpb` in the repository root. To inspect or run it without Claude Desktop, see `mcp/test/server.test.mjs` for an MCP client example. Source is MIT licensed. For support or contributions, open an issue or pull request here; do not attach patient data.

## Related Healthcare Data Engineering Standards

- **[Healthcare Data AI Operating System (HDAIOS) Specification](https://refhealth.consulting/hdaios.html)**: The 5-layer architectural specification connecting decisions, bitemporal data, enterprise BAAs, agent workflows, and governance.
- **[Interactive HDAIOS Self-Assessment Tool](https://refhealth.consulting/hdaios.html#assessment)**: Free, zero-PHI architecture audit tool for healthcare engineering teams.
- **[`refhealth-dbt-healthcare-checks`](https://github.com/apratsunrthd/refhealth-dbt-healthcare-checks)**: 7 generic dbt test macros enforcing bitemporal enrollment consistency, CMS NPI formatting, ICD-10/CPT validity, and midnight timestamp audits.

