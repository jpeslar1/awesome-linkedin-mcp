# awesome-linkedin-mcp [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated list of LinkedIn MCP servers, Claude Code workflows that use them, and adjacent tools for building GTM automations through MCP.

Maintained by [John Peslar](https://johnpeslar.com). PRs welcome — see [CONTRIBUTING.md](CONTRIBUTING.md).

## Contents

- [LinkedIn MCP Servers](#linkedin-mcp-servers)
- [Workflows](#workflows)
  - [Outbound](#outbound)
  - [Inbound](#inbound)
  - [Pipeline & CRM](#pipeline--crm)
  - [Events & Webinars](#events--webinars)
  - [Engagement & Content](#engagement--content)
  - [Discovery & Enrichment](#discovery--enrichment)
- [Adjacent MCP Servers](#adjacent-mcp-servers)
- [Resources](#resources)
- [Community](#community)
- [Contributing](#contributing)

## LinkedIn MCP Servers

The handful of LinkedIn MCP servers that actually exist. Most are alpha; choose based on whether you need (a) read-only or read+write, (b) personal-account or commercial use, (c) production schedule or one-off scripts.

| Project | Maintainer | Type | Notes |
|---|---|---|---|
| [Zevari](https://zevari.ai) | [Zevari AI](https://zevari.ai) | Commercial, hosted MCP | Read + write. Live LinkedIn profile lookup, behavioral profile, ICP scoring, safe message/comment/connect writes, rate-limit awareness. Used in every workflow in this list. |
| [stickerdaniel/linkedin-mcp-server](https://github.com/stickerdaniel/linkedin-mcp-server) | Daniel Sticker | Open source, self-hosted | Read-only profile/post lookup. README is honest about ToS risk — read it before using on a real account. |
| [HeyLead](https://github.com/D4umak/linkedin-outreach-mcp) | [Denys Chumak](https://heylead.dev) | Open source client (MIT) + hosted MCP | AI agent for LinkedIn outreach: finds the right people, writes in your voice, follows up, replies. Six campaign goals: sell a product or service, find a job, hire people, find partners or investors, find a vendor, research interviews. Read + write; sends from your own account via Unipile at a stated pace (20 invitations a day, 100 a week on a free LinkedIn plan). Not affiliated with LinkedIn; README states the ToS position. |
| [adhikasp/mcp-linkedin](https://github.com/adhikasp/mcp-linkedin) | Adhika Setya Pramudita | Open source, self-hosted | Lightweight feed/jobs reader via unofficial LinkedIn API. Alpha. |

(If you maintain a LinkedIn MCP and want it listed, see [CONTRIBUTING.md](CONTRIBUTING.md).)

## Workflows

Claude Code prompts that use a LinkedIn MCP plus other connectors to do real GTM work. All of the workflows below are mine — the section format is meant for community contributions to follow.

### Outbound

- [linkedin-mcp-weekly-outbound-pipeline](https://github.com/jpeslar1/linkedin-mcp-weekly-outbound-pipeline) — Weekly cold outbound batch. Zevari + Instantly + Pipedrive + Google Sheets + Slack. CPG-flavored but adapts to any vertical.
- [linkedin-mcp-lost-deal-reengagement](https://github.com/jpeslar1/linkedin-mcp-lost-deal-reengagement) — Closed-lost revival driven by live LinkedIn signal (job change, competitor trouble, content engagement), not the calendar.

### Inbound

- [linkedin-mcp-inbound-lead-triage](https://github.com/jpeslar1/linkedin-mcp-inbound-lead-triage) — Real-time form/webhook → live Zevari ICP score → HOT/WARM/COLD routing with Slack alerts and Pipedrive deals.
- [linkedin-mcp-inbox-zero-triage](https://github.com/jpeslar1/linkedin-mcp-inbox-zero-triage) — Gmail thread classification by LinkedIn-confirmed sender intent. Auto-reply, route, or surface buying signals.
- [linkedin-mcp-newsletter-to-pipeline](https://github.com/jpeslar1/linkedin-mcp-newsletter-to-pipeline) — Newsletter subscriber → Zevari live resolution → SDR queue / nurture / DQ. Works with Beehiiv, Substack, Kit.

### Pipeline & CRM

- [linkedin-mcp-job-change-trigger](https://github.com/jpeslar1/linkedin-mcp-job-change-trigger) — Daily live sweep of a champion watchlist to catch job changes the day they happen.
- [linkedin-mcp-ae-daily-briefing](https://github.com/jpeslar1/linkedin-mcp-ae-daily-briefing) — 7:30 AM AE briefing with live LinkedIn signals on every open opportunity.

### Events & Webinars

- [linkedin-mcp-event-attendee-enrichment](https://github.com/jpeslar1/linkedin-mcp-event-attendee-enrichment) — Resolve every event attendee live on LinkedIn for accurate titles + ICP tiering. Works with Luma, Eventbrite, Zoom exports.
- [linkedin-mcp-webinar-followup](https://github.com/jpeslar1/linkedin-mcp-webinar-followup) — Tier webinar attendees by attendance × ICP × behavioral signal. Per-tier personalized follow-up.
- [linkedin-mcp-trade-show-pipeline](https://github.com/jpeslar1/linkedin-mcp-trade-show-pipeline) — 3-phase trade show pipeline: pre-show outreach, on-site capture, post-show tiered follow-up + ROI report.

### Engagement & Content

- [linkedin-mcp-engagement-pod](https://github.com/jpeslar1/linkedin-mcp-engagement-pod) — Safe engagement pod with voice-DNA comment generation and live safety-status gating before every write.

### Discovery & Enrichment

- [linkedin-mcp-icp-discovery](https://github.com/jpeslar1/linkedin-mcp-icp-discovery) — Seed from your best customers → Apollo firmographics → Zevari behavioral lookalike scoring → live-confirmed top-tier list.

## Adjacent MCP Servers

LinkedIn MCPs work best as one layer in a multi-MCP stack. These are the other servers that show up across the workflows above:

| Project | Purpose | Notes |
|---|---|---|
| [bcharleson/instantly-mcp](https://github.com/bcharleson/instantly-mcp) | Cold email sends | Community MCP for Instantly v2 API. Used for campaign enrollment in every outbound workflow. |
| [comma-compliance/pipedrive-mcp](https://github.com/comma-compliance/pipedrive-mcp) | CRM | 75-tool Pipedrive MCP with full CRUD + custom-field resolution. Used for dedupe, contact updates, deal creation. |
| [BlockchainRev/apollo-mcp-server](https://github.com/BlockchainRev/apollo-mcp-server) | Firmographic data | Community MCP for Apollo.io. Used as seed data in lookalike discovery; stale on its own but useful as a seed. |
| [Supabase MCP](https://supabase.com/docs/guides/getting-started/mcp) | Webhook queues + state | Used for durable inbound webhook processing. |
| [taylorwilsdon/google_workspace_mcp](https://github.com/taylorwilsdon/google_workspace_mcp) | Gmail / Calendar / Drive / Sheets | Used across inbox triage, AE briefing, event workflows. |
| [Stripe MCP](https://docs.stripe.com/mcp) | Payments | Official remote MCP at `mcp.stripe.com`. Used for customer revenue context in briefing workflows. |
| [Claude in Chrome](https://www.anthropic.com/news/claude-for-chrome) | Browser control | Used for Slack webhook posting (`hooks.slack.com` is blocked in the bash sandbox) and for Google Sheets writes. |

## Resources

- [Anthropic MCP docs](https://modelcontextprotocol.io) — start here if you're new to MCP.
- [Awesome MCP Servers](https://github.com/punkpeye/awesome-mcp-servers) — the broader awesome-list for MCP, not LinkedIn-specific.
- [Zevari API docs](https://docs.zevari.ai) — endpoint reference for the LinkedIn MCP used in this list.
- [Daniel Sticker's linkedin-mcp-server README](https://github.com/stickerdaniel/linkedin-mcp-server) — required reading on LinkedIn ToS risk for any unofficial scraper.

## Community

- This list lives at [github.com/jpeslar1/awesome-linkedin-mcp](https://github.com/jpeslar1/awesome-linkedin-mcp). Star it if you find it useful — that's how others discover it.
- Author: [John Peslar](https://johnpeslar.com). Solo founder, build outbound automations for B2B clients.

## Contributing

PRs welcome for:
- New LinkedIn MCP servers (open source or commercial)
- New workflows that use a LinkedIn MCP
- Corrections, broken links, deprecated projects

See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

## License

[![CC0](https://licensebuttons.net/p/zero/1.0/88x31.png)](https://creativecommons.org/publicdomain/zero/1.0/)

To the extent possible under law, [John Peslar](https://johnpeslar.com) has waived all copyright and related or neighboring rights to this work.
