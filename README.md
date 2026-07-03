# Job Search — Claude Desktop Bundle

> Everything you need in one place: three Agent Skills + the tenant connector. Build your profile, re-rank your matches, write applications — all inside Claude Desktop.

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

> **On Claude Code instead?** Use the one-command plugin: https://github.com/Bundelkund/job-search-plugin

## What's inside

| Item | Type | What it does |
|------|------|--------------|
| `connector/tenant-mcp.mcpb` | MCP connector | Your matches, job text, profile, and application tracker |
| `skills/letter-forge` | skill | Questionnaire → writes your application profile |
| `skills/rank` | skill | Re-ranks your matches by a fit rubric you define |
| `skills/apply` | skill | Turns a job posting into a cover letter + CV |

The skills read and write your data **only** through the connector, scoped to your own API key. No local database, no PDF toolchain.

## Requirements

- [Claude Desktop](https://claude.ai/download) with Agent Skills support
- A personal **tenant API key** (ask the tenant owner)
- The Discovery Engine + Tenant service run centrally — you connect to the live instance, you don't host them

## Install (three steps)

### 1. Install the connector
Double-click / drag `connector/tenant-mcp.mcpb` into Claude Desktop. Paste your API key in the dialog (stored encrypted in your OS keychain). The default URL `https://tenant.konektos.de` is fine.

### 2. Add the three skills
In Claude Desktop: **Settings → Agent Skills → Add Skill**, once per folder:
- `skills/letter-forge`
- `skills/rank`
- `skills/apply`

### 3. Build your profile, then work
```
/letter-forge     # first run only — fills your profile
/rank             # re-rank your current matches
/apply <job_id>   # write the application for one job
```

Typical flow: `letter-forge` once → `rank` → `apply` on the top pick.

## How it fits together

```
Discovery Engine (central) ──► Tenant service (central) ──► tenant-mcp connector
                                                                  │
                                    letter-forge ─ writes ──► your profile
                                    rank / apply ─ read ────► matches + profile
```

## Individual repos

- Skill sources: [letter-forge-skill](https://github.com/Bundelkund/letter-forge-skill) · [rank-skill](https://github.com/Bundelkund/rank-skill) · [apply-skill](https://github.com/Bundelkund/apply-skill)
- Connector source: [tenant-mcp](https://github.com/Bundelkund/tenant-mcp)

## License

MIT — see [LICENSE](LICENSE).
