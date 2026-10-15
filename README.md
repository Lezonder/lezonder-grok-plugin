# Lezonder for Grok Bot

See last night's Lezonder Sleep Score and whether your week is getting better, right in Grok.
This plugin connects Grok Bot to the hosted Lezonder MCP server so Grok can read your latest score
and your dated scores for up to seven days.

Works with your existing Lezonder account. The plugin is free; it does not create accounts, sell
memberships or take payments.

## What it can read

Two read only tools, nothing else:

| Tool | Returns |
|---|---|
| `get_latest_result` | Date and Lezonder Sleep Score of your latest visible result, or nothing if there is none. |
| `get_sleep_trend` | Dated Lezonder Sleep Scores for the last 1 to 7 local days (default 7). Missing days are left out. |

It never returns tickets, draw or prize information, raw tracker or Apple Health records, sleep
stages, email, account details, payments, or anyone else's data. It cannot change anything in your
account. Results are informational, not medical advice.

## Connect

1. Install Lezonder from the Grok Bot marketplace and click **Authenticate**.
2. Sign in with your Lezonder account at `accounts.lezonder.com`.
3. Read the permission screen. It asks only to share your dated Lezonder Sleep Scores with the
   app named on that screen. Approve it if you agree.

Then ask, for example:

- "What is my latest Lezonder Sleep Score?"
- "Show my Lezonder sleep scores for the last seven days."
- "Compare my latest Lezonder Sleep Score with my last three days."

Some results return a sharing permission error until the permission for their data source is
confirmed. Your score in the Lezonder app is not affected.

## Technical details

- Server: `https://www.lezonder.com/mcp` (Streamable HTTP), the only network endpoint.
- Sign in: OAuth 2.1 authorization code with PKCE (S256) at `https://clerk.lezonder.com`, using a
  pre-registered public client. Scopes: `lezonder:mcp:results:read` and `offline_access` only.
- Resource metadata: `https://www.lezonder.com/.well-known/oauth-protected-resource/mcp`.
- This repository holds no secrets, hooks, scripts or code that runs on your machine.

## Privacy, support and disconnecting

- Privacy: <https://www.lezonder.com/mcp-privacy>
- Support: <https://www.lezonder.com/mcp-support> or hello@lezonder.com
- Terms: <https://www.lezonder.com/terms-of-service>

Remove the plugin in Grok Bot to disconnect. For help revoking the authorization, email
hello@lezonder.com.

## License

MIT. See [LICENSE](LICENSE).
