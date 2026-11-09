# minik.cc for Claude and ChatGPT

minik.cc is a link shortener that shows where each link's visits come from. The minik.cc connector lets an AI assistant
work with your minik.cc account: make and edit short links, and answer questions about their visits.

## Set up

1. In Claude, open Settings → Connectors and choose minik.cc from the directory, then Connect. (In ChatGPT, open the minik.cc app and choose Connect.)
2. A minik.cc page opens. Sign in with your minik.cc account. If you do not have one, create it first at minik.cc.
3. The page shows your account and what the assistant may do: see your links, create and edit them, read visit stats, and change settings. Choose to allow.
4. Back in the assistant, ask a question. The first request may ask you to allow a tool; this is the assistant's own confirmation.

The server address, for clients that ask for it, is `https://minik.cc/mcp`. Sign-in uses OAuth 2.1 with PKCE.

## What it can do

- **Links:** create, find, edit, tag, archive, close; change many at once; delete archived links for good (always asked first). Options like a password, an end date or a visit limit are set per link.
- **Visit stats:** totals, time series, busy days and hours, and breakdowns by country, city, source, app, device, language and UTM tags. Counts only. Bots and link-preview opens are left out unless you ask.
- **Waves and events:** a wave is a sudden rise in a link's visits. An event is a dated note on a link's timeline, such as "Newsletter sent". minik.cc matches the two.
- **Channels and QR codes:** a channel is an extra short address, like `minik.cc/abc+ig`, that counts its own visits. QR codes carry their own channel.
- **Your own website:** the assistant can install a tracking script that sets no cookies, add goals and read results, including revenue per currency and the short link that brought each visit.
- **Everything else in the panel:** your own domains, share images, old short links (rb.gy, bit.ly), settings, and CSV import and export. Claude also has tools for the account's subscription.

## Example prompts

- "Which of my links got the most visits in the last 28 days?"
- "Where do the visits to my launch link come from? Show countries and sources."
- "Did any link have a sudden rise in visits lately? What happened that day?"
- "Show me the QR code for my event sign-up link."
- "Shorten https://example.com/guide, tag it Guide, and add an Instagram channel with the key ig."
- "How many people reached the thank-you page of my website, and which short links brought them?"

## Troubleshooting

- **The sign-in page says the connection could not be made.** Start the connection again from the assistant. The link on that page is only valid for the request that opened it.
- **The assistant says it is not allowed to do something.** The connection was approved without that permission. Remove the connection in Settings → API keys and connect again.
- **"This feature is not in your plan."** Some link options are not on every account. The reply says so, and the link is not changed.
- **Too many requests.** A connection may make 120 calls a minute. Wait a minute and ask again.
- **No wave shown.** A wave needs a link older than a week, and a day with at least three times its usual visits.

## Data and privacy

- The connector sees only the account that signed in, and only what that account's permissions allow.
- Visits are returned as counts. Single visits, IP addresses and visitor details are never returned; minik.cc does not store IP addresses.
- minik.cc sets no cookies on people who open a short link. The website script sets no cookies; it uses browser storage only if you switch on its 30-day setting.
- Servers are in Germany.
- End the connection at any time in minik.cc under Settings → API keys. Access stops at once.
- Full policy: https://minik.cc/gizlilik (Turkish).

## Support

hello@minik.cc. Include the time of the problem and, if you can, the assistant's message.


## Install

- **Claude (claude.ai, Desktop, mobile):** Settings → Connectors → minik.cc, or Add custom connector with `https://minik.cc/mcp`.
- **Claude Code:** `claude plugin marketplace add keremozcan/minik-plugin`, then `claude plugin install minik@minik`; or only the server: `claude mcp add --transport http --scope user minik https://minik.cc/mcp`.
- **ChatGPT:** the minik.cc app in the Plugin Directory.
- **Gemini CLI:** `gemini extensions install https://github.com/keremozcan/minik-plugin`.

## What is in this repository

| File | For |
|---|---|
| `.claude-plugin/plugin.json`, `.mcp.json`, `skills/minik/SKILL.md` | Claude plugin |
| `.codex-plugin/plugin.json`, `.mcp.json`, `skills/`, `assets/` | ChatGPT plugin |
| `gemini-extension.json` | Gemini CLI extension |

No keys or secrets: every client signs in to minik.cc with OAuth. The ChatGPT upload is a ZIP of its files only:

```sh
zip -r minik-chatgpt.zip .codex-plugin .mcp.json skills assets
```

minik.cc is made by [Space Island Ltd](https://spaceisland.ltd), registered in England and Wales (company no. 17270833). MIT licence.
