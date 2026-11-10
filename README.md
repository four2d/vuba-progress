# Vuba Measure progress

Live page: <https://four2d.github.io/vuba-progress/>

This public repository is the **single source of truth** for the Vuba Measure progress page. It shows where the iPhone and Android apps are, what is left to do, and the feature checklist. Do not keep a second copy elsewhere.

The work order is [NEXT.md](NEXT.md). Read that before you edit the page. If its first line is waiting on Pete, stop.

## How to update

Edit the files in this repository, then push to `main`. GitHub Pages publishes from `main`.

1. `git pull --ff-only` first. Never force-push.
2. Edit `features.json` for checklist ticks and percentages. Edit `index.html` for the facts on the page (date, callouts, what’s next, blockers, timelines). Edit `NEXT.md` when the work queue changes.
3. Do not put passwords, keys, tokens or the demo login password in this repository.
4. Make sure `features.json` is still valid JSON (`python3 -m json.tool features.json`).
5. Commit and `git push` to `main` (fast-forward only). Do not force-push.

Update after every significant change, and at least once an hour while work is in progress on the apps. If nothing has changed, do not update the files.

## How to tick an item

The checklist and every percentage on the page come from **`features.json`**. Do not type percentages into the page.

1. Find the item by its `id` in `features.json`, for example `"camera-measure"`.
2. Set that platform’s `state` to one of these:
   - `done`: finished, and checked on a real phone or console where that applies
   - `part`: built or drafted, but not checked or not finished
   - `todo`: not done
   - `na`: does not apply
3. Change the `note` so it says what is true now. Keep it short and factual. Never put a password, key or token in it.
4. Change `"updated"` to today’s date.
5. Make sure the file is still valid JSON, then commit and push.

To add an item, copy one that already exists and give it a new `id`. If a platform does not apply, leave that key out.

If someone clicks a box on the page, the tick is stored only in that browser’s localStorage and is labelled “Local tick, not yet saved”. It does not change the file or the percentages. To make it real, edit `features.json`.

## What else to edit in `index.html`

Edit only the facts.

1. The date line at the top (`.asof`) and in the footer.
2. The top `.call` and the two fixed stats (TestFlight build, public releases).
3. The `platforms` array in the script: tracks, rails, timeline points and the call line. A timeline point is `now` when it is on a phone, `past` when it is older and reached a phone, and `wait` when it is only on GitHub or not uploaded. Add a point only if you have a date.
4. `stageRows`, which feeds the four-step chart.
5. The `#gap` callout. Once build 12 or a later build is on the phone, rewrite it or remove it.
6. What’s next (`#next`) and Blockers (`#blockers`).

Do not invent a public release, a company number or a store state. Re-open App Store Connect or Play Console before you quote a version.

## When to update

Update when any of these change:

- The App Store Connect version state, the attached build, or a new TestFlight build
- What is on a phone compared with what is only on GitHub (the `#gap` callout)
- Anything in Play Console
- A checklist item that is finished or newly started
- A blocker that is cleared, or a new one
- The website pages the apps link to

## Brand

Leave the layout, colours and type alone.

- Colours come from the live site’s `vuba.css` and the app `Theme.swift` / `Theme.kt`: charcoal `#111A1F`, panel `#152028`, slate `#1A242C`, mist `#E8EEF2`, soft `#9AA7B2`, blue `#035B80`, light blue `#006F9C`, red `#821732`.
- Poppins 400, 700 and 900 are in `fonts/`, copied from the Android app. They are under the SIL Open Font License (`fonts/OFL.txt`).
- The logo is `vuba-logo-white.svg`, the same file as the live site’s header and the iPhone app’s `VubaMark`. The VUBA and WILTSHIRE wordmark is live text set like the site header. Do not redraw the logo.
