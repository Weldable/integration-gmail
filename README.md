# @weldable/integration-gmail

Gmail send and search actions for Weldable.

Part of the [Weldable](https://weldable.ai/) integration library — see [@weldable/integration-core](https://github.com/weldable/integration-core) for the full catalog.

## Install

```bash
npm install @weldable/integration-gmail @weldable/integration-core
```

`@weldable/integration-core` is a peer dependency and must be installed alongside this package.

## Usage

```ts
import integration from '@weldable/integration-gmail'

// Search your inbox
const list = integration.actions.find(a => a.id === 'gmail.list_messages')!

const messages = await list.execute(
  { q: 'from:alerts@example.com is:unread', maxResults: 5 },
  ctx, // ActionContext from your Weldable-compatible host
)

// Send an email (RFC 2822 format, base64url-encoded)
const send = integration.actions.find(a => a.id === 'gmail.send_message')!

const raw = btoa(
  'To: alice@example.com\r\n' +
  'Subject: Weekly report\r\n' +
  'Content-Type: text/plain\r\n\r\n' +
  'Here is your weekly summary.'
).replace(/\+/g, '-').replace(/\//g, '_')

await send.execute({ raw }, ctx)
```

## Contributing and releasing

See [CONTRIBUTING.md](https://github.com/weldable/integration-core/blob/main/CONTRIBUTING.md) in `@weldable/integration-core` for the development workflow and release process.

## License

MIT
