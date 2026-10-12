# Studio Board

A one-person studio dashboard for a 3D business with two divisions: **3D Agency** (client work) and **3D Creative** (your own products and content). It is a single HTML file. Open it in a browser and it works. Everything is saved in your browser, nothing is uploaded anywhere except the messages you send to an AI you connect yourself.

## What is in it

| Tab | What it does |
|---|---|
| Overview | What is overdue, what is due this week, money due and expected |
| Chat | Group chats by step and a private chat with every role |
| Team | The eight roles and their skills |
| Board | Tasks with status, owner and due date |
| Money | Income and expenses per division, with what you actually kept |
| Decisions | A log of decisions with reasons, disagreement and a revisit date |
| Studio brain | Your goals, brand notes and open questions |

## The team

Seven roles use an AI: **Mira** (art director), **Rico** (producer), **Dewi** (PM), **Sasha** (marketing), **Bima** (copywriter), **Nadia** (client relations) and **Arga** (finance).

**Joy** is the eighth role and never uses an AI. See below.

## Joy: the role that needs no AI

Joy runs inside the page. She needs no key, sends no request and uses no quota, so she always answers, even when every AI is out of messages. She reads only what you keep in the Board, Money, Decisions and Studio brain tabs, and she never makes up a figure.

Open her from Team or from Private chats, then tap a button or type a question.

| Ask | What you get |
|---|---|
| `deadlines`, `what is overdue`, `due this week` | Overdue, due today, next 7 days, later |
| `tasks`, `tasks for Mira`, `what is in review` | Tasks grouped by status, with progress |
| `money`, `who owes me`, `profit` | Received, due, expected, expenses, what you kept |
| `decisions`, `decisions about pricing` | Logged decisions with reasons and revisit dates |
| `brain`, `goals` | Your Studio brain notes |
| `price 6jt cost 1.5jt hours 30` | Profit, margin and real hourly rate |
| `price 6jt fee 15%` | What a marketplace pays out |
| `rate 200k hours 30 cost 500k` | Minimum quote, plus a version with a revision buffer |
| `price 6jt deposit 30%` | Deposit and balance |
| `30 hours in 10 days` | Hours per day, skipping weekends, and whether it fits |
| `checklist`, `delivery checklist`, `intake checklist`, `launch checklist`, `scope checklist` | Questions to answer with y or n, then a score and the gaps to fix |
| `guide revisions`, `guide late payment`, `guide pricing` | Step by step playbooks |
| `template decline`, `template payment reminder` | A message with `[brackets]` to fill in |
| any other word, such as `halloween` | Search across tasks, money, decisions, brain and chats |

Tips:
- Numbers can be written `6jt`, `6.000.000`, `500k`, `7.5M` or `Rp 1,500,000`.
- Add `agency`, `creative` or `both` to pick a division. Without it, Joy follows the division selected on the left.
- For a checklist, reply with the answers in one line, for example `y n y y n y y y`. Joy scores it and lists what to fix.
- Joy's replies are not sent to any AI by default. To let an AI see them, tick **Joy's offline replies** under "What goes into each prompt".

## Connecting an AI

Click **AI** at the top right and add a key. Supported providers: Claude, Gemini, Grok, **Groq (GroqCloud)** and Other (any OpenAI-compatible address).

1. Pick the provider and paste the key.
2. Click **Test connection**. The app loads your model list and picks a model your account can use. For Groq it prefers `llama-3.1-8b-instant`, which does not spend tokens on hidden thinking.
3. Under "Who uses which AI", leave it on Automatic or pick a key for each role.

Keys are stored only in this browser and are never included in backups. Without a key, the app writes each prompt for you to copy into any AI app, then you paste the answer back.

Note: a Groq key used with "Other" is sent to OpenRouter by default and fails with 401. Use the **Groq** provider instead.

## Saving quota

The defaults are set to use as few tokens as possible, about 300 to 450 per message and 1 request per message.

- You talk to **one role at a time**. There is no "Everyone" option.
- Studio brain, last 5 decisions and open tasks are **off**. Turn them on under "What goes into each prompt" only when a question needs them.
- **Earlier messages included** is 4. **Reply length** is Short and capped.
- **Let the AIs propose board changes** and **try another connected AI if one fails** are off.
- For `gpt-oss` models on Groq the app asks for low reasoning effort.
- Use Joy for anything that is a lookup, a sum or a checklist.

## Role pictures

Put one image per role in a folder called `assets` next to the HTML file, named after the role in lowercase: `mira`, `rico`, `dewi`, `sasha`, `bima`, `nadia`, `arga`, `joy`. The page tries `.png`, `.webp`, `.jpg` and `.jpeg`. If none is found it shows the colored initial.

## Your data

- Saved in this browser's local storage. Clearing site data erases it, so export a backup now and then.
- Anyone who can use this browser profile can read your saved keys and notes.
- Messages go to a provider only when you connect an AI, and only to that provider. Google may use free-tier Gemini data to improve its products, so keep client details and money figures out of a free Gemini key.

## Running it

Open `index.html` in a browser, or put it on any static host. No build step. It makes requests only to the AI providers you add (Anthropic, Google, xAI, Groq, OpenRouter), which the page's Content-Security-Policy allows.

## Changing Joy

Joy lives in one block in the HTML file, marked `Joy: the role that never calls an AI`. The checklists (`CHECKS`), guides (`GUIDES`) and message templates (`TEMPLATES`) are plain lists near the bottom of that block. Edit the wording or add an entry, and she uses it right away.
