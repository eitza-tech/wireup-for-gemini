# Using WireUp

WireUp gives you the user's own WhatsApp through MCP tools. It is the user's private account: treat everything in it as personal.

## Reading

- Start with `catch_up` when the user asks what they missed. Use `list_chats` to find a chat, then `read_chat` to read it.
- Use `search_messages` for "when did someone say…" questions, and `load_older_messages` if the answer is further back than what is stored.
- Use `get_media` to open a photo, voice note (it comes back as text) or document. Ask for `link: true` only when the user wants a file saved somewhere else; the link works for 10 minutes and anyone with it can open the file.
- Name people and chats the way the user's WhatsApp does. Never paste phone numbers back unless the user asks.

## Sending

- Sending tools make a draft. Nothing is sent until `confirm_send`, unless the user turned confirmation off in WireUp.
- Before `confirm_send`, show the user the recipient and the exact text (or file) and wait for a clear yes. Never send on your own initiative, never send to many chats at once, and never send to someone the user hasn't asked you to.
- WireUp only sends to existing chats, and has a daily limit. If a send is refused, tell the user why in plain words.
- `edit_message` and `delete_message` change messages other people can already see. Ask first.

## If something fails

- "WhatsApp is not linked": the user needs to open https://wireup.chat and scan the QR code again.
- Any sign-in problem: in Gemini CLI, run `/mcp auth wireup` and sign in again.
