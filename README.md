# Studio Board

A one-person studio dashboard for a 3D business with two divisions: **3D Agency** (client work) and **3D Creative** (your own products and content). Open `index.html` in a browser and it works. Everything is saved in your browser. Nothing leaves it except the messages you send to an AI you connect yourself.

## Files

| File | What it is |
|---|---|
| `index.html` | The whole app |
| `joy-data.json` | Joy's costs, settings and price list. Edit it freely |
| `joy-database-en.json` | Joy's chat database: questions and answers she knows. Edit it freely |
| `assets/` | Optional role pictures, named `mira.png`, `rico.png`, `dewi.png`, `sasha.png`, `bima.png`, `nadia.png`, `arga.png`, `joy.png` (`.webp`, `.jpg` and `.jpeg` also work) |

## The tabs

| Tab | What it does |
|---|---|
| Overview | What is overdue, what is due this week, money due and expected |
| Chat | A group chat for each step and a private chat with every role |
| Team | The eight roles and their skills |
| Board | Tasks with status, owner and due date |
| Money | Income and expenses per division, and what you actually kept |
| Decisions | A log of decisions with reasons, disagreement and a revisit date |
| Studio brain | Your goals, brand notes and open questions |

## The team

Seven roles use an AI: Mira (art director), Rico (producer), Dewi (PM), Sasha (marketing), Bima (copywriter), Nadia (client relations) and Arga (finance). You talk to one role at a time.

**Joy** is the eighth and never uses an AI. She runs inside the page, so she costs no quota and always answers.

## Connecting an AI

Click **AI** at the top right and add a key. Supported: Claude, Gemini, Grok, Groq (GroqCloud) and Other (any OpenAI-compatible address).

1. Pick the provider and paste the key.
2. Click **Test connection**. The app loads your model list and picks a model your account can use. For Groq it prefers `llama-3.1-8b-instant`.
3. Under "Who uses which AI", leave it on Automatic or choose a key for each role.

Without a key the app writes each prompt for you to copy into any AI app, and you paste the answer back. Keys stay in this browser and are not included in backups. A Groq key used under "Other" goes to OpenRouter and fails with 401, so use the Groq provider.

## Saving quota

The defaults use about 300 to 450 tokens and 1 request per message:

- One role at a time. There is no "Everyone" option.
- Studio brain, last 5 decisions and open tasks are off. Turn them on under "What goes into each prompt" when a question needs them.
- Earlier messages included is 4. Reply length is Short and capped.
- "Try another connected AI if one fails" is off.
- "Let the AIs propose board changes" is on, but the board instructions are only added to a prompt when your message is about tasks, money or decisions, so normal chat pays nothing for it. Proposed changes are never saved until you press **Add selected to the board**.
- Use Joy for lookups, sums and checklists.

## Joy

Joy reads your Board, Money, Decisions and Studio brain, plus her own data in `joy-data.json`. She never makes up a figure. Open her from Team or Private chats, then tap a button or type a question.

| Ask | You get |
|---|---|
| `deadlines`, `what is overdue` | Overdue, due today, next 7 days, later |
| `tasks`, `tasks for Mira`, `what is in review` | Tasks by status, with progress |
| `money`, `who owes me` | Received, due, expected, expenses, what you kept |
| `decisions`, `decisions about pricing` | Logged decisions with reasons and revisit dates |
| `brain`, `goals` | Your Studio brain notes |
| `pricing` | A short chat that works out what to charge (below) |
| `price list`, `price list ad` | Your Indonesia and Fiverr packages |
| `my costs` | Monthly and yearly costs, and your day and hour rates |
| `price 6jt cost 1.5jt hours 30` | Profit, margin and real hourly rate |
| `price 6jt fee 15%` | What a marketplace pays out |
| `rate 200k hours 30 cost 500k` | Minimum quote and a version with a revision buffer |
| `30 hours in 10 days` | Hours per day and whether it fits |
| `checklist`, `delivery checklist`, `intake checklist`, `launch checklist`, `scope checklist` | Questions to answer with y or n, then a score and what to fix |
| `guide revisions`, `guide late payment`, `guide pricing` | Step by step playbooks |
| `template decline`, `template payment reminder` | A message with `[brackets]` to fill in |
| `hi`, `i am tired`, `tell me a joke` | A chat answer from her database (below) |
| `teach: question => answer`, `teachings`, `forget 3` | Teach Joy a new answer, list what she knows, or remove one |
| any other word, such as `halloween` | A search across tasks, money, decisions, costs, brain and chats |

Numbers can be written `6jt`, `6.000.000`, `500k`, `7.5M` or `Rp 1,500,000`. Add `agency`, `creative` or `both` to choose a division. For a checklist, answer in one line, for example `y n y y n y y y`.

Joy's replies are kept out of other roles' AI prompts. Tick **Joy's offline replies** under "What goes into each prompt" to include them.

### The pricing chat

1. Joy asks what the project is.
2. She asks how many work days it will take in total, revisions included: `6 days`, `1.5 weeks` or `40 hours`.
3. She asks about anything that changes the price: `rush`, `commercial rights`, `source files`, `2 extra revisions`, `indonesia` or `fiverr`, and `budget 2jt` for what the client offers. Say `none` to skip.

Or in one line: `pricing ad 7 days fiverr rush budget 2jt`. Say `cancel` to stop.

The result gives a **floor** (below it you lose money), a **healthy** price (covers costs and savings), a **quote** (matches your income goal) and an **opening ask**, in rupiah and as a Fiverr dollar price with what you keep after fees. It also shows the nearest package from your price list. If you give a client budget, Joy says go, negotiate or no, and how many work days that budget buys.

The price is only as good as your day estimate.

## Joy's data

Joy's numbers live in `joy-data.json`: your monthly costs, settings (billable hours, savings, income goal, dollar rate, Fiverr fee and the extra percentages) and your services with their Basic, Standard and Premium prices in rupiah and dollars. Each field is explained in the file. The same data is also built into `index.html`, as a fallback.

- **Hosted:** keep `joy-data.json` next to `index.html`. The page reads it the first time Joy needs her data.
- **Opened as a local file:** browsers block the page from reading the file, so use **Import data** in Joy's chat to load it.
- **Once loaded, your copy wins.** Joy saves her data in your browser with the rest of the app and includes it in backups. Editing `joy-data.json` later does not overwrite it, so press **Import data** to load the new file.
- **Export data** downloads your current numbers as `joy-data.json`.
- **Adding a service:** add an entry under `services` with a short `id`, a `name`, some `keywords` that Joy listens for, and its `tiers`. Then import the file.
- **Starting over:** type `reset joy data`, then `reset joy data confirm`.

Quick changes without editing the file:

| Type | Effect |
|---|---|
| `set cost boarding 450k` | Change a cost. A new name adds one |
| `add cost phone 100k`, `remove cost phone` | Add or remove a cost |
| `set billable 70`, `set workdays 22` | Billable hours and work days a month |
| `set savings 15%`, `set salary 6jt` | Savings share and monthly income goal |
| `set fx 16500`, `set fee 20`, `set conv 3` | Dollar rate, Fiverr fee, payout and conversion cost |
| `set rush 30`, `set rights 25`, `set source 10`, `set revisions 0.5` | Extras used by `pricing` |
| `set price ad standard indonesia 3.5jt` | One package price. Markets: `indonesia`, `fiverr` |

The prices in the file are starting points from a web check and your own costs. The 3D modelling prices are estimates with no market data behind them.

## Joy's chat database

Joy can chat without an AI. Her answers come from a list of questions and answers saved in your browser. She matches what you write even with typos or small wording changes. Her tracker commands (`pricing`, `set cost`, `price list`, `my costs`) always run first.

- **Teach her:** `teach: how much is a logo => 25 dollars || around 400k`. Use `||` for several answers; she picks one at random.
- **When she does not know:** she asks what she should say. Reply with the answer, or `skip`.
- **See and remove:** `teachings` lists everything. `forget 3` removes number 3.
- **Hosted:** keep `joy-database-en.json` next to `index.html`. The page loads it once and saves it in your browser.
- **Opened as a local file:** use **Import chat DB** in Joy's chat. **Export chat DB** downloads your current list, including what you taught.
- Format: `{"version": 1, "joyDb": [{"q": "hi", "a": ["Hello!", "Hey there!"]}]}`
- Your chat database is saved with the rest of the app and is included in backups.

## Your data

- Saved in this browser's local storage. Clearing site data erases it, so export a backup now and then. Backups include Joy's data and exclude AI keys.
- Anyone who can use this browser profile can read your saved keys and notes.
- A provider only sees your messages when you connect an AI. Google may use free-tier Gemini data to improve its products, so keep client details and money figures out of a free Gemini key.

## Running it

No build step. Open `index.html`, or put the files on any static host. The page contacts only the AI providers you add (Anthropic, Google, xAI, Groq, OpenRouter), and its own `joy-data.json` and `joy-database-en.json`. These are allowed by the Content-Security-Policy tag at the top of the file.

## Editing Joy's wording

Joy's code is one block in `index.html`, marked `Joy: the role that never calls an AI`. The checklists (`CHECKS`), guides (`GUIDES`) and message templates (`TEMPLATES`) are plain lists in that block. Edit the wording and she uses it right away.
