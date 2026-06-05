# Guardian Clock — Destiny 2 Playtime Tracker

A single-file web tool that shows total and per-character time played for any Destiny 2 player. No server, no install — just `index.html`. Talks directly to the official Bungie.net API.

---

## Quick start (local, search only)

1. Open the [Bungie application portal](https://www.bungie.net/en/Application) and open your app (**ID 47366**).
2. Set **Origin Header** to `*` and save. *(This is what allows a browser to call the API.)*
3. Double-click `index.html`. Type any Bungie Name like `Guardian#1234` and hit **Track Playtime**.

That's it for searching other players. The player's Destiny privacy must allow stats to be public (the default).

> **Why the `*` origin?** When a browser calls Bungie, it sends an `Origin` header. Bungie rejects it unless your app's registered origin matches. `*` accepts any origin, including the `null` origin a local file uses.

---

## Enabling "Sign in with Bungie" (yourself)

Sign-in lets you load **your own** profile in one click and works even if your profile is private. It also sets you up for the inventory features later. It only works when the page is **hosted at an https URL**, because Bungie OAuth requires a registered redirect.

In the Bungie portal for your app:

1. **OAuth Client Type** → set to **Public** (a static web page can't keep a secret, so it must be a public client — never put a client secret in this file).
2. **Redirect URL** → set to your hosted page URL, e.g. `https://yourname.github.io/guardian-clock/`.
3. Save.

---

## Hosting it free on GitHub Pages (~5 minutes)

This gives you a public https link you can share with friends, and makes sign-in work.

1. Make a free account at [github.com](https://github.com) if you don't have one.
2. Click **+ → New repository**. Name it e.g. `guardian-clock`, set it **Public**, click **Create repository**.
3. On the new repo page, click **uploading an existing file**, then drag in `index.html` (and this `README.md`). Click **Commit changes**.
4. Go to **Settings → Pages**. Under *Build and deployment*, set **Source = Deploy from a branch**, **Branch = main**, **Folder = / (root)**. Click **Save**.
5. Wait ~1 minute. The page shows your live URL: `https://yourname.github.io/guardian-clock/`.
6. Put that exact URL into the Bungie portal's **Redirect URL** field (step above). Done — share the link with friends.

To update later, just re-upload a changed `index.html` to the repo.

---

## What it shows

- **Total time played** (days / hours / minutes)
- **Per-character** cards — class, power level, that character's time, share of total, last played
- **By activity type** — PvE, Crucible, Gambit, etc. (when available)
- **Perspective** — fun comparisons (work weeks, etc.)

Time played = seconds spent inside activities. It excludes idle time in orbit and social spaces, matching how Bungie reports it.

---

## Notes & next steps

- **API key is visible** in the file. That's normal and expected for Bungie browser apps — the key only identifies the app and grants read access to public data. Don't add a client *secret*.
- Planned expansions: filters and date ranges, player-vs-player comparison, and the inventory tracker (uses sign-in for private data).

*Not affiliated with Bungie. "Destiny" is a trademark of Bungie, Inc.*
