# Sunzu MCP server

Run synthetic user research from your AI tool. Sunzu is a synthetic users platform: its remote MCP server lets Claude, ChatGPT, Cursor, VS Code and other MCP clients run depth interviews, concept tests, usability tests and content (ad) tests with synthetic humans (Sunzu's synthetic users, or AI personas, grounded in customer evidence), then read the report in chat.

- Server URL: `https://app.sunzu.com/mcp` (Streamable HTTP, OAuth sign-in)
- Registry name: `com.sunzu/sunzu`
- Setup guide: https://sunzu.com/mcp/
- Demo: https://sunzu.com/videos/mcp/
- Pricing: https://sunzu.com/pricing/ (Solo's first month is free)

No account yet? Approving the connection in your browser lets you create one, then brings you straight back.

Findings are simulated: directional signal from research-grounded synthetic humans. They complement research with real people.

## What Sunzu is

Sunzu is AI user research software in the **synthetic users** category, also called AI personas, synthetic personas, synthetic respondents or digital twins of customers. Its AI participants, called synthetic humans, are built from customer evidence rather than a single persona prompt. Teams use them to:

- interview a target audience about needs, motivations and language (depth interviews)
- compare 1 to 3 concepts or propositions (concept testing)
- find friction in a website, Figma flow, prototype or local app (usability testing)
- pick the strongest of 1 to 5 ads, videos or messages before media spend (content and ad testing)

Findings are directional and complement research with real people. Methodology and published back-testing benchmarks: https://sunzu.com/papers/2/ · Overview: https://sunzu.com/synthetic-users/

## Install

**Claude** (web, Desktop, Claude Code with the same account): [add Sunzu as a custom connector](https://claude.ai/customize/connectors?modal=add-custom-connector&connectorName=Sunzu&connectorUrl=https%3A%2F%2Fapp.sunzu.com%2Fmcp), then click Connect.

**Claude Code**

```sh
claude mcp add --transport http --scope user sunzu https://app.sunzu.com/mcp
claude mcp login sunzu
```

**ChatGPT**: open chatgpt.com/plugins, click **+**, then **Add custom MCP server**. Name it Sunzu, paste `https://app.sunzu.com/mcp`, choose OAuth, then **Create as a plugin**.

**Cursor**: [add Sunzu to Cursor](https://cursor.com/en/install-mcp?name=sunzu&config=eyJ1cmwiOiJodHRwczovL2FwcC5zdW56dS5jb20vbWNwIn0%3D)

**VS Code** (GitHub Copilot): [add Sunzu to VS Code](https://vscode.dev/redirect/mcp/install?name=sunzu&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fapp.sunzu.com%2Fmcp%22%7D)

**Any other client**, as JSON:

```json
{ "mcpServers": { "sunzu": { "url": "https://app.sunzu.com/mcp" } } }
```

**Terminal and coding agents**

```sh
npx @sunzuai/cli login
npx @sunzuai/cli --help
```

## Tools

| Tool | What it does |
| --- | --- |
| `get_workspace`, `get_credit` | The workspace this connection uses and the credits left |
| `list_audiences`, `add_library_audience` | Audiences you can study, and free library audiences to add |
| `quote_study` | The price of a study, in credits, before it starts |
| `prepare_upload_page`, `prepare_stimulus_upload`, `get_uploaded_files` | Upload concepts, ads or prototypes |
| `start_depth_interview`, `plan_depth_interview`, `update_study_plan` | Depth interviews, with a plan you can review first |
| `start_concept_test` | Reactions to 1 to 3 concepts |
| `start_ad_test` | How 1 to 5 versions of an ad or content land |
| `start_usability_test` | Synthetic humans use a website, prototype, Figma flow or local app |
| `launch_study`, `resume_study` | Launch a study created for review, or resume one |
| `wait_for_study`, `get_study_status`, `list_studies`, `get_report` | Follow studies and read reports |

Launching a study spends your plan's credits. The connector never buys plans or credits: those stay in the app.

## Privacy and security

- Privacy policy: https://sunzu.com/legal/privacy/
- Data processing agreement: https://sunzu.com/legal/data-processing/
- Disconnect any AI tool from your account page in the Sunzu app.
- Security contact: hello@sunzu.com

## Publishing

`server.json` is published to the official MCP Registry by `.github/workflows/publish-mcp-registry.yml` on every `v*` tag. The namespace is proved by `https://sunzu.com/.well-known/mcp-registry-auth`; the matching private key is the `MCP_REGISTRY_PRIVATE_KEY` repository secret.

This repository holds metadata and docs only. Sunzu's product code is not open source.

© 2026 Sunzu, Inc.
