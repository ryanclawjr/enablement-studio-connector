# Enablement Studio for Cursor

This plugin connects Cursor to your Enablement Studio account. Ask Cursor to draft a training kit from a job posting, coach a call from its transcript, or critique a lesson outline, and the kits are saved to your Library on the site.

## What you need

- An Enablement Studio account with a confirmed email: https://enablementstudio.ai
- AI apps are in early access, so they may not be open for your account yet. If they are not, the guide explains how to ask.

## Install

- From the Cursor Marketplace: find Enablement Studio and install it. Cursor opens an Enablement Studio page in your browser to sign in and allow access.
- By hand: add the server to your `mcp.json`, then sign in when Cursor asks.

```json
{
  "mcpServers": {
    "enablement-studio": {
      "url": "https://enablementstudio.ai/mcp"
    }
  }
}
```

No client ID or secret is needed. The server uses OAuth with PKCE and registers Cursor on its own.

## What is in it

- The remote server at `https://enablementstudio.ai/mcp`, with nine tools.
- Three skills: `build-a-role-kit`, `coach-from-a-call` and `critique-a-lesson`. Each tells the agent which tool to call and to check the run until it is done.

## The tools

| Tool | What it does | Reads or makes |
| --- | --- | --- |
| `get_my_plan` | Shows your plan, how much of its allowance is used, and when it resets. | Only reads |
| `list_kits` | Lists your projects and the kits in them. | Only reads |
| `get_kit` | Reads one kit, in the order the site shows it, with its link. | Only reads |
| `get_example` | Reads the finished example kit for Role, Call or Critic. | Only reads |
| `draft_role_kit` | Starts a Role kit from a job posting, an SOP or a gap described in plain words. | Makes something new |
| `coach_call` | Starts coaching notes and one fix from a call transcript. | Makes something new |
| `critique_lesson` | Scores a lesson outline and rewrites its weakest part. | Makes something new |
| `get_run` | Checks where a run is, and gives the kit's link when it is done. | Only reads |
| `ask_specialist` | Asks one of a kit's specialists a question. A change it suggests waits in Review. | Makes something new |

## What it can and cannot do

It can see your plan and how much allowance is left, read your projects and kits, start Role, Call and Critic runs (these count against your plan), and ask a specialist about a kit. Any change a specialist suggests waits in Review until you apply it on the site.

It cannot apply or reject a change, rename, move or delete anything, or reach your account, billing or sign-in settings. Runs take pasted text only, not links or files.

## Your data

Only what the app sends when it uses a tool reaches Enablement Studio: the words it pastes for a run, a question for a specialist, and which kit, project or run it means. A kit a run makes is saved to your Library until you delete it. The words for a run go to the model provider (OpenAI) only if you ticked the box allowing it when you connected; without the tick, nothing goes to the provider. When an app reads a kit it receives everything in that kit, including any names in a transcript you pasted.

## Disconnect

Open Settings, then AI apps, on enablementstudio.ai. Under Connected apps, choose Disconnect next to Cursor. Access ends at once. Kits the app made stay in your Library. You can also remove the server in Cursor.

## Links

- Guide: https://enablementstudio.ai/ai-apps/guide
- Privacy policy: https://enablementstudio.ai/privacy
- Terms: https://enablementstudio.ai/terms
- Support: https://enablementstudio.ai/contact

## Security

Report a security problem as described in https://enablementstudio.ai/.well-known/security.txt (see also SECURITY.md).

## Licence

MIT. See LICENSE.
