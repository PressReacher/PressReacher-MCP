<div align="center">

![PressReacher](./assets/logo.png)

**Official MCP server for PressReacher**

Find UK journalists, verify emails, and build media lists from your AI assistant

[![MCP](https://img.shields.io/badge/MCP-2025--03--26-blue?style=flat-square)](https://modelcontextprotocol.io/)
[![Transport](https://img.shields.io/badge/Transport-Streamable%20HTTP-green?style=flat-square)](https://pressreacher.com/api/mcp/)
[![Works with](https://img.shields.io/badge/Works%20with-Claude%20%7C%20ChatGPT%20%7C%20Grok%20%7C%20Gemini%20%7C%20Cursor-purple?style=flat-square)](#connecting-your-ai-assistant)
[![License](https://img.shields.io/badge/License-MIT-orange?style=flat-square)](./LICENSE)

[Website](https://pressreacher.com) • [Documentation](https://pressreacher.com/mcp/) • [Pricing](https://pressreacher.com/pricing/)

</div>

---

## What You Can Do

Ask your AI assistant in plain language:

> **"Find 50 UK technology journalists with working emails and add them to a new collection called AI Startups"**

> **"Search for journalists who recently wrote about sustainable fashion. Show me their contact details and open rates."**

> **"Check if this email address is deliverable: editor@example.com"**

> **"List my media alerts and show me my latest coverage stats"**

> **"Create a draft campaign for my Spring Launch collection"**

The PressReacher MCP connector gives Claude, ChatGPT, Grok, Gemini, Cursor, and other AI assistants access to:

- 🔍 **Search journalists** by country, beat, outlet, or article coverage
- ✉️ **Verify email addresses** (any email, not just journalists)
- 📋 **Build and manage media lists** with smart filtering
- 📊 **View campaign stats** and coverage reports
- 📝 **Create draft campaigns** and media alerts

All tools are scoped to your PressReacher account and respect your plan limits.

![PressReacher Search](./assets/discover-screenshot.png)

---

## Quick Start

**Endpoint:** `https://pressreacher.com/api/mcp/`

Choose your authentication method based on your AI assistant:

<details>
<summary><b>🔵 Claude (OAuth)</b></summary>

<br>

1. Open Claude → **Settings** → **Connectors** → **Add custom connector**
2. Paste the endpoint URL:
   ```
   https://pressreacher.com/api/mcp/
   ```
3. Click **Connect** and sign in with your PressReacher account
4. Click **Allow** on the consent screen

That's it! No token management needed.

**To revoke access:** Go to [PressReacher Settings → MCP](https://pressreacher.com/dashboard/settings/mcp) and disconnect the app.

</details>

<details>
<summary><b>🟢 ChatGPT (OAuth)</b></summary>

<br>

1. Open ChatGPT → **Settings** → **Beta features** → **Custom connectors**
2. Click **Add connector** and paste:
   ```
   https://pressreacher.com/api/mcp/
   ```
3. Sign in with your PressReacher account when prompted
4. Authorize the connection

OAuth handles authentication automatically.

**To revoke access:** Go to [PressReacher Settings → MCP](https://pressreacher.com/dashboard/settings/mcp) and disconnect the app.

</details>

<details>
<summary><b>⚫ Grok (Bearer Token)</b></summary>

<br>

1. Generate a Bearer token:
   - Go to [PressReacher Settings → MCP](https://pressreacher.com/dashboard/settings/mcp)
   - Click **Create token**
   - Copy the token (format: `pr_mcp_...`)

2. Add the MCP server in Grok:
   - Navigate to **Settings** → **Integrations**
   - Add remote MCP server with URL:
     ```
     https://pressreacher.com/api/mcp/
     ```
   - Set authorization header:
     ```
     Authorization: Bearer <your-token>
     ```

**To revoke access:** Delete the token from [PressReacher Settings → MCP](https://pressreacher.com/dashboard/settings/mcp).

</details>

<details>
<summary><b>💎 Gemini (Bearer Token)</b></summary>

<br>

1. Generate a Bearer token:
   - Go to [PressReacher Settings → MCP](https://pressreacher.com/dashboard/settings/mcp)
   - Click **Create token**
   - Copy the token (format: `pr_mcp_...`)

2. Add the extension in Gemini:
   - Go to **Extensions** → **Custom**
   - Add PressReacher connector with URL:
     ```
     https://pressreacher.com/api/mcp/
     ```
   - Configure authentication with your Bearer token

**To revoke access:** Delete the token from [PressReacher Settings → MCP](https://pressreacher.com/dashboard/settings/mcp).

</details>

<details>
<summary><b>🔷 Cursor (Bearer Token)</b></summary>

<br>

1. Generate a Bearer token:
   - Go to [PressReacher Settings → MCP](https://pressreacher.com/dashboard/settings/mcp)
   - Click **Create token**
   - Copy the token (format: `pr_mcp_...`)

2. Add MCP server in Cursor:
   - Open Cursor settings
   - Navigate to MCP configuration
   - Add remote server with URL:
     ```
     https://pressreacher.com/api/mcp/
     ```
   - Configure authorization header with your token

**To revoke access:** Delete the token from [PressReacher Settings → MCP](https://pressreacher.com/dashboard/settings/mcp).

</details>

<details>
<summary><b>🔧 Other MCP Clients (Bearer Token)</b></summary>

<br>

For any MCP-compatible client:

1. Generate a Bearer token at [PressReacher Settings → MCP](https://pressreacher.com/dashboard/settings/mcp)
2. Configure your client with:
   - **URL:** `https://pressreacher.com/api/mcp/`
   - **Transport:** Streamable HTTP (JSON-RPC over POST)
   - **Auth:** `Authorization: Bearer <your-token>`
   - **Protocol:** `2025-03-26`

</details>

---

## Available Tools

### Read-Only Tools

| Tool | Description |
|------|-------------|
| `get_account` | View your plan, limits, and current usage |
| `search_journalists` | Search by country, beat, outlet, keywords, or article coverage |
| `search_journalists_by_articles` | Find journalists who wrote about specific topics |
| `get_journalist` | Load a journalist profile by name or ID |
| `get_journalist_emails` | List email addresses for a journalist (Agency/Enterprise) |
| `list_collections` | View your journalist collections (media lists) |
| `get_collection` | Load a collection with all journalists |
| `list_campaigns` | View your email campaigns |
| `get_campaign_stats` | Get sent, opened, clicked, and bounced counts |
| `list_media_alerts` | View your news alerts |
| `get_coverage_stats` | View coverage totals for your clients |
| `list_coverage_reports` | List your coverage reports |
| `list_email_templates` | View available email templates |
| `list_team_members` | List team members (Agency/Enterprise) |
| `verify_email` | Check if any email address is deliverable |

### Write Tools

| Tool | Description |
|------|-------------|
| `create_collection` | Create a new journalist collection |
| `rename_collection` | Rename or update a collection description |
| `add_journalists_to_collection` | Add journalists to a collection (max 100 at once) |
| `copy_collection` | Copy a collection to a new private list |
| `create_campaign` | Create a draft campaign (does NOT send) |
| `create_media_alert` | Create a news alert for keywords |

### Destructive Tools (Require Confirmation)

| Tool | Description |
|------|-------------|
| `remove_journalists_from_collection` | Remove journalists from a collection |
| `share_collection_with_team` | Share a collection with a team member (Agency/Enterprise) |
| `delete_collection` | Permanently delete a collection |

All tool parameters and detailed descriptions are available in the [full documentation](https://pressreacher.com/mcp/).

---

## Rate Limits & Plans

Rate limits are per user per hour:

| Plan | Tool Calls/Hour | Email Verification/Day | Draft Campaigns/Day | Media Alerts |
|------|-----------------|------------------------|---------------------|--------------|
| **Freelancer** | 60 | 200 | Blocked | 10 (daily only) |
| **Agency** | 200 | 1,000 | 10 | 50 |
| **Enterprise** | 500 | 5,000 | Unlimited | 200 |

**Note:** MCP is available on **paid plans only** — not available on trials.

[View full pricing details →](https://pressreacher.com/pricing/)

---

## FAQ

<details>
<summary><b>Can I send email campaigns through MCP?</b></summary>

<br>

No. The `create_campaign` tool creates **draft campaigns only**. Drafts are never sent automatically. You must log into the PressReacher dashboard to review, edit, and manually send campaigns.

</details>

<details>
<summary><b>How many journalists can I search for?</b></summary>

<br>

Search results are paginated (max 20 per page). Use the `nextCursor` token to fetch more results.

</details>

<details>
<summary><b>Does this work with email addresses outside the journalist database?</b></summary>

<br>

Yes! The `verify_email` tool works with **any email address**, not just journalists in the PressReacher database. You can verify up to 10 addresses per call.

</details>

<details>
<summary><b>What's the difference between OAuth and Bearer token authentication?</b></summary>

<br>

- **OAuth (Claude, ChatGPT):** Sign in once with your PressReacher account. The app manages tokens automatically.
- **Bearer token (Grok, Gemini, Cursor):** You generate and configure a static token manually. Revoke it anytime from the dashboard.

Both methods have the same rate limits and access to the same tools.

</details>

<details>
<summary><b>Can I use MCP on a trial account?</b></summary>

<br>

No. MCP is only available on **paid plans** (Freelancer, Agency, Enterprise). Trial accounts cannot connect.

</details>

<details>
<summary><b>What fields are marked "untrusted"?</b></summary>

<br>

Fields like bios, job titles, and outlet descriptions come from third-party sources. They're marked `untrusted` in API responses and should be treated as data, not instructions.

</details>

<details>
<summary><b>How do I revoke access?</b></summary>

<br>

Go to [PressReacher Settings → MCP](https://pressreacher.com/dashboard/settings/mcp) and:
- For OAuth apps: Click **Disconnect**
- For Bearer tokens: Click **Revoke token**

Access is revoked immediately.

</details>

<details>
<summary><b>Where can I see the full API specification?</b></summary>

<br>

The MCP server implements the [Model Context Protocol specification](https://modelcontextprotocol.io/) version `2025-03-26` with Streamable HTTP transport.

- **Server metadata:** `GET https://pressreacher.com/api/mcp/`
- **OAuth metadata:** `GET https://pressreacher.com/.well-known/oauth-protected-resource`
- **Full documentation:** [https://pressreacher.com/mcp/](https://pressreacher.com/mcp/)

</details>

---

## Support

Questions or issues? Contact **abbie@pressreacher.com**

---

## License

This documentation is provided under the MIT License. See [LICENSE](./LICENSE) for details.

---

<div align="center">

**[PressReacher](https://pressreacher.com)** • **[MCP Documentation](https://pressreacher.com/mcp/)** • **[Pricing](https://pressreacher.com/pricing/)**

Built in the UK 🇬🇧 • UK-built PR software to find journalists, send personalised pitches, and track coverage

</div>
