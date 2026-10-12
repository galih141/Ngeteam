The new index.html is ready. It adds the AI button at the top right with a status dot, and it opens a key popup like your screenshot. I haven’t tried it with real keys from Google or xAI. I tested it against simulated providers and in a real Chromium browser (desktop and phone width).

The AI popup

Several keys: Claude, Gemini, Grok, plus an “Other” option. “+ Add another key” adds more, and two keys from the same provider are fine.
Test connection: it loads that provider’s model list into the model box, then sends one tiny message to check the model answers. It shows “Connected, key works”, or a plain reason if not: wrong key, over quota, or the provider can’t be reached.
Who uses which AI: each role picks its best match automatically (Rico on Claude, Mira on Gemini, Sasha on Grok). You can override any role.
Behavior toggles: automatic replies, board changes, and fallback to another AI when one runs out of messages. Fallback is off by default because it sends your prompt to a different company.

What changes in the chat

Replies now arrive in the chat by themselves, one at a time, so each role sees what the one before said.
If a reply fails, the card shows why. You can try another AI, or copy the prompt by hand as before.
The AIs can propose tasks, money records and decisions, but nothing is saved until you approve it, and Undo removes what was added.
Each role may only propose what its job allows. Only Arga can propose money records, and the division always follows the chat, never the AI.

Keys and security

Keys stay in your browser’s storage and are never in backups. Clear data keeps them.
Anyone who can use that browser profile can read them. A security rule in the file also stops the page from sending data anywhere except the four provider hosts.

What I couldn’t verify

I could only confirm Claude’s browser access live. Gemini should work, since your screenshot shows another app doing it. Grok may block direct browser calls. If Test connection says “Could not reach Grok”, use the “Other” provider with an OpenRouter key.
Test results will tell you quickly: Gemini first, since it’s free.
Claude’s API isn’t free. Google may use free-tier Gemini data, so keep client and money details out of a free key.
