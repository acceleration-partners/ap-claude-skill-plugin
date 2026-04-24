# APVision Tool Reference

All tools require a valid authenticated session via the AP MCP server.

## Required Parameters (most tools)

| Parameter | Type | Description |
|-----------|------|-------------|
| `merchantKeys` | number[] | From `get_assigned_merchants` |
| `dateStart` | string | `YYYY-MM-DD` |
| `dateEnd` | string | `YYYY-MM-DD` |

---

## Trends & Benchmarks Tools

### Aggregate Metrics
| Tool | What it returns |
|------|----------------|
| `get_totals` | Sum of clicks, revenue, commission, cost, actions, orders |
| `get_ratios` | AOV, CVR, ROAS, CPA, commission rate |
| `get_averages` | Daily and monthly averages |
| `get_customer_metrics` | New vs repeat customer breakdown |

### Comparison & Rankings
| Tool | What it returns | Extra params needed |
|------|----------------|---------------------|
| `get_period_comparison` | Current vs previous period delta | `prevDateStart`, `prevDateEnd` |
| `get_publisher_rankings` | Top publishers by metric | `prevDateStart`, `prevDateEnd` |
| `get_client_rankings` | Benchmark vs other clients | `rank_client` filter |
| `get_vertical_rankings` | Benchmark within vertical | `rank_vertical` filter |

### Breakdown by Dimension
| Tool | Dimension |
|------|-----------|
| `get_country_data` | Geographic — countries |
| `get_region_data` | Geographic — regions |
| `get_network_metrics` | Affiliate networks |
| `get_vertical_data` | Industry verticals |
| `get_diversification` | Revenue/traffic distribution |

### Activity Metrics
| Tool | What it returns |
|------|----------------|
| `get_activity_metrics` | Publisher click/sale activity |
| `get_program_activity_metrics` | Program and platform activity counts |
| `get_vertical_activity_metrics` | Vertical-level activity |
| `get_network_wot_metrics` | Network week-over-time trends |

---

## CRM Tools

### Publishers
| Tool | What it returns |
|------|----------------|
| `get_crm_publishers` | Search CRM publishers (groups) with filters |
| `get_crm_publishers_performance` | Time-series performance per CRM publisher |
| `get_publisher_merchant_performance` | Publisher performance across merchants |
| `get_publisher_tags` | Publisher segments and categories |
| `get_publisher_recommendations` | Recommendation history |

### Merchants & Reference Data
| Tool | What it returns |
|------|----------------|
| `get_assigned_merchants` | Merchants accessible to current user ← **start here** |
| `get_active_merchants` | All active merchants with network info |
| `get_merchants_verticals` | Merchants with their verticals/properties |
| `get_verticals` | Available verticals with counts |
| `get_networks_and_platforms` | Affiliate networks and platforms |

### Lookup Tables
| Tool | What it returns |
|------|----------------|
| `get_countries` | Countries with codes and regions |
| `get_regions` | All geographic regions |
| `get_recommendation_statuses` | All recommendation status values |