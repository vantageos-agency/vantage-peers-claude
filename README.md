# VantagePeers for Claude

Add it in claude.ai: **Customize > Plugins > Add marketplace**, paste
`https://github.com/vantageos-agency/vantage-peers-claude`, then install **vantage-peers**.

What it gives you:

- The VantagePeers Cloud connector (`https://mcp.vantagepeers.com/mcp`). You sign in with your
  VantagePeers account the first time Claude uses it; no key is stored in the plugin.
- Skills:
  - `my-tasks`: List my open tasks and my agent's open tasks in VantagePeers.
  - `delegate-a-task`: Give a task to my agent in VantagePeers.
  - `message-my-agent`: Send a message to my agent in VantagePeers.
  - `remember-a-decision`: Record a decision in VantagePeers so that it is not lost.
  - `recall-what-was-decided`: Find what was decided or recorded in VantagePeers on a subject.

## ChatGPT

The same skills and the same connector are packaged for ChatGPT beside the Claude files, in
`plugins/vantage-peers/`: `plugin.json` and `mcp.json` (the Agent Plugins format that
[OpenAI documents](https://developers.openai.com/plugins/build/plugins)). The five skills live
once, in `plugins/vantage-peers/skills/`; both manifests read that folder.

Connect it in ChatGPT, following OpenAI's
[connection steps](https://developers.openai.com/plugins/deploy/connect-chatgpt):

1. Go to <https://chatgpt.com/plugins>, select the plus button, then **Add custom MCP server**.
2. Enter a name and description. Under **Connection**, enter the server URL with its `/mcp` path:
   `https://mcp.vantagepeers.com/mcp`.
3. Choose OAuth for authentication, review the risk warning, select **I understand and want to
   continue**, then **Create as a plugin**.
4. Sign in with your VantagePeers account. At the consent screen, choose your organisation and,
   if the screen offers it, the agent you connect as.
5. Start a new conversation and select the plugin with `@`.

Which ChatGPT plans can add and use a custom MCP server is OpenAI's to state; see
<https://help.openai.com/en/articles/12584461> and
<https://developers.openai.com/plugins/deploy/connect-chatgpt> ("Account and workspace policies
apply to adding and using custom MCP servers"). What we observed: on 2026-10-31 an account on the
ChatGPT Free plan connected through this connector and wrote to VantagePeers. Check your own plan
and workspace policy.

VantagePeers Cloud only. Your data stays in your organisation's workspace.

Support: hello@vantageos.agency. License: see `LICENSE` (Functional Source License 1.1,
Apache 2.0 future license).
