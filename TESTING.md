# Testing this plugin

Time needed: about five minutes. Access is in early access, set per email address, so use the reviewer account from the submission's testing instructions (the password is given there, not here). That account is already allowed and holds three kits: "Instructional Designer" (Role), "Discovery call, Harborline Payments" (Call) and "Explain interchange" (Critic). No emailed code is needed.

## Connect

1. In your browser, sign in at https://enablementstudio.ai/login with the reviewer account.
2. In Cursor, install this plugin, or add this to `mcp.json`: `{"mcpServers":{"enablement-studio":{"url":"https://enablementstudio.ai/mcp"}}}`. Then choose Authenticate on the enablement-studio server.
3. Your browser opens an Enablement Studio page. Check that it says you are signed in as the reviewer account. Tick the box "Send what I write in Cursor to OpenAI to draft kits and answer questions." It is unticked by default; without it the plugin can read kits but cannot start runs or ask specialists. Choose Allow. A short page, "Going back to Cursor", returns you to Cursor; if your browser asks to open Cursor, allow it.

## Try it

In a Cursor agent chat:

1. "What is my Enablement Studio plan and how much allowance is left?" Tool: `get_my_plan`.
2. "List my Enablement Studio kits." Tool: `list_kits`. Returns the three kits above.
3. "Open the Harborline Payments call kit and tell me the one fix it recommends." Tool: `get_kit`. Returns the kit's text, marked as the person's material, and a link to the kit.
4. "Show me the finished example Critic kit." Tool: `get_example`.
5. "Ask the quiz specialist on my Instructional Designer kit to make the second question harder." Tool: `ask_specialist`. This can take up to a minute. If the specialist proposes a change, the reply says it waits in Review. Open the link, signed in as the same account, to see it under Review: nothing changes until a person chooses Apply there.
6. "Coach this call and tell me the one thing to fix: Alex Rivera: Before I talk product, how do you take cards today? Jordan Kim: A local ISO. Weekends at the market, payouts lag. Alex Rivera: What happens when a payout slips? Jordan Kim: I stay late and my baker waits on flour money. Alex Rivera: Thursday at ten to review the notes together? Jordan Kim: Works." Tools: `coach_call`, then `get_run` if it is still running. Returns a link to a new Call kit in the Library.
7. Optional, about three minutes: "Draft a training kit for new support agents who keep escalating billing questions they could answer themselves." Tools: `draft_role_kit`, then `get_run`.

## What to expect

- Cursor may ask before a run or a specialist question: those four tools use the account's allowance.
- A run may say it was drafted offline by the Studio's own rules and give the reason (the plan's allowance is used, or the day's AI limit is reached). That is expected, and the kit is still saved.
- Runs are limited to 10 an hour and 30 a day for one account.

## Disconnect

Open https://enablementstudio.ai/settings/ai-apps while signed in, then choose Disconnect next to Cursor. Access ends at once.
