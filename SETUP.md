# For You — setup

5 files. Host them anywhere free, then she adds the page to her home screen.

---

## 1. Put it online (GitHub Pages — recommended)

This is the one to pick, because it lets you edit tomorrow's message **from your phone** in about 20 seconds.

1. Go to github.com, make a free account if you don't have one.
2. Click **New repository**. Name it anything (`for-you`). Set it to **Public**. Create.
3. On the repo page: **Add file → Upload files**. Drag in all 5 files (`index.html`, `messages.json`, `manifest.json`, `icon.png`, `icon-512.png`). Commit.
4. **Settings → Pages**. Under "Branch" pick `main` / `/ (root)`. Save.
5. Wait ~1 minute. Your URL appears there: `https://yourname.github.io/for-you/`

> "Public" means the URL is technically findable, but nobody will ever stumble on it. If that bothers you, use Netlify below instead — it gives you a random URL that isn't indexed.

**Alternative — Netlify (60 seconds, no account needed to start):**
Go to app.netlify.com/drop, drag the whole folder onto the page. You get a live URL instantly. To update a message you re-drag the folder, so it's a bit more work day to day.

---

## 2. Add it to her home screen

On her iPhone:

1. Open the URL in **Safari** (must be Safari — Chrome can't do this).
2. Tap the **Share** button (square with the up arrow).
3. Scroll down → **Add to Home Screen** → Add.

Done. There's now a heart icon on her home screen. Tapping it opens fullscreen — no address bar, no Safari chrome. It looks like a real app.

---

## 3. Writing the daily message

Open `messages.json` on GitHub (tap the file → pencil icon) and add an entry:

```json
{
  "date": "2026-07-28",
  "text": "Your message here."
}
```

Rules:

- Date format is `YYYY-MM-DD`.
- Every entry needs a comma after it **except the last one**.
- Order doesn't matter — it sorts itself.
- Commit the change. It's live in under a minute.

**If you skip a day**, the most recent message you wrote stays up — she'll see yesterday's again rather than an empty screen. If she opens it before you've ever written one, she gets the `fallback` line.

You can also write a week ahead of time by adding several dated entries at once.

### Editing the other bits

- `"signoff"` — the italic line under every message (`— always, me`).
- `"fallback"` — what shows if there's no message at all yet.
- `"_howto"` — just a note to yourself, the app ignores it.

⚠️ JSON is picky. If the app suddenly shows only the fallback message, you probably have a missing or extra comma. Paste the file into jsonlint.com to find it.

---

## What it does

- Opens to a slow-beating, floating heart with "tap the heart" underneath.
- On tap: soft haptic buzz, the heart swells and dissolves, twelve small hearts scatter outward, then today's message fades up.
- Small `♥` under the message takes her back to the heart if she wants to open it again.
- If she leaves the app running overnight, it re-checks for a new message when she comes back to it.

## Changing the look

Everything is in `index.html`.

- Background colors: the `body` background gradient near the top.
- Heart color: the `#hg` gradient stops inside the `<svg>`.
- Message font: the `#message` rule (currently New York / Georgia serif).
- Hint text: search for `tap the heart`.
