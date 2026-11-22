<p align="center">
  <img src="assets/logo.png" alt="WireUp logo" width="110" />
</p>

<h1 align="center">WireUp for Gemini</h1>

<p align="center">
  <strong>Your own WhatsApp in Gemini CLI and the Gemini app.</strong><br />
  Catch up on chats, search old messages, open photos and voice notes, and draft replies that wait for your approval.
</p>

<p align="center">
  <a href="https://wireup.chat">Website</a> ·
  <a href="https://wireup.chat/connect/gemini-cli">Setup guide</a> ·
  <a href="#example-prompts">Examples</a> ·
  <a href="#faq">FAQ</a> ·
  <a href="https://wireup.chat/privacy">Privacy</a>
</p>

---

## What is WireUp?

[WireUp](https://wireup.chat) connects your own WhatsApp account to the AI assistant you already use. You sign in with Google, link WhatsApp once by scanning a QR code (the same way you link WhatsApp Web), and add one connector link. There is nothing to install or keep running on your computer.

This repository is a [Gemini CLI extension](https://geminicli.com/extensions) for WireUp: it adds the hosted WireUp connector and a short context file that tells Gemini how to use it well. It contains no server code, no account data and no credentials. The connector itself is hosted at `https://wireup.chat/mcp`.

## Set it up

First, create your account at [wireup.chat](https://wireup.chat): sign in with Google and scan the QR code with WhatsApp (**Settings → Linked devices → Link a device**).

### Gemini CLI

Install the extension:

```bash
gemini extensions install https://github.com/eitza-tech/wireup-for-gemini
```

Then start Gemini CLI, type `/mcp auth wireup`, and sign in with the same Google account.

Prefer not to install an extension? Add the connector directly instead:

```bash
gemini mcp add --transport http --scope user wireup https://wireup.chat/mcp
```

### The Gemini app (gemini.google.com)

Where Google has turned on custom apps for your account:

1. Open **Settings → Connected apps** and choose to add a custom app.
2. Paste `https://wireup.chat/mcp`.
3. Approve the connection and sign in with the same Google account.

Google is rolling custom apps out gradually, so the option may not show for every account yet.

## Example prompts

| Goal | Ask Gemini |
|---|---|
| Catch up | "What did I miss on WhatsApp today?" |
| Summarize a group | "Summarize this week in my family group. Anything I need to answer?" |
| Find something | "When did Dana send me the address for Sunday?" |
| Voice notes | "What did my brother say in his last voice note?" |
| Draft a reply | "Draft a reply to Sam saying I'll be 10 minutes late." |
| Send a file | "Send ./invoice.pdf to the project group." |

## What it can do

| Area | Tools |
|---|---|
| Catch up and read | `catch_up`, `list_chats`, `read_chat`, `load_older_messages`, `list_statuses` |
| Search | `search_messages`, `search_contacts`, `group_info`, `message_info` |
| Photos, voice notes and files | `get_media` (voice notes and documents come back as text) |
| Send, always as a draft first | `send_message`, `send_media` (photos, stickers, GIFs, voice notes, files), `send_poll`, `send_location`, `forward_message`, then `confirm_send` |
| Manage | `react_to_message`, `edit_message`, `delete_message`, `chat_settings`, `mark_as_read` |
| Status | `whatsapp_status` |

## Sending stays in your hands

- Every send is a draft until you confirm it, unless you turn confirmation off yourself.
- Messages go only to chats you already have, with a daily limit and an off switch.
- Reading your chats never marks them as read on your phone.

## FAQ

**Is it free?** Yes, WireUp is free for now.

**Is this an official WhatsApp product?** No. WireUp links to your account as a linked device, the same way WhatsApp Web does. It is not made by, affiliated with or endorsed by WhatsApp or Meta, and it doesn't use the WhatsApp Business API. Use it for your own conversations and within WhatsApp's terms.

**Where are my messages kept?** In a storage space that belongs to your account alone, so Gemini can catch you up and search even when your phone is slow to answer. You can keep only the last 30 days, six months or a year, and delete everything at any time from your dashboard. What Gemini reads is processed by Google as part of your conversation. Details: [wireup.chat/privacy](https://wireup.chat/privacy).

**Can I use it in other AI apps too?** Yes. See [WireUp on GitHub](https://github.com/eitza-tech/wireup) for every app.

## Troubleshooting

| What you see | What to do |
|---|---|
| "WhatsApp is not linked" | Open [wireup.chat](https://wireup.chat) and scan the QR code again. |
| Gemini CLI says WireUp needs sign-in | Run `/mcp auth wireup`. |
| A send was refused | Check the daily limit and the sending switch on your dashboard. |

## Support

Email [contact@eitza.tech](mailto:contact@eitza.tech).

## Trademarks and license

WhatsApp is a trademark of Meta Platforms, Inc. Gemini is a trademark of Google LLC. WireUp is an independent service by Eitza Tech and is not affiliated with, sponsored or endorsed by Meta, WhatsApp or Google.

The files in this repository are released under the [MIT License](LICENSE). The WireUp service itself is not open source.
