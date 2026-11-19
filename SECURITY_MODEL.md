# Security model

Threat model for the Enablement Studio connector plugin. This repository is the Cursor-plugin half of the owner's **studio-connector** component; the OAuth and MCP server it points at lives in the private Enablement Studio repository. Answers from the owner are marked **(owner)**. Devin security scans rank their findings against this model, so edit it when the connector or its priorities change. To report a vulnerability, see [`SECURITY.md`](SECURITY.md).

## System overview and trust boundaries

The plugin ships `mcp.json` (the MCP server URL `https://enablementstudio.ai/mcp`), `.cursor-plugin/plugin.json`, and the skills in `skills/*/SKILL.md` (build-a-role-kit, coach-from-a-call, critique-a-lesson). Cursor connects to the server with OAuth 2.1 and PKCE, using dynamic client registration; the account owner approves on a consent page. Trust boundaries:

1. **AI client -> connector server**: OAuth discovery, registration, authorize, token and `/mcp` are internet-reachable; only allow-listed accounts can sign in.
2. **Connector server -> Enablement Studio**: the server calls the Studio over a service binding; the user's kits, runs and plan live there.
3. **This repository -> users' editors**: the URL and skill text are executed or followed by agents on users' machines (supply-chain and integrity surface).

## Entry points

The nine MCP tools: `get_my_plan`, `list_kits`, `get_kit`, `get_example`, `draft_role_kit`, `coach_call`, `critique_lesson`, `get_run`, `ask_specialist`. There are no apply, delete, billing or sign-in-settings tools.

## Assets

**(owner)** Critical: Enablement Studio accounts and kits (may contain employee or customer data), and model spend.

- OAuth tokens and consent records.
- The integrity of the server URL and skill instructions shipped to users.

## Attacker profiles

**(owner)** All of these matter.

1. A malicious or compromised AI agent or OAuth client: cross-account kit reads, allowance or spend abuse, consent bypass, token theft through redirect URIs.
2. Malicious content inside kits, transcripts or lessons steering the agent (prompt injection through tool output).
3. Supply chain: a tampered `mcp.json` URL or skill text.

## Existing controls

PKCE, account allow-list, per-account connector sign-in cap, spend ceilings and a separate model key for connector work, a read-and-generate tool set with no destructive actions.

## Out of scope / accepted risk

**(owner)** Nothing is out of scope or accepted risk for the original repositories; this repository is held to the same answer by inference until the owner confirms.
