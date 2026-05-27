# Cybersec Path — Summer 2026 Tracker

A personal, single-file web app that tracks my Summer 2026 cybersecurity prep plan
(CompTIA Security+ SY0-701 · TryHackMe Pen Test path · portfolio project rebuild)
across 14 weeks from May 27 to August 31, 2026.

No backend, no build step, no framework. Just one HTML file with embedded CSS and JS,
plus optional cloud sync through a private GitHub Gist so the same data follows me
between laptop and phone.

---

## Table of contents

1. [What this tracks](#what-this-tracks)
2. [Live site / running it](#live-site--running-it)
3. [How the app works, tab by tab](#how-the-app-works-tab-by-tab)
4. [GitHub Gist cloud sync (optional)](#github-gist-cloud-sync-optional)
5. [Hosting your own copy on GitHub Pages](#hosting-your-own-copy-on-github-pages)
6. [Data, privacy, and storage](#data-privacy-and-storage)
7. [Customizing the plan for your own goals](#customizing-the-plan-for-your-own-goals)
8. [Tech notes](#tech-notes)
9. [License](#license)

---

## What this tracks

The plan has three parallel tracks running across 14 weeks:

| Track | Total work | Time per active day |
| --- | --- | --- |
| **TryHackMe Pen Test path** | 92 hours remaining | 2 hours |
| **CompTIA Security+ SY0-701** | 121 Professor Messer videos (~15 hrs) | 1 hr video + 30 min notes/Anki |
| **Portfolio rebuild** | 30 hours, starting after Sec+ pass | (concentrated in Aug 5–31) |

Active study days are roughly 5 per week (not 7) — about 3.5 hours total per active day.
The plan explicitly allows one full rest day per week and a 5-day vacation block.

Phase milestones to celebrate when hit:

- ◆ Pen Test path complete (mid–late July)
- ● Security+ exam booked (early–mid July)
- ★ Security+ exam **passed** (first week of August)
- ▲ Portfolio project shipped (end of August)

---

## Live site / running it

Three ways to use it:

**1. As a hosted site (recommended).** Push this repo to GitHub, turn on Pages, get a URL like
`https://<your-username>.github.io/<repo-name>/`. Open it on any device, save the page
to your home screen on mobile — it behaves like a native app.

**2. Locally on your computer.** Just double-click `index.html`. It opens in your default browser
and works fully offline. Progress saves to that browser's `localStorage`.

**3. Run from a USB stick or any folder.** Same as local — no installer, no permissions.
Just an HTML file.

---

## How the app works, tab by tab

### Dashboard

The high-level view. Top row of stats:

- **Day of summer**: how many days into the 97-day window you are.
- **Days remaining**: until Aug 31.
- **Current streak**: consecutive days (counting back from today) where at least one
  daily checkbox was ticked.
- **Hours logged total**: cumulative hours across all three tracks since May 27.

Three progress bars for the three tracks:

- **TryHackMe**: total hours logged on the pen-test track vs the 92-hour goal.
- **Security+**: cumulative Professor Messer hours watched vs ~15 hours of video.
  Each day you tick the Messer checkbox counts as one hour. Below the bar, an estimated
  current section (1–5) based on cumulative video hours.
- **Portfolio**: hours logged on study days inside the Aug 5–31 project window, vs 30.

Then a **"this week"** card that shows your current week's targets pulled straight from the plan,
and the four phase milestones (the only manual checkboxes left in the app — they're for
celebration, not bookkeeping).

### Today

Where you actually log your day. The date defaults to today but you can backfill any
day in the May 27 – Aug 31 window with the date picker in the top-right.

Three checkboxes mirroring the plan's daily structure:

| Box | What to log |
| --- | --- |
| **Messer video (1 hr)** | The section + video title you watched. |
| **Notes / Anki (30 min)** | Topics you took notes on, cards reviewed. |
| **TryHackMe (2 hrs)** | Room/box name + how many hours you actually put in (default 2). |

Plus a free-text **day notes** field for wins, blockers, things to revisit.

Everything auto-saves on every keystroke / checkbox click — no save button to forget.

### Weeks

The 14-week roadmap as a table, with **everything auto-computed from your daily logs**.
Columns:

| Column | What it means |
| --- | --- |
| **Wk / Dates** | Week number and date range. The current week is highlighted green. |
| **Pen Test goal** | Cumulative TryHackMe hours target from your plan (e.g., "28 hrs total"). |
| **Security+** | What you should be doing in Sec+ that week. |
| **Project** | Portfolio work, mostly in weeks 11–14. |
| **Hours** | Total hours you actually logged in that week (Messer + Notes + THM). |
| **vs target** | Cumulative pen-test hours logged through end of that week vs the plan's target. Color-coded. |
| **Days** | Active days out of days that have passed in the week (e.g., "3 / 4 so far"). |
| **Status** | Auto pill: `✓ on pace` / `→ catching up` / `⚠ behind` / `→ in progress` / `upcoming`. |

No manual checkboxes here — the table reflects reality based on what you've logged.
If you fall behind on hours, you'll see it immediately in red.

The off-day rules from the plan are tucked into an expandable section at the bottom.

### Calendar

GitHub-style heatmap: 14 columns (one per week) × 7 days. Each cell's color intensity
reflects hours logged that day:

| Cell | Hours |
| --- | --- |
| Empty | 0h |
| Faint green | < 1h |
| Light green | 1 – 2.5h |
| Medium green | 2.5 – 4h |
| Bright green | ≥ 4h |

Click any cell to jump to the Today tab for that date — useful for backfilling.

Below the heatmap: active days vs elapsed days, longest streak ever, average hours per active day.

### Settings

- **GitHub Gist sync**: paste a PAT + Gist ID to enable cloud sync. See the next section
  for setup steps.
- **Data**: state size in bytes, last save time, **Export JSON** (download your data),
  **Import JSON** (load from a file), **Reset all** (wipe local data — does not touch the cloud copy).
- **Plan reference**: a quick-glance summary of the goal, daily routine, exam threshold,
  and links to Professor Messer and TryHackMe.

---

## GitHub Gist cloud sync (optional)

Without sync, your progress lives only in the browser you're using. If you want the
same data on your laptop and your phone, you can sync through a free GitHub Gist.

The app never touches any server except `api.github.com`. The token lives only in
your browser's localStorage.

### Step 1 — Personal Access Token

1. Go to <https://github.com/settings/tokens?type=beta> (fine-grained tokens).
2. Click **Generate new token**.
3. Token name: `cybersec-tracker`. Expiration: your call (90 days, custom, or no expiration).
4. Scroll to **Account permissions** → find **Gists** → set to **Read and write**.
   You do **not** need any repository permissions.
5. Click **Generate token**. **Copy the token immediately** (starts with `github_pat_`) —
   GitHub only shows it once.

### Step 2 — Create a secret gist

1. Go to <https://gist.github.com>.
2. Filename: `cybersec-progress.json` (must match exactly).
3. Content: `{}` (open and close brace).
4. Click the dropdown next to the button at the bottom and pick **Create secret gist**.
5. From the URL after creation — `https://gist.github.com/<you>/<gist-id>` — copy the
   long hex string at the end. That's your **Gist ID**.

### Step 3 — Connect

1. In the app, go to **Settings**.
2. Paste your token into **GitHub Personal Access Token**.
3. Paste your Gist ID into **Gist ID**.
4. Click **connect & sync**.

The status indicator at the top right turns green and reads "synced". From then on,
every change is auto-pushed (debounced ~1.5 s) and the latest data is pulled on every page load.

**Buttons in the sync section:**

- **connect & sync**: validate credentials, then either pull (if the gist already has data)
  or push (if it's empty / just `{}`). The app will ask you which when there's a conflict.
- **sync now**: force-push current local state.
- **pull from cloud**: force-pull and overwrite local. Useful if you made changes on another device.
- **disconnect**: forgets the token and gist ID. Local data is untouched.

---

## Hosting your own copy on GitHub Pages

1. Create a new repo (public is easiest). Don't initialize with a README.
2. From your project folder, run:
   ```bash
   git init -b main
   git add .
   git commit -m "initial commit"
   git remote add origin https://github.com/<you>/<repo>.git
   git push -u origin main
   ```
3. In the repo settings on github.com: **Settings → Pages → Source** = `Deploy from a branch`,
   **Branch** = `main / (root)`, **Save**.
4. Wait ~30 seconds, refresh. Pages shows the live URL.
5. **Important**: this repo includes a `.nojekyll` file. That tells Pages to skip Jekyll
   processing — necessary because the JavaScript uses `${...}` template literals that
   Jekyll would otherwise try to parse as Liquid template tags and fail on.

**To deploy updates** later: edit `index.html`, then:
```bash
git add -A && git commit -m "update" && git push
```
Pages redeploys within a minute.

**To add it to your phone**: open the live URL in Safari/Chrome on your phone →
**Share** → **Add to Home Screen**. It becomes a full-screen app icon.

---

## Data, privacy, and storage

- **Local data** lives in your browser's `localStorage` under two keys:
  `cybersec_path_v1` (progress) and `cybersec_path_settings_v1` (PAT + gist ID).
- **Cloud data** (if sync is on) lives in your private GitHub Gist as a JSON file
  named `cybersec-progress.json`. Only you can read or write that gist.
- **No telemetry, no analytics, no third-party scripts.** The app never talks to any
  server except `api.github.com` for sync, and only when you've turned sync on.
- **Exporting / backing up**: Settings → Export JSON downloads everything as a single file
  you can stash anywhere.
- **Wipe**: Settings → Reset all clears local data. Cloud copy is unaffected unless
  you sync again afterward.

---

## Customizing the plan for your own goals

The plan-specific data is all in one constants block at the top of the `<script>` in
`index.html`. Find:

```js
const START_DATE = "2026-05-27";
const END_DATE   = "2026-08-31";
```

and:

```js
const WEEKS = [
  { wk:1, start:"2026-05-27", end:"2026-06-02", thm:14, thmDesc:"...", sec:"...", proj:"" },
  ...
];
const PHASES = [
  { id:"penTestComplete", title:"Pen Test path complete", desc:"..." , icon:"◆"},
  ...
];
```

Change the dates, the per-week targets (`thm` is cumulative target hours), the descriptions,
and the phase milestones, and the entire app re-orients around your plan.

The three daily checkboxes are defined in the HTML (`<section id="view-today">`) — you
can rename them and the fields they capture if your routine is different.

---

## Tech notes

- **Single file**: `index.html` is ~50KB, no external dependencies, no build step.
- **Vanilla JS** only. No React, no jQuery, no bundler. Just `addEventListener` and `fetch`.
- **CSS** uses custom properties for theming. The dark hacker palette is defined in `:root`.
- **Mobile-responsive** down to 380px viewport. The heatmap and weeks table scroll
  horizontally on narrow screens.
- **Sync uses** GitHub's REST API (`PATCH /gists/:id` to push, `GET /gists/:id` to pull),
  authenticated with a Bearer token. Writes are debounced 1.5 s to avoid hammering the API.
- **Date math** is timezone-naive (everything is calendar-local). Dates are compared as
  `YYYY-MM-DD` strings, which sort lexicographically the same as chronologically.
- **Browser support**: tested in modern Chrome, Safari, and Firefox. Requires ES2017+
  (async/await, template literals). Won't run in IE11.

---

## License

Personal project, MIT. Take it, fork it, change every date — make it yours.
