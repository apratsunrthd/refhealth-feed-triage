# Architecture

Claude Desktop loads the `.mcpb` archive and starts `mcp/server.mjs` over MCP stdio. The single read-only tool accepts an optional absolute `.csv` or `.json` path and a CSV delivery target from 1 to 168 hours. With no path it reads the bundled synthetic CSV. `mcp/feed-core.mjs` performs all inspection locally and returns aggregate JSON with row-numbered findings. The server sends that JSON to Claude for interpretation.

CSV checks validate required columns and timezone-aware timestamps, deduplicate matching retries, exclude conflicting duplicate IDs, and compute delivery rates and latency summaries. FHIR Bundle checks cover Encounter IDs, subject references, encounter period ordering, and references to Patients present in the supplied Bundle. FHIR `meta.lastUpdated` is not treated as delivery time.

The server has no HTTP client, persistence, telemetry, account, or API key. Its trust boundary is the local file the user names and the tool result sent to Claude. The landing page and privacy notice live at `refhealth.consulting`; they are outside the extension runtime.
