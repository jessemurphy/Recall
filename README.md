# Recall PWA

The interim product while the native iOS app (`RecallIOS/`) waits for
commercialization: a full offline-capable web app you install from Safari's
share sheet. Same scheduler, same cloze syntax, plus what the artifact
prototype couldn't do — **photos on cards** (downscaled to ≤1200px,
stored in IndexedDB) and **Export/Import backup** (a JSON file that is
also the future import format).

No accounts, no server-side anything: the four files here are static, and
all data stays on the phone.

## Publish (one time, ~5 minutes, needs a computer)

GitHub Pages is free for **public** repos only, so this lives in its own
tiny repo rather than familynet:

1. github.com → New repository → name `recall`, Public, no README.
2. On any machine with this branch checked out:

       cd familynet/recall-pwa
       git init -b main && git add . && git commit -m "Recall PWA"
       git remote add origin git@github.com:jessemurphy/recall.git
       git push -u origin main

3. Repo → Settings → Pages → Source: "Deploy from a branch",
   branch `main`, folder `/ (root)`. Save.
4. A minute later it's at `https://jessemurphy.github.io/recall/`.

## Install on the iPhone

Open that URL in Safari → Share → **Add to Home Screen**. It opens
full-screen with its own icon, works offline after the first load, and its
storage lives in the app's own container (not subject to Safari's 7-day
browsing-storage purge — and a daily review habit resets any idle clock
anyway). Still: tap **Export backup** on the decks screen now and then.

## Updating later

Push changes to the `recall` repo; Pages redeploys automatically. The
service worker is network-first, so an installed app picks up new versions
on the next online open. Bump the `CACHE` name in `sw.js` when changing
files other than index.html.

## What's deliberately not here

Anki/CSV import (later, per plan), push notifications (possible on iOS
16.4+ installed PWAs if a "cards due" nudge ever feels wanted), and any
kind of account or sync — the App Store build is the commercial vehicle;
this is the daily driver until then.
