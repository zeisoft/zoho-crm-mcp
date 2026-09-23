<div align="center">

<img src="assets/cover.png" alt="Zoho CRM through HeyMetra's MCP server" width="100%">

# Zoho CRM &times; HeyMetra

**Lead counts and the pipeline by stage, split into open, won and lost.**

Your pipeline lives in Zoho CRM. What it cost to fill it lives somewhere else entirely. Ask once, across both.

[![MCP Registry](https://img.shields.io/badge/MCP_Registry-com.heymetra%2Fheymetra-1f6feb)](https://registry.modelcontextprotocol.io/v0/servers/com.heymetra%2Fheymetra/versions)
[![Transport](https://img.shields.io/badge/transport-Streamable_HTTP-444)](https://modelcontextprotocol.io/)
[![Auth](https://img.shields.io/badge/auth-OAuth_2.1-444)](https://heymetra.com/security/)
[![Connector page](https://img.shields.io/badge/heymetra.com-zoho-crm-1f6feb)](https://heymetra.com/connectors/zoho-crm/)

```
https://mcp.heymetra.com/mcp
```

</div>

---

## Ask it things like

> How many leads came in this week, and where did they come from?

> Which owner took the most leads last month?

> In the leads that came in this week, which service did people ask about?

> What is the open pipeline worth, and how much have we already won?

> How many open deals carry no amount at all?

> Which fields do our leads carry that we could group a report by?

> What subjects came up most in our call notes this month?

No dashboard, no export, no query language. You ask in the assistant you already use and the answer comes back with the account it came from.

## Connect Zoho CRM

**1. Decide which Zoho user will authorise it**

HeyMetra sees exactly what that user sees. A CRM with territories or role-based sharing shows different records to different people, so the account you sign in with decides the answers, not the plan or the permission switches.

> An administrator sees everything, which is usually what a question about the whole pipeline wants — and is more than you may intend to expose. Pick deliberately.

**2. Choose Zoho CRM on the Connections screen**

It sends you to Zoho's own sign-in page. Your password is typed on Zoho's screen and never reaches HeyMetra.

**3. Grant the three read permissions Zoho lists**

Modules, organisation and settings — all READ. Modules is the records themselves; settings is what lets HeyMetra read your own field names, so a custom field your team added comes back under the label they gave it.

> There is nothing on this screen that can write. If Zoho offers you a WRITE or ALL scope, you are on a different consent screen than the one HeyMetra asked for.

**4. Check the data centre matches**

Zoho runs separate data centres — .com, .eu, .in, .com.au and others — and an organisation lives in exactly one. HeyMetra records which one from the sign-in and calls that one afterwards.

> This is why signing in with the wrong regional account produces an empty CRM rather than an error: the credential is valid, it is simply pointed at a data centre your records are not in.

**5. Add HeyMetra to the assistant you use**

Claude, ChatGPT, Cursor or Codex. The CRM tools appear there and answer from the live CRM — nothing is copied out of it.

## Then add HeyMetra to your assistant

Add HeyMetra once and it is there in every conversation. The address is the same everywhere:

```
https://mcp.heymetra.com/mcp
```

### One command

```bash
npx add-mcp https://mcp.heymetra.com/mcp
```

[`add-mcp`](https://www.npmjs.com/package/add-mcp) is a third-party installer that writes the configuration for Claude Code, Codex, Cursor, Antigravity, VS Code and seventeen other agents. It infers the name from the address, so the server lands as `heymetra`. Run against this endpoint before it was written here.

### Or by hand

<details>
<summary><b>Claude</b> — Settings → Customize → Connectors → Add custom connector</summary>

Paste the address above into Settings → Customize → Connectors → Add custom connector.

_On Team and Enterprise plans only an owner can add it, under Organization settings._

Full walkthrough: [heymetra.com/mcp/claude/](https://heymetra.com/mcp/claude/)
</details>

<details>
<summary><b>ChatGPT</b> — Settings → Security and login → Developer mode, then chatgpt.com/plugins</summary>

Paste the address above into Settings → Security and login → Developer mode, then chatgpt.com/plugins.

_The endpoint has to include its /mcp path here._

Full walkthrough: [heymetra.com/mcp/chatgpt/](https://heymetra.com/mcp/chatgpt/)
</details>

<details>
<summary><b>Grok</b> — grok.com/connectors → New Connector → Custom</summary>

Paste the address above into grok.com/connectors → New Connector → Custom.

_XAI calls this “bring your own MCP”._

Full walkthrough: [heymetra.com/mcp/grok/](https://heymetra.com/mcp/grok/)
</details>

<details>
<summary><b>Perplexity</b> — Settings → Connectors → Custom connector → Remote</summary>

Paste the address above into Settings → Connectors → Custom connector → Remote.

_Perplexity documents it as a Pro, Max and Enterprise feature._

Full walkthrough: [heymetra.com/mcp/perplexity/](https://heymetra.com/mcp/perplexity/)
</details>

<details>
<summary><b>Claude Code</b> — claude mcp add --transport http</summary>

```bash
claude mcp add --transport http heymetra https://mcp.heymetra.com/mcp
```

_Or a .mcp.json in the project root; /mcp inside a session shows what connected._

Full walkthrough: [heymetra.com/mcp/claude-code/](https://heymetra.com/mcp/claude-code/)
</details>

<details>
<summary><b>Codex</b> — ~/.codex/config.toml</summary>

```toml
[mcp_servers.heymetra]
url = "https://mcp.heymetra.com/mcp"
```

_Under an [mcp_servers.<name>] section, then codex mcp login._

Full walkthrough: [heymetra.com/mcp/codex/](https://heymetra.com/mcp/codex/)
</details>

<details>
<summary><b>Cursor</b> — ~/.cursor/mcp.json, or .cursor/mcp.json in a project</summary>

```json
{
  "mcpServers": {
    "heymetra": { "url": "https://mcp.heymetra.com/mcp" }
  }
}
```

_Leave the static OAuth fields empty — they exist for servers that cannot register themselves._

Full walkthrough: [heymetra.com/mcp/cursor/](https://heymetra.com/mcp/cursor/)
</details>

<details>
<summary><b>Antigravity</b> — ~/.gemini/config/mcp_config.json, or .agents/mcp_config.json in a project</summary>

```json
{
  "mcpServers": {
    "heymetra": { "serverUrl": "https://mcp.heymetra.com/mcp" }
  }
}
```

_The key is serverUrl, not url — the one every other JSON client spells differently._

Full walkthrough: [heymetra.com/mcp/antigravity/](https://heymetra.com/mcp/antigravity/)
</details>

## What it may and may not touch

Propose a change through this account's own API, for operations HeyMetra does not cover. Nothing is sent until you approve it, and HeyMetra cannot undo it afterwards.

Permissions are switched on per connection, and one you leave off is a tool your assistant never sees.

| Permission | What it covers | Changes anything? |
|---|---|---|
| **Included with the connection** | What HeyMetra needs to set the connection up and nothing more. It cannot be switched off on its own — removing the connection is how you withdraw it. | No, read only |
| **Direct API access** | Let your assistant use this account's own API for anything HeyMetra's other operations do not cover. It reads directly, and what comes back is the provider's own answer rather than a figure HeyMetra has checked. It can also propose changes — those are never applied until you approve them, and HeyMetra cannot undo one afterwards. | Yes — every change waits for your approval |

<details>
<summary>What each permission lets an assistant do, in full</summary>

- Ask this account's own API a question HeyMetra's other operations do not cover. Reads only, and the answer is the provider's own rather than a figure HeyMetra has checked.
- Propose a change through this account's own API, for operations HeyMetra does not cover. Nothing is sent until you approve it, and HeyMetra cannot undo it afterwards.
</details>

Anything that would change something comes back as a proposal you approve, inside bounds that live in code rather than in a prompt: ±50% on a budget, 5 campaigns per action and 20 changes a rolling day, and an approval that expires after 30 minutes. [How that works](https://heymetra.com/security/).

## When something goes wrong

<details>
<summary>It connects, and the CRM looks empty or much smaller than it is.</summary>

**Why:** The Zoho user who authorised it cannot see those records — a sharing rule, a territory, or simply a different organisation on a different data centre.

**Fix:** Disconnect and connect again as a user who can see them. Comparing one count against Zoho's own list view, signed in as that same user, tells you which of the two it is.

</details>

<details>
<summary>A field the team uses every day is missing from the answers.</summary>

**Why:** Custom fields are read from the module's own definitions, which needs the settings permission. Without it the standard fields still arrive and the custom ones silently do not.

**Fix:** Reconnect and grant all three permissions. The field tool lists what HeyMetra can currently see, which is the quickest way to tell whether a field is missing or merely empty.

</details>

<details>
<summary>Answers stop after a while and ask for a reconnect.</summary>

**Why:** The grant was revoked in Zoho, or the authorising user was deactivated. A connection is that person's access, so it ends when their access does.

**Fix:** Reconnect. If the person has left, connect as somebody who has not — the same reason the first step asks you to choose deliberately.

</details>

## What HeyMetra reads from Zoho CRM

Connect the CRM once and your MCP client gets one tool that reads it: lead counts for a period grouped by source, status, owner, day, or any field your own Leads module carries — the custom ones your team added included; every deal by stage, split into open (the forecast), won (revenue already realised) and lost, each with the value of the deals that state an Amount; the list of fields your own modules carry, custom ones included, so a report can be built on the fields this organisation actually uses; and, if you switch that permission on, what your call notes are about and who has been writing them, with the text of each note behind a second switch of its own. Deals with no Amount are counted, not valued, and the answer says how many — a pipeline is not worth less because somebody left a field empty. Zoho can separate reading from writing, so you choose which at connect time: a read-only connection is offered no tool that can change a record, and a read-and-write one proposes every change and waits for your approval.

<details>
<summary>About Zoho CRM</summary>

Zoho CRM manages your leads, contacts, and deals across the sales cycle. It’s the system of record for your pipeline and sales activity.
</details>

## One connection, not seven

The reason to read Zoho CRM through HeyMetra rather than through a server that only knows Zoho CRM is everything else it can answer in the same breath:

**Ads** — [Google Ads](https://heymetra.com/connectors/google-ads/) · [Meta](https://heymetra.com/connectors/meta-ads/)

**Analytics** — [Google Analytics 4](https://heymetra.com/connectors/google-analytics-4/) · [Google Search Console](https://github.com/zeisoft/google-search-console-mcp) · [PostHog](https://github.com/zeisoft/posthog-mcp)

**Ecommerce** — [Shopify](https://heymetra.com/connectors/shopify/) · [Trendyol](https://github.com/zeisoft/trendyol-mcp) · [WooCommerce](https://github.com/zeisoft/woocommerce-mcp)

**Revenue & CRM** — [Stripe](https://heymetra.com/connectors/stripe/) · [HubSpot](https://heymetra.com/connectors/hubspot/) · **Zoho CRM** · [Zoho SalesIQ](https://github.com/zeisoft/zoho-salesiq-mcp) · [Zoho Marketing Automation](https://github.com/zeisoft/zoho-marketing-automation-mcp)

**Mobile** — [AppsFlyer](https://github.com/zeisoft/appsflyer-mcp) · [RevenueCat](https://heymetra.com/connectors/revenuecat/) · [Adapty](https://github.com/zeisoft/adapty-mcp) · [App Store Connect](https://github.com/zeisoft/app-store-connect-mcp)

**Work** — [Google Calendar](https://heymetra.com/connectors/google-calendar/) · [Google Meet](https://heymetra.com/connectors/google-meet/) · [Jira](https://github.com/zeisoft/jira-mcp)

**Channels** — [Slack](https://github.com/zeisoft/slack-mcp) · [Telegram](https://github.com/zeisoft/telegram-mcp)

The full catalogue is at [heymetra.com/connectors/](https://heymetra.com/connectors/).

## Links

- [Zoho CRM connector page](https://heymetra.com/connectors/zoho-crm/)
- [HeyMetra](https://heymetra.com/) — what the product is
- [Setup for every assistant](https://heymetra.com/mcp/)
- [Security and limits](https://heymetra.com/security/)
- [Pricing](https://heymetra.com/pricing/)
- [HeyMetra's own repository](https://github.com/zeisoft/heymetra-mcp)

---

<sub>Built by <a href="https://zeisoft.com">Zeisoft</a>, who make HeyMetra. Not affiliated with Zoho CRM. This README is generated from HeyMetra's live connector catalogue and refreshed daily; corrections are welcome as issues.</sub>
