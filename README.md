# ACP adapter for Codex

Use [Codex](https://github.com/openai/codex) from [ACP-compatible](https://agentclientprotocol.com) clients such as [Zed](https://zed.dev)!

This tool implements an ACP adapter around the Codex CLI, supporting:

- Context @-mentions
- Images
- Tool calls (with permission requests)
- Following
- Edit review
- TODO lists
- Slash commands:
  - /review (with optional instructions)
  - /review-branch
  - /review-commit
  - /init
  - /compact
  - /logout
  - Custom Prompts
- Client MCP servers
- Auth Methods:
  - ChatGPT subscription (requires a paid subscription; in Zed remote/headless projects this uses device-code login)
  - CODEX_API_KEY
  - OPENAI_API_KEY

Learn more about the [Agent Client Protocol](https://agentclientprotocol.com/).

## How to use

### Zed

The latest version of Zed can already use this adapter out of the box.

To use Codex, open the Agent Panel and click "New Codex Thread" from the `+` button menu in the top-right.

Read the docs on [External Agent](https://zed.dev/docs/ai/external-agents) support.

#### Testing a custom build in Zed

If you want to try a fork or prerelease build before it lands in Zed's registry:

1. Download the `codex-acp` binary for your platform from the Releases page.
2. Put the binary on the machine where Zed will run the agent. For remote SSH projects, that means the remote host, not your local machine.
3. Add it as a custom external agent in your Zed settings:

```json
{
  "agent_servers": {
    "codex-acp-dev": {
      "type": "custom",
      "command": "/absolute/path/to/codex-acp",
      "args": [],
      "env": {}
    }
  }
}
```

Then open the Agent Panel, choose `codex-acp-dev`, and sign in. In remote/headless projects, `Login with ChatGPT` opens terminal auth and uses a device code.

### Other clients

Or try it with any of the other [ACP compatible clients](https://agentclientprotocol.com/overview/clients)!

#### Installation

Install the adapter from the latest release for your architecture and OS: https://github.com/zed-industries/codex-acp/releases

You can then use `codex-acp` as a regular ACP agent:

```
OPENAI_API_KEY=sk-... codex-acp
```

Or via npm:

```
npx @zed-industries/codex-acp
```

## License

Apache-2.0
