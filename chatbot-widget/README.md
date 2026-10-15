# Chatbot widget — host-page integration

A single-file HTML demo of the Authava chatbot widget's runtime integration API. Open the
hosted page in a browser and the on-page controls drive the embedded widget directly — no
build step, no bundler, no framework.

**Hosted:** [sample-integration.html](https://authava.github.io/authava-examples/chatbot-widget/sample-integration.html)
**Source:** [sample-integration.html](./sample-integration.html)

## What it demonstrates

The widget exposes a `window.AuthavaChatbot_<tenantId>` client once it dispatches the
`AuthavaChatbotReady` event. This page wires that client to six on-page controls:

| Control | Client call | Behaviour |
|---|---|---|
| **Send to Bot** | `client.sendMessage(text)` | Sends the textbox contents as if the visitor typed it. If the widget is closed, it opens first — so the visitor actually sees the message and the streaming reply. |
| **Show tooltip** / **Hide tooltip** | `client.showTooltip(text)` / `client.hideTooltip()` | Shows the launcher tooltip bubble with your text. Only visible while the widget is closed; dismisses on click. |
| **Set disclaimer** / **Clear disclaimer** | `client.setDisclaimer(text)` / `client.clearDisclaimer()` | Replaces the banner at the top of the chat with your text. "Clear" reverts to whatever the bot settings specify. |
| **Update presets** / **Clear presets** | `client.setPresetQuestions(lines)` / `client.clearPresetQuestions()` | Replaces the suggestion chips at the bottom of the chat with the lines of your textarea. |
| **Show Bot Window** / **Hide Bot Window** | `client.open()` / `client.close()` | Opens or closes the widget programmatically. |

Full API reference lives in the [widget repo's README](https://github.com/authava/chatbot-widget#api-reference).

## Point it at your tenant

The default tenant is Authava's public demo. To exercise the controls against your own bot,
append `?tenantId=<your-uuid>`:

```
https://authava.github.io/authava-examples/chatbot-widget/sample-integration.html?tenantId=00000000-0000-4000-a000-000000000001
```

Nothing is persisted — the override only affects that tab.

## Copying it into your own page

The whole page is ~150 lines of plain HTML + a `<script type="module">` block. View source,
copy the parts you need (the `AuthavaChatbotReady` listener and the handler wiring),
and drop them into your own site. The widget's loader `<script src="https://cdn.authava.com/chatbot.js" data-id="<your-tenant-id>">` is the only runtime dependency.
