# Agentline NZ

Give your AI assistant its own email inbox: send, read and catch sign-in codes. Texting coming soon.

## What your assistant gets

- **Its own email address** ending in `@agentline.nz`, separate from yours.
- **Sending email.** Your assistant can write and send email from that address, for example replies, bookings and confirmations. It should check with you before it sends anything.
- **Reading email.** It can see what has arrived, open a message and keep track of what it has already dealt with.
- **Sign-in codes.** When a website emails a one-time code, your assistant can wait for it and pick it up, so it can finish signing up or logging in without you copying codes across.
- **Texting is coming soon.** It isn't available yet. You can join the waitlist on the [pricing page](https://agentline.nz/pricing#texting).

Agentline NZ works with AI assistants that support MCP (Model Context Protocol), such as Claude, ChatGPT, Cursor, VS Code and many others.

## Get started

1. **Create an account** at [agentline.nz](https://agentline.nz/signup?ref=github).
2. **Add Agentline NZ to your AI assistant** using this address:

   ```
   https://agentline.nz/mcp
   ```

3. **Sign in when asked.** Your assistant opens an Agentline NZ sign-in page. Sign in and approve access. There's nothing to copy or paste.

Step-by-step guides for each assistant are in the [docs](https://agentline.nz/docs).

## Pricing

See [agentline.nz/pricing](https://agentline.nz/pricing) for current plans and the free trial.

## For developers

### Connection

| | |
| --- | --- |
| MCP endpoint | `https://agentline.nz/mcp` |
| Transport | Streamable HTTP |
| Auth | OAuth 2.1 with PKCE. Discovery starts from the `WWW-Authenticate` header on the 401 response. Dynamic Client Registration and Client ID Metadata Documents are supported. |
| Scopes | `messages:read`, `messages:send`, `offline_access` |
| Without OAuth | Send an API key from your dashboard as `Authorization: Bearer <key>` |

Example for Claude Code:

```sh
claude mcp add --transport http agentline https://agentline.nz/mcp
```

Example config for clients that use an `mcpServers` file:

```json
{
  "mcpServers": {
    "agentline": { "url": "https://agentline.nz/mcp" }
  }
}
```

### Tools

Email and codes:

| Tool | What it does |
| --- | --- |
| `get_my_inbox` | Your assistant's `@agentline.nz` address, plan and remaining email allowance. Call this first. |
| `send_email` | Send an email from your `@agentline.nz` address (up to 5 recipients). |
| `list_emails` | Recent emails, newest first. Filter by direction, unread only, or time. |
| `read_email` | The full text of one email. Reading doesn't mark it as read. |
| `mark_read` | Mark emails as read, or unread. |
| `wait_for_code` | Wait for a one-time code to arrive by email and return it. Each code is returned once. |

Account:

| Tool | What it does |
| --- | --- |
| `get_profile` | Which Agentline NZ account is connected. |
| `list_api_keys` | List API keys (prefix, name, last used). |
| `create_api_key` | Create an API key. The secret is shown once. |
| `revoke_api_key` | Revoke an API key. |
| `list_audit_log` | Recent account events, such as sign-ins, sends and key changes. |
| `get_billing` | Plan, status, trial end date and allowances. |
| `get_checkout_link` | A link for the account owner to start a plan. It's emailed to the owner; the assistant can't pay. |
| `get_billing_portal_link` | A link for the account owner to update their card, switch plan or cancel. |

Some assistants, such as ChatGPT, show a smaller set of these tools.

### Keyless endpoint

`https://agentline.nz/public/mcp` needs no sign-in and can't send email. It offers `get_pricing`, `get_docs`, `get_install_instructions` and `signup`, which lets an assistant create an account for its person. The person then gets an email to confirm.

## Links

- Website: [agentline.nz](https://agentline.nz)
- Docs: [agentline.nz/docs](https://agentline.nz/docs)
- Pricing: [agentline.nz/pricing](https://agentline.nz/pricing)
- Terms: [agentline.nz/terms](https://agentline.nz/terms)
- Privacy: [agentline.nz/privacy](https://agentline.nz/privacy)
- Support: [support@agentline.nz](mailto:support@agentline.nz)

## Licence

[MIT](LICENSE). This repository holds the listing details for the hosted Agentline NZ service. It doesn't contain the service's source code.
