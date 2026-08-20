# Casper — Idea document

Working name: **Casper Play** (AI in chat: **Casper**)  
Status: idea / brainstorm (not a repo yet)  
Purpose of this file: capture product, business and technology so it can later be used as input to Cursor when a first repo is created.

This is a living document. Open questions are marked with **TBD**.

---

## 1. One-liner

Casper Play is a **chat-first phone app** with two tabs: **Connect** (groups, private chats, and event bubbles that organise social play) and **Play** (a session chat that runs the night on court). Pickleball first. Formats are generic enough for other racket sports later.

**Client:** Expo (React Native) on iOS and Android.  
**Backend:** AWS (Cognito, Lambda, API Gateway, DynamoDB, SES, CDK), region `eu-north-1` first, worldwide later.  
**AI:** OpenAI with tool calling, on demand only. Formats and standings are backend code.

The person who uses AI pays — 3 months free, then **49 kr/month**, cancel anytime. Players in a group or session can **read** without paying.

**UI language:** English first. The app is built for more languages; **Swedish is the first extra locale**.

Early installs: **Apple Developer + TestFlight** (internal testing), not the App Store.

---

## 1.1 Naming (do this before App Store Connect / bundle id)

**Working name (chosen for now): Casper Play.** The bot in the thread is **Casper** (“Ask Casper”). Store / home screen: **Casper Play**. Not a legal clearance — still do the cheap checks below before App Store Connect.

The **Apple Developer account** can be a person or company (seller name ≠ app name). Next identifiers to pick once checks pass: **bundle id**, **domain**, **EAS slug**.

### What we are naming

Two tabs, both chat, plus an AI the organiser *asks*:

- **Connect** — groups, “I’m in”, who is actually here  
- **Play** — format, scores, table, last-minute swaps  
- **AI + chat** — Casper speaks when asked; it is not a booking website  

A good name either **is the companion** you tap (“Ask Casper”) or **is the place** (the club-night chat). Putting “AI” in the name will age badly.

Avoid pickleball slang (*Dink*, *Kitchen*). **Rally**, **Reclub**, **Pralley**, **PicklePear** already sit on that shelf.

### Test: “Ask ___” vs home-screen word

| Kind | Works as | Example |
|---|---|---|
| **Character** | Ask Casper / Hey Caddie | Feels like a helper in the thread |
| **Place / product** | Open ClubNight | Feels like the two tabs |
| **Split** | App = ClubNight, bot = Casper | Often the cleanest |

### Already crowded (skip or fight)

| Name | Why not (quick look) |
|---|---|
| **Casper** alone | Mattress, ghost, **Casper Wallet** on the App Store |
| **PlayChat** | Casual games + voice chat app |
| **Courtly** | Padel booking (BG) |
| **OnCourt** | Racquet club/tournament software |
| **I'm In** | Friends & plans app (also uses AI to plan) |
| **Huddle** | Several sports/social apps |
| **Volley** | Video messaging app |
| **InPlay** | Betting term |
| **Clubhouse** | Famous audio app |

**Casper Play** did not show up as an existing pickleball/chat product. Still in the Casper trademark neighbourhood, but more specific than “Casper”.

### Brainstorm by what we do

**A — The companion (AI in the chat)**

| Name | Why it fits | Watch |
|---|---|---|
| **Casper Play** | Character + the Play tab; still say “Ask Casper” | Casper neighbourhood; two words on the icon |
| **Hey Casper** | Exactly the Connect action | Informal; Casper still in search |
| **Ask Casper** | Matches the product literally | Long; “Ask” apps exist |
| **Caddie** | Helper beside you on court; sport-agnostic | Golf; spelling Caddy vs Caddie |
| **Captain** | The person who pays and asks the AI | Military / aviation apps |
| **Skipper** | Same idea, slightly warmer | Boats |
| **Cue** | The AI prompts the next game | Thin meaning; hard to search |
| **Second** | Tennis “second”; a partner in the chat | Easy to miss |

**B — Connect (I’m in / who’s here)**

| Name | Why it fits | Watch |
|---|---|---|
| **ShowUp** | RSVP *and* on-site | Generic verb |
| **DropIn** | Real term for social play | Drop-in clinics, other apps |
| **OnSite** | The last-minute roster | Generic; offices |
| **MixIn** | “I’m in” + mixed social partners | Mix as in audio |
| **Lineup** | Tonight’s list | Concerts / police |
| **Roster** | Same | Sports-admin dry |
| **WalkIn** | Hall walk-ups | Clinics |
| **WhosIn** | The Connect question | Ugly as a word; domain luck |

**C — Play (the night on court)**

| Name | Why it fits | Watch |
|---|---|---|
| **ClubNight** | What captains actually run | Long; “club” is everywhere |
| **NextCourt** | “You’re up” | Clear, a bit literal |
| **NextUp** | Same | Many apps |
| **Rotate** | Americano / social formats | Dry |
| **Shuffle** | Last-minute redraw | Spotify shuffle |
| **Playtab** | The two tabs | Meta; “tab” is UI jargon |
| **Rounds** | RR / americano rounds | Drinking; boxing |
| **SideOut** | Racket feel | Volleyball |

**D — Chat as the product**

| Name | Why it fits | Watch |
|---|---|---|
| **Playroom** | A room to connect and to play | Kids’ room |
| **Thread** | Everything lives in chat | Slack/email |
| **Clubthread** | Group + night | Invented, a bit long |
| **NightChat** | Club night in a chat | Dating-app vibe |
| **The Desk** | Tournament desk in your pocket | Cold, hotel-like |

**E — Invented / compact (EN + SV easy)**

| Name | Notes |
|---|---|
| **Casplay** | Casper + Play in one word; still “Ask Casper” in the UI |
| **Playlo** | Soft, empty of collisions at a glance |
| **Coura** | Court-ish; invented |
| **Kortly** | *Kort* = court in Swedish; English-first UI may hide that |
| **Inne** | Swedish “in”; too local for an English-first product |

Do **not**: PlayAI, CourtAI, ChatGPT-for-pickleball.

### A tighter shortlist to argue about

Keep **Casper Play**. Add only names that still sound like *this* app:

1. **Casper Play** — companion + Play. Split optional: icon “Casper”, store “Casper Play”.  
2. **Hey Casper** — the button we already designed.  
3. **ShowUp** — Connect *and* on-site. Bot can still be Casper.  
4. **DropIn** — social-play English. Same split.  
5. **ClubNight** — the thing you run every Thursday.  
6. **MixIn** — I’m in + rotating partners.  
7. **Caddie** — helper on court; “Ask Caddie”.  
8. **Casplay** — one word if two-word Casper Play is too long on the icon.  
9. **NextCourt** — Play-tab literal, very clear.  
10. **Playroom** — both tabs are rooms.

### Check before locking

1. App Store and Play, **exact** name  
2. `name.app` / `name.se`  
3. Instagram / TikTok  
4. EUIPO / USPTO / PRV class 9 + 42 (collisions, not legal advice)  
5. Bundle id: `se.<name>.app` or `com.<name>.app`

**TBD:** exact bundle id (candidate `se.rabbiteye.casperplay`). Domains **casperplay.app** and **casperplay.com** are registered (GoDaddy). Other names in the brainstorm stay as discarded alternatives, not the brand.

---

## 2. Problem

Social racket sports already happen in WhatsApp / Messenger groups. The painful part is not “finding a chat”. It is:

1. **Connect** — who is in tonight? Who dropped? Who is standing in the parking lot right now?
2. **Play** — we have *N* players, *C* courts, *T* minutes. Make a fair format *now*. Then keep score and show a table without a spreadsheet on someone’s phone.

Existing tournament tools assume a planned event: fixed draw, named teams, DUPR IDs collected days ahead. They break when:

- 14 people said yes, 11 showed up, 2 more walk in
- one court is taken by a lesson
- someone has to leave after 40 minutes
- the organiser is also playing and has no laptop

Casper is built for that moment: **minutes before, and during, social play** — and for the groups that lead up to it (including focused ones like “Skill 4+ Sundays 9–12”).

We do **not** bolt Casper onto WhatsApp. We build our own chat, and we **share out** (invite links, event cards, recaps) to other messengers so groups can still recruit there.

---

## 3. Who it is for

### Primary (v1)

- **Organiser (paid / trial)** — has a Casper membership and a role that may use AI. Creates events, asks Casper, starts Play, registers scores in the Play chat.
- **Group creator / admin** — creates groups, invites, toggles quiet mode, assigns who may organise. Can always post in the group. Often the same person as the organiser.
- **Player (free)** — member of a group or participant in a Play session. Can read Connect/Play they belong to, **RSVP**, **like** an event, use **private chats**. Does not pay. Does not invoke AI.

### Secondary (later)

- Other racket sports using the same formats (padel, badminton, table tennis)
- DUPR-rated social nights
- Halls / clubs as organisations (not required for v1)

**Sport:** v1 is **pickleball**. Every event/session has `sport: "pickleball"`. Formats themselves are sport-agnostic. Adding padel later should be a sport tag + scoring defaults, not a rewrite.

First users are likely Swedish / Nordic pickleball groups, but the **product UI is English**. Copy, format names, and default Casper prompts are English. **i18n from day one**; Swedish (`sv`) is the first translation. Device language can switch to Swedish; missing keys fall back to English. Code, API, and DynamoDB stay English.

---

## 4. Product shape: two tabs, both chat

```
Casper (Expo app)
├── Tab: Connect
│     ├── Groups          e.g. "Skill 4+ Sundays 9–12"  (quiet mode on/off)
│     ├── Private chats   1:1 — always available, not affected by group quiet mode
│     └── In a group: messages + **event bubbles** (RSVP, like)
└── Tab: Play
      └── Session chats   from an event, or scratch (no event)
```

Inbox is split by **job**: organising vs running the night. Chat must feel native: no laggy composer, optimistic send, keyboard that stays put, stick-to-bottom while Casper streams.

### 4.1 Groups and private chats

Someone **creates a group** (a digital club, or a slice of one). Then people **join** (link / code) or creator/admins **invite**.

Groups can be narrow on purpose:

- “Skill 4+ Sundays 9–12”
- “Thursday social — Hall X”
- “Beginners Wednesday”

Invite the right people to the right group. **Weekly events** live in that group as repeating event bubbles.

**Private chats** sit in the same Connect tab: 1:1 between members. Quiet mode on a *group* does **not** turn off DMs. People should still be able to message each other privately and RSVP on events.

Casper is not sitting in every DM. **TBD:** Ask Casper from a private chat vs Play tab only.

This is not “a hall’s official club” unless they choose to be. It is **groups of people who play together**.

### 4.2 Roles, membership, and who may use AI

Two gates, both required to create events / Ask Casper / start Play / register scores via AI:

1. **Group role** that is allowed to organise (creator, admin, or an “organiser” role)
2. **Personal Casper membership** (trial or paid) — **AI use is what you pay for**

| | No membership (free player) | Trial / paid membership |
|---|---|---|
| **Member** | Read group + events they are in. RSVP. Like event. Private chats. View Play if participant. | Same; may organise only if the **group role** allows it |
| **Creator / admin / organiser role** | Can read and post (admins); **cannot** call Casper until trial/pay | Create event, Ask Casper, start Play, register scores via AI |

**Players do not pay.** They can read Connect and Play threads they belong to.

If the organiser stops paying, AI actions stop. Existing groups, events, and Play records stay **readable**. **TBD:** exact grace behaviour.

### 4.3 Connect — Casper on tap; quiet mode is a group switch

Casper is **not** always listening. Organiser starts it with **Ask Casper** or **Create Event**.

Events **live in the chat as bubbles**: date, time, place, courts, RSVP counts, likes, share, Start Play.

Players on an event bubble can always:

- **RSVP** (in / out / maybe)
- **Like** the event (optional, lightweight interest)

**Weekly events:** a group like “Skill 4+ Sundays 9–12” can post the next bubble on a schedule.

#### Quiet mode (creator toggles on/off)

Per **group**, not a global app setting. Creator turns it on so the group is not used as a second WhatsApp.

| | Quiet **off** | Quiet **on** |
|---|---|---|
| Creator / admin **post** in the group | Yes | **Yes, always** |
| Member free-chat in the group | Yes | **No** (hard block; lean this way) |
| Member **RSVP** | Yes | **Yes** |
| Member **like** event | Yes | **Yes** |
| **Private 1:1 chats** | Yes | **Yes** — unchanged |

DMs and RSVP (and likes) stay. The noisy *group* thread is what quiet mode shuts down. Admins can still announce (“court 3 is wet, we start 15 min late”).

### 4.4 Play — from event or scratch

Play is a **new chat**, created when someone with role + membership starts a session.

Two entry points:

1. **From an event bubble** — roster copied from Connect. Last-minute drop/add still works.
2. **From scratch** — **allowed.** No Connect event. Organiser starts a format with the people who are here. Always an **organiser**. **Participants can view**.

Play membership = **organiser + participants of this session**, not the whole Connect group.

Job of Play:

- AI interviews the organiser: courts, names, DUPR or not, format, scoring, time
- Backend **generates** the session (catalogue only)
- Live table and next games in the Play chat
- Swap who is actually here
- **Register scores via AI** (see below)
- End session → stored on the organiser; participants can view

#### Scores (open, with a chosen AI path)

**Decided for the AI path:** the organiser asks Casper to register a score **to the right match**, because the Play chat **shows on screen which match it is**. The model must bind “11–8” to that match (court / round / pairing in context), then call the backend `record_result`. It must not invent a match.

**Still open:** may a **player** also tap or type a score, or only the organiser via AI?

Standings and next round after a recorded result are **engine**, not LLM.

During play also: substitute, late arrival, someone leaving, pause/drop a court, undo last score.

### 4.5 Data ownership and visibility

| Thing | Stored / owned | Who can see |
|---|---|---|
| **Group** | Creator / admins | Members |
| **Private chat** | The two users | Those two |
| **Connect messages + event bubbles** | The group | Members (read). RSVP/like: members. AI: organiser with membership |
| **Event** | Organising person; usually a group | Group members |
| **Play session + Play chat** | Organising person | Organiser + participants can view |
| **Match history** | Under organiser, linked to players | Organiser; each participant for sessions they played |

Scratch Play: `sourceEventId` is null. Still `organiserId` + `participantIds`.

### 4.6 Sharing (out), not bridging (in)

Own chat. No WhatsApp Business bridge.

Share: group invite, event bubble link, **Open in Casper** (universal/app link into Expo), optional recap image.

A small **web landing page** (CloudFront) is only for those links — not the chat UI.

### 4.7 What stays where

**Connect:** groups, DMs, event bubbles, weekly rhythm, quiet groups.  
**Play:** courts, table, AI score registration, swaps, recap — including scratch sessions.

---

## 5. Experience principles

1. **Two chats, two jobs.** Connect organises people. Play runs the night.
2. **Events are bubbles in a group**, not a separate admin website.
3. **Casper speaks when asked** (Ask Casper / Create Event / Play setup / register score).
4. **Quiet mode is a group toggle.** Admins still post. Members still RSVP, like, and DM.
5. **AI use is the paid act.** Readers (players) stay free.
6. **Scratch Play is first-class.** No event required. Organiser + participants can view.
7. **Score goes to the match on screen.** AI + tool call, then engine updates the table.
8. **AI never invents a format** (or a match that is not in the current round).
9. **Last-minute is first-class.**
10. **Deterministic format engine.** Testable.
11. **History is queryable** from stored sessions, scoped by organiser + participation.
12. **Share out, stay in.**
13. **Ordinary Connect messages do not hit OpenAI.** Play score registration does, by design.
14. **Chat must feel native.** Optimistic send, native keyboard and list, reconnect after lock screen. Expo exists so this is not a Safari PWA.
15. **English UI, ready for more languages.** Swedish first. Never hard-code user-visible strings in components.

---

## 6. Formats (backend-owned)

Formats are **versioned code** behind an API. The model may only choose from this catalogue and pass parameters.

Formats are **not pickleball-specific**. Scoring defaults may be (`sport: pickleball` → games to 11, win by 2, doubles).

Proposed v1 catalogue:

| Code | Name | When it fits |
|---|---|---|
| `americano` | Americano | Mixed partners, rotating, very common social |
| `mexicano` | Mexicano | Similar rotation, winners move up |
| `round_robin` | Round robin (fixed pairs or rotating) | Smaller groups; also scratch Play |
| `king_of_court` | King of the court | Winners stay, losers rotate |
| `social_rotate` | Timed rotate | “Play 12 min, rotate” — no ranking required |

Later: ladder / box league, single elimination, DUPR constraints on top of a format.

### Format engine contract (sketch)

Backend, not the LLM:

- Input: `sport`, `format`, `playerIds[]`, `courts`, `options`
- Output: `rounds[]` → `matches[]` (court, side A, side B, status)
- Commands: `record_result`, `swap_player`, `add_player`, `remove_player`, `rebalance`, `next_round`
- Invariants: no duplicate simultaneous play, court count respected, bye rules explicit

`record_result` is what Casper’s tool must call after the organiser names a score. The engine validates match id, score shape, and whose turn it is.

If the roster changes, **rebalance** is a real algorithm.

---

## 7. DUPR

Optional per event/session. Relevant while `sport: pickleball`.

When **rated = true**: collect DUPR names/IDs if we have them (**TBD:** official API vs manual), store exportable results. Casper is not DUPR.

When **rated = false**: skip IDs, still store Casper history.

**TBD:** launch feature vs v2 for clubs?

---

## 8. Example evening (happy path)

```
CONNECT — group "Skill 4+ Sundays 9–12" (quiet ON)
           24 members, weekly event
           members cannot free-chat; they RSVP / like; admins can post
           private DMs still work

Creator    weekly event bubble already there
Event bubble: Sun 17 Aug 09:00–12:00, 4 courts, not DUPR
              [I'm in] [Out] [Like] [Share]
…             16 tap in over the week
Admin post:   "Hall opens 08:45, bring indoor shoes."
Organiser     shares the bubble link to an old WhatsApp thread
              → landing page → Open in Casper (TestFlight / later App Store)


PLAY — new chat "Sun 17 Aug — Skill 4+"
       organiser + participants

09:02  Organiser: We're 11 here, 3 courts. Americano.
       Casper: Games to 11? Win by 1 or 2? Until 12:00?
       Organiser: 11, win by 1, until 12.
       Casper: Starting Americano, pickleball, 11 players, 3 courts, 1 bye.
               Round 1:
               Court 1  Cassie/Erik vs Anna/Moa     ← on screen
               Court 2  …
               Bye: Kim

09:14  Organiser (Ask Casper): Court 1 11-8
       Casper: Records 11–8 on Court 1 Cassie/Erik vs Anna/Moa (match in view).
               Table updated. Next games posted.     ← engine after the tool call

09:40  Organiser: Lisa arrived, Kim has to go
       Casper: Swapped. Remaining rounds rebuilt.
```

Scratch (no event): Play → New session → add people → same interview. Organiser owns it; participants can view.

---

## 9. Business model

**Chosen:** organiser pays for AI. Players free. 3 months free, then **49 kr/month**, cancel anytime.

### How it works

| | |
|---|---|
| **Who pays** | The person who **uses AI** (Ask Casper, Create Event, run Play, register scores via AI). Not the players. |
| **Who is free** | Players: read, RSVP, like, DMs, view Play they participated in. |
| **Trial** | **3 months free**, then paid. |
| **Paid** | **49 kr / month.** **Stop anytime** — no binding period. |
| **Price job** | Cover **OpenAI + AWS + ops**, small margin. Shrug-and-pay for a Thursday captain. |
| **Gate** | AI requires **role** + **active trial/paid membership**. |

### Why not charge players

They already paid for the court. A paywall on “I’m in” kills the group.

### Cost control (49 kr must work)

- Connect group chat does **not** go to OpenAI
- Format generation and standings = **Lambda / engine**
- Play interview, swaps, **score registration** = OpenAI tool calling
- Prefer a **cheap model** for `record_result` (short prompt: current matches on screen + “Court 1 11-8”)
- Soft cap **TBD** if someone hammers Ask Casper
- AWS serverless (pay per use) so infra stays small until US/Asia

Rough night: 1 setup + ~15–40 score calls + a few swaps. With a mini model, token cost should sit well under 49 kr.

### Price details

- **49 kr/month** (working number, Sweden first)
- **While on TestFlight:** no real charges; fake trial for everyone
- **Production billing (chosen direction):** **Apple In-App Subscription** on iOS and **Google Play Billing** on Android. Owner: **RabbitEye AB**. Web/Stripe is not the v1 checkout — see §9.1.
- Membership is **per person who uses AI**, not per group. Two captains = two × 49 kr if both Ask Casper. **TBD** group seat later.
- **TBD:** 49 kr including Swedish VAT? Apple IAP: user pays the store price; Apple typically handles consumer VAT.

### Unit economics — AWS vs AI per paying organiser

Sketch, August 2026. **Not a quote.** Prices move. Use this to see whether **49 kr/month** can cover OpenAI + AWS.

**FX:** ~9.5 SEK / USD → **49 kr ≈ $5.15**. If 49 kr is a Swedish consumer price **including 25% VAT**, net to Casper is **~39 kr ≈ $4.10**. Below, “cover 49 kr” means the sticker; VAT makes the squeeze tighter.

**Who generates which bill**

| Cost | Scales with | Pays? |
|---|---|---|
| **OpenAI** | The **AI user** (organiser): Ask Casper, Create Event, Play setup, register scores | Yes — this is why they subscribe |
| **AWS variable** (Lambda, API GW, DynamoDB, WebSocket, data out) | Organiser **plus all free players** in their groups/sessions | Organiser’s 49 kr must cover this too |
| **AWS + tooling floor** | The product existing (logs, secrets, Apple Developer, EAS, domain) | Shared across all paying organisers |

Players do **not** hit OpenAI. They still cost a little AWS (Cognito MAU, WebSocket while the app is open, message fan-out, push).

#### OpenAI per AI user / month

Assume **4 social nights** (one per week) + a bit of Connect.

| Call | Count / month | Model |
|---|---|---|
| Play setup / swaps / Create Event | ~20–30 | mini; optionally one stronger model for first setup |
| Register score | ~80–160 (20–40 games × 4 nights) | **mini only**, current matches in the prompt |
| Connect Ask Casper | ~5–15 | mini |

Token sketch (expected): ~0.3–0.8M input + ~0.03–0.08M output on **gpt-4o-mini** ($0.15 / $0.60 per 1M).

| Scenario | What we did | OpenAI / organiser / month |
|---|---|---|
| **Tight** (the plan) | mini for scores; short “matches on screen” context | **~$0.05–0.25** (~0.5–2.50 kr) |
| **Expected** | a bit of chatty setup + 4o for 1–2 setups, mini for the rest | **~$0.20–0.80** (~2–8 kr) |
| **Fat** | **gpt-4o** on every 11–8, fat history in every prompt | **~$5–15+** — **this breaks 49 kr** |

So: 49 kr is very comfortable on OpenAI **if scores stay on a mini model**. It is not comfortable if every score is a large-model novel.

#### AWS variable (one organiser + ~15–20 free players)

Serverless list prices, order of magnitude, `eu-north-1` / US rates (Stockholm is in the same ballpark):

- API Gateway HTTP ~$1 / million requests  
- WebSocket ~$1 / million messages + $0.25 / million connection-minutes  
- Lambda ~$0.20 / million invokes + duration (waiting on OpenAI is billed; still cents)  
- DynamoDB on-demand: writes are the meter; still cents at this volume  
- Cognito: **Lite/Essentials, 10,000 MAU free** (Google/Apple count as social login). **Lite** after that ~$0.0055/MAU; default **Essentials** ~$0.015/MAU. Prefer **Lite** if the feature set is enough.  
- Data out: chat JSON is tiny vs video

Per organiser-month (4 nights, ~16 people connected ~2 hours on court, RSVP traffic in the week): **variable AWS is typically well under $0.50**, often **a few cents**, unless we log every WebSocket frame to CloudWatch ($0.50/GB — the usual serverless surprise).

**Cognito** stays $0 until ~10k monthly actives ≈ **~500 paying organisers** at 1:20 player ratio. Then players start to show up on the bill, still small (thousands of MAU × $0.0055).

#### Floor (exists even at 1 user)

| Item | Rough |
|---|---|
| CloudWatch / X-Ray (keep logs quiet) | $2–15/month if disciplined; much more if verbose |
| Secrets Manager | ~$0.40 per secret |
| SES | pennies at TestFlight volume (Cognito may use SES) |
| S3 + CloudFront landings | pennies–a few dollars |
| Apple Developer Program | $99/year ≈ **$8/month** |
| EAS (Expo builds) | $0 on free tier; often **~$19/month** if we pay for a plan |
| Domain / Apple certificates | small |

**Floor ≈ $15–40/month** before the first 49 kr, mostly **Apple + EAS + logs**, not Lambda.

#### Does 49 kr work?

| Paying AI users | Revenue (gross 49 kr) | OpenAI (expected) | AWS variable | Floor | Picture |
|---|---|---|---|---|---|
| **1** (you) | ~$5 | < $1 | cents | $15–40 | **Loss.** Floor dominates. Fine for TestFlight. |
| **10** | ~$52 | ~$2–8 | < $5 | $15–40 | **About break-even** on infra+AI if logs stay quiet and EAS is modest. No salary. |
| **100** | ~$515 | ~$20–80 | still small | $20–50 | **49 kr works.** OpenAI + AWS are a minority of revenue. VAT/IAP cut (~15–30% store, or 25% VAT) still leave room. |
| **500+** | | | Cognito may leave free tier | | Still OK on Lite; watch **Essentials** ($0.015/MAU) and **CloudWatch**. |

**Read this as:** AWS is not the problem. **OpenAI is not the problem** on the architecture we already chose (mini + tools + engine). The problem at the start is **fixed cost** (Apple, EAS, logs) and later **store/VAT cut**, not DynamoDB.

**Implications for the model**

1. Keep score registration on a **cheap model**; never send the whole Play transcript into GPT-4o.  
2. Do not send Connect group chat to OpenAI (already decided) — that would make AWS *and* AI scale with free players.  
3. Cap or meter Ask Casper so one captain cannot burn $15 of 4o in a weekend.  
4. 3-month **trial is cheap in tokens** (~$1–3 of OpenAI); it does not pay the Apple/EAS floor.  
5. Prefer Cognito **Lite**, Lambda **without VPC/NAT** (NAT gateway alone can be ~$30+/month).  
6. Revisit 49 kr only if we must use a large model for every score, or if IAP+VAT stack on top and we want salary — not because AWS chat is expensive.

**TBD:** 49 kr including VAT or excluding; IAP vs Stripe net.

### 9.1 Who sells the subscription (RabbitEye AB)

**Legal owner:** **RabbitEye AB** — Apple Developer *organization* (not a personal account), Google Play organization, domains, privacy policy, terms. Seller name on the store can be RabbitEye AB; the *app* is still **Casper Play**.

Need for Apple org: D-U-N-S for the AB, plus the 99 USD/year program.

#### Apple Subscription vs web (Stripe)

Casper Play sells a **digital** feature (AI in the app). That is Guideline **3.1.1** by default: unlock in the app → **In-App Purchase**. It is not a court booking (physical). Players are free; only the organiser sub is paid.

| | **Apple / Google store subscription** | **Web (Stripe) as the only checkout** |
|---|---|---|
| App Review | Default legal path | Easy **3.1.1 reject** if the iOS app sells/steers to the website (except regional exceptions) |
| VAT / invoices | Apple/Google often **merchant of record** — much less OSS pain for a small AB | RabbitEye AB is merchant: EU VAT, invoices, chargebacks |
| Cancel anytime | Built into the store | You build it (required anyway by law) |
| Cut | **15%** Small Business Program (under ~$1M/year); **30%** otherwise; **15%** after year 1 of a sub in many cases | Stripe ~1.5%+ but **not** “Apple takes 0%” if you link out in the EU — alternative terms still have Apple fees (CTC / store services / acquisition) |
| iOS + Android | Two billings (StoreKit + Play Billing), one product: 49 kr/month | One Stripe customer — nicer *later*, when you have a real web paywall |
| UX for a Thursday captain | Pay in the app, stay in the chat | Safari hop to pay, then return — friction at 49 kr |

**EU (Sweden) nuance:** DMA lets you *promote a web checkout* with StoreKit External Purchase Link, under **alternative EU terms**. You generally **cannot mix** that with IAP on the **same EU storefront**. US storefronts have their own link-out rules. Rest of world still expects IAP. That is three billing stories. Too much for v1.

**Guideline 3.1.3(b) multiplatform:** you *may* honour a sub bought on the web **if the same thing is also for sale as IAP** in the app, and you do not steer iOS users away from IAP (except where regional link-out is allowed).

**Recommendation**

1. **TestFlight:** no payments.  
2. **App Store / Play Store v1:** **store subscriptions** (Apple + Google). Enroll **App Store Small Business Program**. Price **49 kr** on the Swedish store.  
3. **Do not** ship a “Subscribe on our website” button in the iOS app at v1.  
4. Revisit **Stripe + EU external link** only if the 15–30% actually hurts (many captains, US+Android+web). At 49 kr and ~$0.20 OpenAI, the cut is not the problem; review rejection is.

**49 kr vs Apple cut (order of magnitude):** 15% ≈ 7 kr, 30% ≈ 15 kr. Still above expected OpenAI+AWS variable. Floor (Apple Developer, EAS) is unchanged.

### 9.2 Web address (product vs company)

The **app** is Casper Play. The **company** is RabbitEye AB. Do not put the mattress brand `casper.com` anywhere.

| URL | Role |
|---|---|
| **casperplay.app** | **Primary product site — owned (GoDaddy).** Invite landings, Universal Links / “Open in Casper”, privacy, support. |
| **casperplay.com** | **Owned (GoDaddy).** Redirect to `.app` so squatters cannot take it. |
| **casperplay.se** | Optional later: Swedish trust, redirect → `.app`. Not required now. |
| **rabbiteye.se** (or existing RabbitEye domain) | **Legal home:** AB, contact, maybe a one-liner “we make Casper Play”. Privacy can live here *or* on casperplay.app — Apple needs a stable privacy URL. |

Avoid: `casper.app` / `casper.se` (ghost/mattress collisions), `play.casper.com` (you do not own casper.com).

**Suggested stack of URLs**

- `https://casperplay.app` — marketing + TestFlight/App Store badges  
- `https://casperplay.app/e/{token}` — event share (“Open in Casper Play”)  
- `https://casperplay.app/privacy` — App Store privacy  
- `https://casperplay.app/support`  
- Associated domains for Expo: `applinks:casperplay.app`

**Bundle id (candidate):** `se.rabbiteye.casperplay` — scoped to the AB, not a random `se.casper.app`.

Registrant should be **RabbitEye AB**. Point **casperplay.com** → **casperplay.app**. Expo associated domains: `applinks:casperplay.app`.

### When they cancel

- No new AI
- They and players keep **reading**
- **TBD:** resume anytime; trial only once per account

### Rejected / later

| Model | Status |
|---|---|
| Per-session fee at the door | Rejected |
| Every player pays | Rejected |
| Hall booking bundle | Later |
| Sponsorship | Ignore for now |

### Positioning

**“The chat that organises the group — and runs club night.”**  
Players free. Captains: three months free, then 49 kr/month.

---

## 10. Technology

**TypeScript everywhere** (Expo app, Lambdas, CDK, format engine).

**Primary region (v1):** `eu-north-1` (Stockholm). Edge: CloudFront for invite landings and media. Later: extra regions + DynamoDB global tables — not a rewrite.

### 10.0 Client — Expo (locked)

Casper is an **Expo** app (React Native), not a PWA and not two native codebases.

| Decision | Why |
|---|---|
| **Expo**, not Swift+Kotlin | One TypeScript app; Cursor is fast here; AWS is the unique work |
| **Expo**, not a web chat | Native list, keyboard, push; chat must not feel laggy on court |
| **Dev client**, not Expo Go | Cognito, push, and TestFlight need a real binary |
| **EAS Build** | Repeatable iOS/Android binaries for devices and TestFlight |

Chat UI bar:

- Inverted message list (`FlashList` or equivalent)
- Native composer + keyboard controller (no jump when the keyboard opens)
- **Optimistic send** (bubble appears before the server ACK)
- Casper replies stream into the last bubble
- Reconnect WebSocket after lock screen without a stuck “sending”
- Event bubbles and Play tables are message types in the same thread, not a webview

**Not the chat product:** a thin **S3 + CloudFront** page for invite/event links (“Open in Casper”). Deep links into the Expo app.

**Rejected:** PWA-first (rebuild the thread later), bare React Native without Expo, native two-apps for v1.

Why not PWA / dual native (short): OpenAI and Lambda latency are the same on every client. What feels like a laggy chat is keyboard, scroll, background socket, and push — iOS Safari loses that fight. Two native apps double the chat work for Cursor.

### 10.1 Distribution — Apple Developer / TestFlight first

We do **not** ship App Store on day one. First testers (your phone, then a small group) use Apple’s developer testing path.

| Stage | What | Who |
|---|---|---|
| **0. Local** | Expo dev client on a cable / LAN, Apple Developer signing | You, while building with Cursor |
| **1. TestFlight Internal** | EAS Build → App Store Connect → **TestFlight (Internal Testing)** | You + invited testers on the Apple Developer team (up to 100). **No public App Store. No Beta App Review.** |
| **2. TestFlight External** | Optional, when we want more players without adding them to the team | Needs Beta App Review |
| **3. App Store + Play Store** | Production. 49 kr via store IAP as required | Phase 3 |

**Need now:** paid **Apple Developer Program** membership (99 USD/year) as **RabbitEye AB**, App Store Connect app record, bundle id (candidate `se.rabbiteye.casperplay`), EAS credentials. Domains already held: **casperplay.app**, **casperplay.com**.

**Android (same phases, lower ceremony):** EAS preview APK/AAB, then Play **internal testing** when we have Android testers. iOS is the path that gates a Swedish pickleball group.

**Sign in with Apple:** required by Apple if we offer Google and we go TestFlight External / App Store. Put **Apple + Google** in Cognito **before** inviting real testers on TestFlight, not as a Phase 3 afterthought. Magic link still exists for new device / dead session.

OTA: Expo **EAS Update** can ship JS/TS chat fixes to TestFlight users without a new binary; native module changes still need a new build.

### 10.2 Shape

| Layer | Choice | Why |
|---|---|---|
| Client | **Expo** (iOS + Android), EAS | Flawless chat; one TS app |
| i18n | English default; **Swedish first extra**; i18next (or equivalent) + Expo localization | Device language, fallback `en`. No hardcoded UI strings |
| Auth | **Amazon Cognito** (Google, Apple, magic link/OTP via SES) | No passwords; TestFlight-ready IDPs |
| API | **API Gateway** (HTTP + **WebSocket**) + **Lambda** (Node.js / TypeScript) | No server to babysit; worldwide later |
| Rules / formats | Same Lambdas, **pure TS format engine** | Deterministic; no LLM |
| AI | Lambda → **OpenAI** (tools). Key in **Secrets Manager** | |
| Data | **DynamoDB** | NoSQL, AWS-native, global tables later |
| Email | **Amazon SES** | Magic link, invites |
| Files / landings | **S3 + CloudFront** | Avatars, recaps, Open in Casper pages |
| Payments | Stub on TestFlight; **App Store + Play subscriptions** in Phase 3 (RabbitEye AB). Stripe web later if ever | See §9.1 |
| Push | **Expo Notifications** (+ APNs / FCM) | Native, not web push |
| Secrets / config | Secrets Manager, SSM | |
| Observability | CloudWatch, X-Ray | |
| IaC | **AWS CDK** (TypeScript) | Repeatable US/Asia stacks |
| App builds | **EAS Build + EAS Submit** (TestFlight) | Apple Developer test path |

Not v1 unless we hit a wall: ECS/Fargate, AppSync, Bedrock, PWA chat.

### 10.3 Map

```
Expo app  (iOS TestFlight / Android internal)
   │  HTTPS + WSS
   ▼
Cognito: Google / Apple / magic link (SES)

API Gateway HTTP  ── Lambda ── DynamoDB
                      ├── format engine
                      ├── OpenAI (Ask Casper, scores, setup)
                      └── Stripe webhook (later)

API Gateway WebSocket ── Lambda ── DynamoDB (connections + messages)

S3 + CloudFront  — recap images, invite landing (“Open in Casper”)
EAS              — ipa/aab → TestFlight / Play internal
```

Cognito JWT on every call. Membership (trial / 49 kr / lapsed) stored in DynamoDB (and optionally Cognito attributes). AI Lambdas **refuse** if lapsed — OpenAI is not called.

### 10.4 DynamoDB (not Mongo)

**Hard limit:** 400 KB per item. Do **not** store a whole Play night (all rounds + all chat) in one item.

| Entity | Keys (sketch) | Notes |
|---|---|---|
| User | `USER#id` | membership, trial_start, stripe_customer / IAP |
| Group | `GROUP#id` | quietMode, sport default |
| Membership | `GROUP#id` / `USER#id` | role: creator, admin, organiser, member |
| DirectThread | `DM#min:max` | two user ids |
| Event | `GROUP#id` / `EVENT#id` | bubble, recurrence, RSVP + likes as related items |
| Session | `SESSION#id` | organiser, participants, sourceEventId?, sport, format |
| Match | `SESSION#id` / `MATCH#round#court` | sides, score, status |
| Message | `THREAD#…` / `TS#iso` | group, DM, or Play; type text \| event_bubble \| table \| system |
| Connection | `CONN#websocketId` | API Gateway WS fan-out |
| Invite | token | |

Player history: GSI on `participantId` + `sessionDate` (or a `PlayerMatch` item per result). **Typed Lambda queries only** — the model never invents DynamoDB queries.

**Later worldwide:** DynamoDB **global tables**, API + Lambda in `us-east-1` / `ap-southeast-1`. Cognito multi-region when we leave Nordics.

### 10.5 AI architecture

```
Ask Casper / Create Event / Play setup / "Court 1 11-8"
        ↓
API Gateway → Lambda
        ↓
Authz: Cognito JWT + role + trial/paid
        ↓
Load current session into the prompt
  (matches on screen: ids, court, names, status)
        ↓
OpenAI tools → create_event | start_session | record_result | swap_player | …
        ↓
Format engine in Lambda (validate match id, write DynamoDB)
        ↓
WebSocket fan-out → Expo clients (optimistic UI already showed the user bubble)
```

**Play score path:** organiser talks to Casper while the round is visible. System prompt includes **current open matches** with stable ids. Tool `record_result({ matchId, scoreA, scoreB })` is rejected if `matchId` is not open. Casper then confirms in chat.

**Connect:** no LLM on member messages, RSVP, or likes.

Rules: allowed tools + format codes only; `sport` passed in (`pickleball`); idempotent scores; organiser undo; lapsed membership → no OpenAI call.

Prefer **gpt-4o-mini** (or similar) for score registration; a stronger model only for first-time Play setup if needed.

### 10.6 What the AI is allowed to do vs not

| Allowed (organiser + membership) | Not allowed |
|---|---|
| Ask clarifying questions after Ask Casper / Create Event | Run on every Connect group message |
| Recommend a format from the catalogue | Invent a rotation system |
| `record_result` on a **match id we provided** | Invent a match / wrong court |
| `create_event`, `start_session`, `swap_player` | Scan DynamoDB ad hoc |
| Summarise who’s in / a table | Use training data as history |
| Draft share text | Post into WhatsApp |

### 10.7 Data the AI needs from us

- Current open matches (ids, court, names) — **required for scores**
- Group members, quietMode, event roster / on-site
- Format catalogue + `sport`
- Standings snapshot, aliases, caller membership status

### 10.8 Auth (Cognito)

- **Sign in with Google**
- **Sign in with Apple** (needed for TestFlight/App Store when Google is offered)
- **No passwords**
- **Long-lived login** (Cognito refresh tokens)
- **Magic link / email OTP** if session gone or new device (SES)

Walk-up: organiser adds a display name in Play; claim later. **TBD:** merge.

### 10.9 Realtime and push

- **Chat / RSVP / table:** API Gateway **WebSocket**; connection ids in DynamoDB; Lambda fan-out. Expo paints the outgoing bubble **before** ACK.
- **Push:** APNs (via Expo) for TestFlight iOS; FCM when Android testers exist. Event reminders + “you’re up” + admin posts in quiet groups. No notify on disabled member chat.
- Lock screen: reconnect WS on foreground; show missed messages from DynamoDB, not an empty spinner.

### 10.10 Why not Docker / Fastify / Mongo

That matches other personal apps, not this one. Casper needs Cognito, WebSockets, NoSQL, Expo, worldwide. DynamoDB + Lambda is the AWS version of that. If WebSocket + Lambda gets painful, API Gateway WS stays and the format engine can move to **Fargate** without leaving AWS.

---

## 11. Information architecture

```
User (Cognito sub + DynamoDB profile: trial | paid 49kr | lapsed | never)
 ├── DirectThread (1:1)                         [Connect]  always on
 └── Group (quietMode on/off, roles)            [Connect]
        ├── Admin/member messages (members blocked if quiet)
        └── Event bubbles (RSVP + like always)
               └── Start Play → Session

User starts Play from scratch
 └── Session (sourceEventId: null)              [Play]
        ├── organiserId (always)
        ├── participantIds (can view)
        ├── Match items (not one blob)
        └── Messages (score confirmations, tables)
```

GDPR: **TBD** retention, export, delete account (Cognito + DynamoDB + S3).

---

## 12. Phased build

### Phase 0 — this document

Product + stack agreed. Apple Developer Program active. No production App Store.

### Phase 1 — vertical slice on TestFlight Internal

- Expo app: Connect + Play tabs, native chat shell (list, composer, optimistic send)
- **English UI** with i18n keys; Swedish file can be empty/partial (fallback to English)
- EAS Build → **TestFlight Internal** (and local dev client)
- Cognito: **Google + Apple** + magic link/OTP
- AWS CDK in `eu-north-1`: HTTP + WebSocket, DynamoDB, SES
- One group, quiet toggle, Create Event bubble, RSVP + like
- Ask Casper only on organiser actions
- Play from bubble **and scratch**
- One format (Americano or round robin)
- **AI register score** to match on screen + engine table
- Membership stub (everyone on fake trial)
- Share: copy link + simple “Open in Casper” landing

Out of scope: Stripe/IAP, DUPR, voice, App Store review, Play Store production.

### Phase 2 — real group night (still TestFlight)

- Invites, roles, weekly recurrence
- Private chats
- More formats
- Native push (APNs)
- Walk-up names
- Recap on S3
- Optional TestFlight **External** if the group is larger than the Apple team

### Phase 3 — productize

- App Store + Play Store  
- **49 kr/month** via **Apple Subscription + Google Play Billing** (RabbitEye AB, Small Business Program), 3-month trial, cancel anytime  
- Privacy/support on **casperplay.app**
- DUPR export
- Multi-region when US/Asia is real
- `sport` expansion if demanded

---

## 13. Risks

| Risk | Mitigation |
|---|---|
| 49 kr eaten by fat prompts on every score | Mini model + only current matches in context; see unit economics |
| AWS floor (Apple, EAS, CloudWatch) at 1 user | Expected until ~10 paying captains; no NAT gateway; quiet logs |
| Cognito Essentials after 10k MAU | Prefer **Lite** if features suffice |
| Player scores still ambiguous | Keep question open; AI path is organiser-only for now |
| Quiet groups feel dead | RSVP, likes, admin posts, DMs still alive |
| DynamoDB 400 KB / awkward queries | Split matches & messages; GSIs for history |
| Lambda + WebSocket complexity | Connection-table pattern; Fargate fallback |
| Chat still feels laggy on Expo | FlashList, keyboard controller, optimistic send, WS reconnect — treat as Phase 1 acceptance, not polish |
| Apple Sign-In / TestFlight friction | Apple + Google from Phase 1; Internal TestFlight first (no beta review) |
| Store IAP vs 49 kr Stripe later | Ignore until Phase 3; no charges on TestFlight |
| Trial abuse | One trial per Cognito user |
| Name / bundle id collision | Check domains, trademarks, `bundleIdentifier` before EAS |
| DUPR TOS | Manual export first |

---

## 14. Open questions

Product

1. **Player scores:** AI-only (organiser), or players may tap/type too? **Kept open.**
2. Ask Casper from **private chats**, or only groups + Play?
3. After Play ends: keep forever vs archive after N days?
4. Walk-up names: guests forever vs require claim?
5. Voice in v1 or text only?
6. Two Play sessions at once from one group?
7. Casper’s **spoken/replied language**: always English, or follow the user’s UI locale (sv/en)?

Formats

8. First format: Americano vs round robin?
9. Singles in v1, or doubles only?
10. Bye rules for odd numbers?

Business

11. Two admins = 2 × 49 kr, or a **group seat** later?
12. Trial once; cancel day 89 and return?
13. Phase 3: keep store IAP, or add Stripe + EU external-purchase link later?
14. Is **49 kr including Swedish VAT** (25%)? (IAP: user pays store price.)
15. Optional: also register **casperplay.se**?

Tech

15. HTTP API + WebSocket vs **AppSync** subscriptions?
16. Confirm bundle id **`se.rabbiteye.casperplay`**?
17. Email OTP vs true magic link in Cognito v1?
18. Android testers in Phase 1, or iOS TestFlight only until the chat is right?
19. Cognito **Lite vs Essentials** (cost after 10k MAU)?

---

## 15. Decisions already made

**Product**

- **Casper Play** is the product name. The AI in chat is **Casper**. Owner: **RabbitEye AB**.
- Chat-first. Connect + Play. Pickleball (`sport` field); formats reusable later.
- Last-minute on-site roster. AI interviews organiser (courts, names, DUPR yes/no). Results + tables in Play chat.
- Two tabs, both chat. Groups: create / join / invite. Events are bubbles. Weekly groups. Private 1:1 chats.
- Quiet mode: creator on/off. Members still RSVP, like, DM. Admin can always post. Member free-chat off when quiet.
- Scratch Play allowed. Organiser + participants can view. History in NoSQL. Formats locked in backend API.
- Own chat, share out, no WhatsApp bridge.
- Who organises: right **role and membership**. Who pays: the one who **uses AI**. Players read free.
- 3 months free, then **49 kr/month**, cancel anytime.
- **UI: English.** i18n from the start; **Swedish first additional language.** Code/API in English.
- Scores: organiser asks AI to register on the **match shown on screen**. Player tap **kept open**.

**Tech**

- **Expo** frontend (iOS + Android). Dev client + EAS. Not PWA, not dual native.
- Early distribution: **Apple Developer (organization: RabbitEye AB) + TestFlight Internal**, not App Store.
- Production pay: **Apple + Google subscriptions**, not web checkout in v1. Product site: **casperplay.app** (owned); **casperplay.com** owned, redirect to `.app`.
- AWS: Cognito (Google + Apple + magic link), Lambda, API Gateway HTTP+WebSocket, DynamoDB, S3/CloudFront, SES, CDK. `eu-north-1` first.
- OpenAI tools; format engine in Lambda. TypeScript everywhere.

---

## 16. Next step

Still useful to lock: bundle id `se.rabbiteye.casperplay`, **first format**, and whether Casper **replies in the UI language**. Then `implementation-plan.md` and a real repo.
