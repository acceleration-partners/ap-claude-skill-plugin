---
name: ap-vision
description: >
  Work with Acceleration Partners affiliate performance data via the APVision MCP server.
  Use this skill when building prototypes, analyzing affiliate marketing performance,
  querying merchant data, publisher rankings, trends, benchmarks, or CRM data.
when_to_use: >
  Triggered by requests like: "show me performance data", "build a prototype for...",
  "analyze merchants", "get publisher rankings", "compare periods", "show trends".
---

# APVision MCP — Working Guide

APVision is the Acceleration Partners data platform. This MCP server exposes affiliate marketing performance data: trends, benchmarks, CRM publishers, merchants, and more. Test 369 69 9 111

## Authentication

Authentication is handled automatically via the MCP server. No credentials needed from the user — the Bearer token is managed by the server. If a 401 is returned, the user needs to re-authenticate via the OAuth flow.

## Step 1 — Always Start Here

**Before any data query, call `get_assigned_merchants` first.**

This returns the list of merchants the authenticated user has access to. All subsequent tool calls should use only the `merchantKey` values from this response.

```
get_assigned_merchants → [ { merchantKey, networkKey, merchantName, ... } ]
```

If the result is empty, the user has no merchant access — inform them and stop.

## Step 2 — Understand What Data You Need

See [tools.md](tools.md) for the full tool reference.

**Trends & Benchmarks** — time-series performance metrics:
- Revenue, clicks, actions, commission, ROAS, AOV, CVR
- Period comparisons, publisher rankings, country/region/vertical breakdowns
- All require: `merchantKeys[]`, `dateStart`, `dateEnd`

**CRM** — publisher and merchant relationship data:
- Publishers, recommendations, tags, verticals, networks
- Some tools require `merchantKeys[]`, others don't

## Step 3 — Date Ranges

Always confirm date range with the user if not specified. Default to last 30 days.

Format: `YYYY-MM-DD`

For period comparison tools (`get_period_comparison`, `get_publisher_rankings`, etc.) you also need `prevDateStart` and `prevDateEnd`.

## Step 4 — Building a Prototype

When asked to build a prototype or demo:

1. Call `get_assigned_merchants` → get available merchants
2. Ask the user which merchant(s) to focus on (or use all if they have few)
3. Determine what metrics they want to see
4. Call the relevant tools in parallel where possible
5. Present data in a structured, readable format
6. Suggest next steps or related data they might want

## Key Rules

- Only use `merchantKey` values returned by `get_assigned_merchants`
- Never expose raw error details from the API to end users
- Round financial values to 2 decimal places
- Use AP terminology: **publisher** (not affiliate), **merchant** (not advertiser), **commission** (not payout)
- If a tool returns empty data, explain why (date range too narrow, no activity, etc.)
- For large date ranges, suggest breaking into smaller periods if performance is slow
