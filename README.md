# Ping AI prototype: handoff notes for the next AI session

> Written for an AI assistant picking this project up in a new account. Read it fully before you change anything.
> **Talk to the user (Leqi) in Chinese (中文).** Deliverables (the prototype UI and its copy) stay in English.

---

## 1. Who and why

- **User:** Leqi Huang. Senior in Information Science at UIUC (HCI / UI-UX), minor in Art & Design. UX/UI designer.
- **Goal:** final-round interview for the **UI/UX Design Intern** role at **Ping AI**, a consumer AI startup in NYC.
  - Interview: Fri Oct 16, 2026, 3 pm.
  - Interviewer earlier in the process: Lindsay Cai (Head of Growth & Strategy).
- **Assignment:** a take-home called **"Beyond the Chatbox"**, delivered as a web prototype plus a Figma prototype.
  - The brief asks for a consumer AI that does not wait for a prompt. It surfaces signals across the user's interests, and the research happens behind the scenes.
  - Required screens: **Home / discovery**, **Signal detail**, **Next-step state**.
  - Every screen must answer three questions: *what happened*, *why it matters to me*, *what can I do*.
  - Chat may exist, but it must not be required or dominant.
- **Scope of the latest work:** web demo only. The Figma file was not touched in this round.

## 2. How it started (version 1, the "old" demo)

The original prototype is in `old/`. A design rationale page lives in `old/rationale/` and `new/rationale/`; read it for the full reasoning.

- Leqi's framing: **Ping is the hunter for your interests.** It finds tables, tickets, restocks and appointments, the signals that change fast and won't wait.
- **Rule 1: no chat.** Every decision is a tap on an option Ping has already prepared.
- **Rule 2: Ping acts only after a clear yes.** It can watch, hold and prepare on its own, but never books or pays without confirmation. Payment needs Face ID.
- **Home** was a *daily brief that ends*, not a feed.
  - Headline example: "6 new today. Vela won't last."
  - Sensing line: "Watching 23 places · checked 2 min ago".
  - Finds were drawn as *ticket stubs*.
  - Tabs: For you / Following / Nearby.
  - Handled cards fly into a "Handled today" fold.
- **Signal detail** sections: What happened · Why you · Insider note · Where this came from · What I used about you. The actions were Grab it / Not now.
- **Next step:**
  - Tapping the action tears the stub, and the hunt moves to a Hunts tab.
  - Each hunt is a timeline: waiting → fork (two prepared options) → working → hold → done.
  - It also had lock-screen and Dynamic Island states.
- The old version used a dark, warm theme.

## 3. The update (version 2, the "new" demo)

**Brief from Leqi:** update the assignment to match **Ping's new App Store preview**.

- Leqi submitted screenshots of that preview. These reference images live only in the previous session and are **not** in this repo.
- The redesign moved the prototype toward that look:
  - a light theme with white, black type and an amber accent `#F0B43C`;
  - big photo-led story cards;
  - pill controls;
  - a floating tab bar;
  - specialist **"Insiders"**: Access Insider (reservations, concerts, movies, appointments), Shop Insider (vintage, restocks), Markets Insider and Sports Insider.

### Major changes, in roughly the order they were made

1. **Retheme.** Dark/warm became the light App Store look. Logic was untouched at this stage.
2. **Today feed.** Photo-story cards, one column. Tapping a card expands it centered in view with FLIP motion.
   - Later simplified because the cards had too many elements.
   - Each card now has **two actions plus an "ask about this" text link**: *Not now* and the primary CTA (e.g. "Try to hold", "Review copy trade").
3. **Ask Ping.** A floating ✦ button opens an overlay with chips and an input.
   - Leqi liked the original chip layout; a redesign was rejected, so only the visuals were polished.
4. **No mascots.** Leqi rejected the illustrated mascots; use text and avatars instead.
5. **New hunt.** A **full-page chat flow** that asks one question at a time. It is not a popup and does not open full-height.
6. **Insiders tab.** It went to an assignment-card list and was then **reverted to a chat list** (one chat per Insider). Keep it as chats.
7. **Confirm before grab.** Leqi felt "Grab it" was too hasty (e.g. it auto-booked a table for 2).
   - Every primary CTA now opens a **confirm sheet** ("Before I grab it") with editable choices: people, time, seating, fallback, amount, auto-stop, and so on.
   - Values come from the user's saved preferences.
   - The sheet also offers "not sure yet? ask [Insider]".
8. **Task page.** It replaced the old thread view.
   - **Hero:** photo, status pill, "MANAGED BY [Insider] ›", title.
   - **Ticket-style result** when done.
   - **PROGRESS timeline**, newest first.
   - **Inline task chat** with suggested prompts.
   - **Forward-only bar** ("back to today · next up: …"). Leqi wants forward motion, not a back button.
9. **"Needs your decision" strip** at the top of Today.
   - A task that needs the user appears only there, never duplicated as a feed card.
   - Tapping *decide* opens the task page.
10. **Not now** opens a chooser: *Remind me later* / *Not interested*, plus why.
    - There is an undo toast.
    - The "why" question is asked only on pass.
11. **Discover detail page** and track flows.
12. **Trust controls** (inspired by Muse-style AI products).
    - Per-Insider **autonomy**: *only ask me* / *hold & queue* / *pay ≤ $50*.
    - Editable preferences page: "What ping knows about you".
    - The thread shows "paid with · one-time card".

### Work done in the last session (Oct 15–16)

- **UI pass**
  - **Confirm sheet:** photo header, −/+ stepper for numbers, pill chips, round × cancel, 56px pill confirm.
  - **Task page:** hero, ticket result, PROGRESS label.
  - **Insider chat:** segmented control, bubble tails, typing dots.
- **Confirm sheet copy and layout**
  - Note text trimmed: the autonomy line and "change it on the Insider page" were removed.
  - Options now **wrap**, with no inner scroll; all rows show at once.
- **Progress motion**
  - The card's bar creeps continuously toward the next step and has a sheen.
  - It fills to 100% and holds a ~0.75 s "Ready · found it · needs your ok" beat.
  - The card then **folds up into the needs strip**.
- **Motion pass 2**
  - Sheets and the Ask overlay slide or fade out on close; previously they vanished.
  - The strip collapses on exit, and the cards below glide into place.
  - The segmented thumb slides.
  - Stepper numbers roll.
  - Changing copy crossfades.
  - New timeline rows drop in and the older rows ease down.
  - The Insider greeting bubbles stagger in.
- **Autonomy moved out of the chat.**
  - It now lives in an **"[Insider] settings" bottom sheet**, opened from a sliders button at the top right of the Insider chat.
  - Leqi's reasoning: it is a setting, not conversation.
- **Markets scenario enriched.** Card: "A market take you follow is up 36% this month", @remmy's defense-tech basket of 15 stocks.
  - **Steps:**
    - checked @remmy's record (+41% in 12 mo, worst drop −18%);
    - checked brokerage ($1,240 cash free);
    - amount;
    - split across 15 stocks;
    - **Face ID buy**;
    - filled.
  - Sheet choices for amount, auto-stop and take profit flow into the buy rows. Funds come "from linked brokerage · cash".
  - **Task page:**
    - "WHAT YOU'D OWN" holdings bar before buying;
    - "YOUR POSITION" after buying: value, +today, animated sparkline;
    - "I'M WATCHING": earnings Tue, early warning before the auto-stop, @remmy's next trades.
  - Result actions: *adjust limits* / *stop copying*. There are market-specific chat replies.
  - **Bug fixed:** after a Face ID payment, the hunt now continues to the steps that follow, where before it got stuck "in progress". This applies to all pay flows, but only the market flow was checked.
  - The needs strip shows "Defense tech take · confirm the buy" instead of "@remmy".

## 4. Leqi's preferences and decisions (respect these)

- Replies in Chinese, concise. Show screenshots of changes.
- Prefers **refining** over redesigning what she already likes, e.g. the Ask chips. Ask before big structural changes.
- **No mascots.** Insiders stay **chat-based**. Settings never go inside chat.
- **Confirm before acting** on anything that books or pays. Show the choices, never silently pick defaults.
- **Forward-only flows**: after finishing a step, offer the next thing; don't strand the user on "back".
- **No duplicate surfaces**: a needs-you task appears in the strip only.
- Motion should feel smooth (iOS-like easing `cubic-bezier(.32,.72,0,1)` / `(.22,.8,.28,1)`) and respect `prefers-reduced-motion`.
- Avoid real brand impersonation. Fictional tickers and venues are used: ORBL, KSTR, Osteria Vela, Nova Lanes.
- **Security:**
  - Never type passwords, tokens or API keys for her.
  - Deploy auth is done by her approving device codes.
  - Log out of deploy CLIs afterwards.

## 5. What's in this repo

```
index.html        landing page with links to new/ and old/
new/index.html    the current prototype (single self-contained component file)
new/support.js    the DC runtime (do not edit)
new/_blob/        photos (.jpg) and the lock-screen background video (.mp4)
new/rationale/    design rationale page
old/              the original version, same structure
dev/              the build scripts used in the previous session (reference only)
HANDOFF.md        this file
```

Run it with `python3 -m http.server 8000`, then open `/new/`. Use a server, not `file://`.

The GitHub repo is `github.com/Leqih/ping-AI`. The previous session could not push to it (proxy 403, repo not authorized), so Leqi uploads this repo by hand.

## 6. How the prototype is built (read before editing `new/index.html`)

- It's a **DC component**: `<script type="text/x-dc">` with `class Component extends DCLogic`, rendered by `support.js`.
- **Template:**
  - `<sc-if value="{{x}}">` and `<sc-for list="{{arr}}" as="it">`, with `{{bindings}}` that come from `renderVals()`.
  - Event handlers are functions returned from `renderVals` (`onClick="{{fn}}"`).
  - State is changed with `this.setState(...)`; a `set({...})` helper returns a handler.
- **Quirks:**
  - `sc-for` reuses DOM elements by index. A newest-first list therefore reuses rows: animate by detecting a changed first row.
  - `prevState` passed to `componentDidUpdate` is empty, so the code keeps its own `this._pvState`.
  - `data-lc="1"` opts text out of an automatic sentence-case observer.
  - Text bindings next to elements inside a flex span become separate flex items, so wrap the text in its own `<span>`.
- **Key data maps inside `renderVals`:**
  - `HUNT`: per-card hunt steps (`nodes`), done copy.
    - A node is `{ t, text }` (a work step), or a stop: `{ key, q, opts }` (a choice), `{ hold:true, yes, no }`, or `{ pay:true, rows, total }`.
  - `GP`: confirm-sheet rows per card, as `[label, options, default, presetKey]`. Preset keys flow into the hunt answers `a.*`.
  - `ROWS`: result ticket rows. `TQ`: suggested task-chat prompts. `INS` / `AUTOL` / `AUTON`: Insiders and autonomy labels.
  - `liveAll`: live hunts with `needs` and `beat` (the short "Ready" pause before needs shows).
- **Key state:**

  | Key | Meaning |
  | --- | --- |
  | `stackSel` | open card |
  | `gk` | confirm sheet |
  | `tk` | task page |
  | `hs` | hunt states |
  | `dActs` / `dPass` | acted / passed |
  | `insK` | open Insider chat |
  | `insSet` | Insider settings sheet |
  | `auto` | autonomy per Insider |
  | `askOpen` | Ask overlay |
  | `nhChat` | new-hunt chat |
  | `needSeen` | releases the needs state after the beat |

- **Motion helpers:**
  - `_gridFlip`, `_followCard`, `_pillSlide`, `_tabSwitch`;
  - `_pushTrack` (ghost-out for pages and sheets), `_foldTrack` / `_dismiss` (cards leaving and gliding), `_stripTrack`;
  - `_micro()` (segmented thumb, number roll, `.swap` text crossfade, timeline rows).
- **Previous workflow:** the old session regenerated `new/index.html` from `old/index.html` through a chain of patch scripts (`dev/build3.sh` → `retheme.py` → `post*.py`). In a new session it is simpler to **edit `new/index.html` directly** and keep the `dev/` scripts as history.
  - If you do edit directly, change `_blob/...` paths with care. They are relative and carry extensions in this repo, while the original build used `/_blob/<hash>` with no extension.
- **Testing:** use Playwright with Chromium.
  - The phone frame is `div[style*="width: 390px; height: 844px"]`.
  - Enter the app with the "PING" button on the lock screen.
  - Click card CTAs by their text.

## 7. Open ideas / next steps

- Enrich the other scenarios the way Markets was done. Each needs realistic steps, a scenario-specific result block and specific chat replies.
  - Nova Lanes secret show (queue)
  - Suede bomber (deposit hold)
  - Opening-night IMAX (seats)
  - Tin Toy restock
  - Lumen Studio salon
  - Sunday Stack fantasy swap
- **Strongest demo path today:** Osteria Vela.
  1. Try to hold, then the sheet.
  2. The progress bar runs, then the strip.
  3. Decide, then confirm.
  4. The ticket result, then the forward bar.
  5. Open "MANAGED BY", then the settings sheet.
- **Second path:** Markets, from "Review copy trade" to the Face ID buy and the position view.
- Possibly sync key screens back into the Figma prototype.
