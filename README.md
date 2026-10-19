# authava-examples

Public, self-contained integration examples for Authava's SDKs and widgets. Nothing in this
repo talks to a private backend or holds a secret — every page here can be opened directly
from the GitHub Pages URL below and exercised against the public demo tenant.

## Hosted examples

| Example | URL | What it demonstrates |
|---|---|---|
| Chatbot Widget — host page integration | [sample-integration.html](https://authava.github.io/authava-examples/chatbot-widget/sample-integration.html) | Driving the embedded chat widget from your own page UI: send messages programmatically, show/hide the launcher, override the tooltip, replace the disclaimer, and update the preset-question chips at runtime. |

## Repo layout

```
chatbot-widget/
  sample-integration.html   ← the demo page
  README.md                 ← what the page demonstrates + how to adapt it to your tenant
```

Each example subfolder has its own README with the specific setup, tenant-id override pattern,
and screenshots where useful.

## Pointing an example at your own tenant

Every example that embeds the chatbot widget accepts a `?tenantId=<your-uuid>` query parameter.
No code edits needed — just append the parameter to the hosted URL:

```
https://authava.github.io/authava-examples/chatbot-widget/sample-integration.html?tenantId=<your-tenant-id>
```

## Contributing

Keep every example self-contained — a single HTML file, no build step, no secrets. The whole
point of this repo is that a prospect can view-source and understand the integration in minutes.
Open a PR against `main` and GitHub Pages will republish on merge.
