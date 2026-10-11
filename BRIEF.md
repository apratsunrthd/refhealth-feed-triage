# Brief

Healthcare Feed Triage is a free local MCP extension for Claude Desktop. It inspects a CSV event feed or FHIR Bundle and gives Claude aggregate timing and data quality findings, with row numbers for investigation. Version 0.1.2 supports one read-only tool and two synthetic samples. When it finds issues, the result includes a public investigation-guide link. It has no network service or account requirement.

The extension is intended to help a data team ask better questions about a proposed operational trigger. It cannot establish complete feed coverage, patient consent, clinical suitability, or outreach success. The [product page](https://refhealth.consulting/feed-triage.html) hosts the installable package.

Version 0.1.1 was submitted to Anthropic's desktop extension directory on 2026-10-11; the submitted package does not have the new guide link. Directory acceptance is not guaranteed. Next: gather feedback from users with approved de-identified extracts before adding more rules.
