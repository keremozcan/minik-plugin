---
name: minik
description: Use minik.cc for short links, sharing a link in a place (WhatsApp, Instagram story or bio, newsletter, poster/QR, a campaign), questions about visits (how many, from where, did the campaign work, best time to post), weekly updates, and adding visit tracking or goals to the person's own website. Triggers on "kısalt", "link hazırla", "kaç kişi girdi", "kampanya", "minik", "short link", "UTM", "QR".
---

# minik.cc through an assistant

minik is run by talking. The person should never need the panel, and should rarely need to answer a question.

## How to behave

- Act on what you can work out. Pick titles, channel words (insta, wa, bulten, x, linkedin) and campaign words (kasim, lansman, yaz2026) yourself: short, lowercase, no spaces. Never ask for a link id: every tool takes a short code (`abc`) or a short address (`minik.cc/abc`).
- Ask before deleting, closing, cancelling, or anything that costs money.
- Reply in the person's language. minik's own messages are Turkish.
- After a task, offer one next step in a single sentence. Don't list menus.

## Which tool

| The person says | Call |
|---|---|
| "minik", "neler yapabilirim?", "bu hafta nasıldı?", opens without a clear ask | `get_briefing` (`tour: true` for "what can you do?") |
| "WhatsApp'a hazırla", "Instagram hikâyem için link", "kampanya linkleri", "afişe QR" | `share_link` with `url` or `link`, `places`, optional `campaign`; then write each message ready to copy |
| "şunu kısalt" | `create_link` (it gives the existing link back for a page already shortened) |
| "kaç kişi girdi?", "nereden geldiler?", "kampanya işe yaradı mı?", "karşılaştır", "ne zaman paylaşmalıyım?" | `show_report` with `link` / `links` / `campaign` / `tag` and `focus`; answer in one or two sentences, the card shows the charts |
| "minik'i siteme ekle" | `setup_site` (find the hostname and platform in the repository first), edit the files it names, then `check_site`; `add_goal` for a sign-up or sale |
| "kendi alan adımla" | `connect_domain`; add the DNS record yourself if you have a DNS tool |
| "her pazartesi özet" | offer to schedule a task that runs the `haftalik-ozet` prompt; or `update_settings` `weeklyDigest: true` for the e-mail |

## Words

- Labelled address: `minik.cc/abc+insta.story:kasim` is link `abc`, channel `insta`, sub-channel `story`, campaign `kasim`. Works at once; nothing to save. Visits count apart and the destination gets UTM tags.
- Event (olay): a dated note on a link's timeline ("bülten gitti"). Wave (dalga): a sudden rise in visits.
- Goal (hedef): something a visitor does on the person's site (sign-up, purchase), counted per link that brought them.

## Slash commands

`/minik:baslarken`, `/minik:haftalik-ozet`, `/minik:paylas`, `/minik:kampanya`, `/minik:rapor`, `/minik:kampanya-sonucu`, `/minik:siteme-ekle`, `/minik:tasi` come from the server as MCP prompts.
