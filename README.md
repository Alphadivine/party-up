# ▶▶ Party Up

A shared game inventory for you and your friends. Everyone adds the games they own (or want), you compare libraries to see what you all have, and the app tells you straight away whether the people who want to play can actually **play together across PC, PlayStation and Xbox**, where to buy it, and what it costs.

Party Up is a single self-contained `index.html` (plus a data file). No build step, no server of your own: it runs in the browser and stores shared data in a free [Firebase](https://firebase.google.com) (Firestore) project.

> **Live site:** **https://alphadivine.github.io/party-up/**

---

## ✨ Features

- **Library + Wishlist**: the Library is everything the crew owns, with who owns it and on what; the Wishlist is games nobody owns yet, with votes and prices. Mark many games at once with **I own…**, see a **Who owns what** grid, filter to **Ready tonight** (2+ owners who can play together) or to one person's games.
- **Simple layout**: four tabs (Library, Wishlist, Nights, Crew), a toolbar with just Search, Filters and ＋ Add, and a Cards / List / Who owns what / Compare switch on the Library. Phones start in the compact List view.
- **＋ I have this too**: mark a game a friend owns in one tap, right on its card. Changes come with **Undo**.
- **Tap a tag to learn what it means** (Full crossplay, PC·GP, Up to 4, Ready…), and a **Get started** checklist for new members.
- **Filters panel**: one Filters button for platform owned on, genre, party size, type, ownership (like "I don't have it" or "Everyone owns it"), plus Ready tonight, On sale, Crossplay and more.
- **Compare inventories**: pick two or more people to see the games you all own, whether you can play them together, and who's missing the rest. Crew cards have **Compare with me**.
- **Add to My library or Wishlist**: choose at the top of Add a game; library adds ask which platforms you own it on.
- **Who can play what**: every card shows each person and the platform they'd play on, with ✔ / ✖ and the reason when someone can't join.
- **Paste a store link**: Steam, Xbox, Epic and GOG links fill in the game for you.
- **Sale alerts**: % off badges, an On sale filter and lowest-price-ever notes.
- **Stats**: awards and what the crew plays most.
- **Built-in guide**: shows on first visit and from the ? button.
- **Add a game by name**: type a title and pick it from the results. A description is pulled in automatically (from [RAWG](https://rawg.io) if a key is set, or from [IGDB](https://www.igdb.com) through the optional Party Up Worker; otherwise Wikipedia plus Wikidata for platforms, genres and release dates). Wishlist games can carry a note on why the crew should get it.
- **Cover art for every game**: all 110 built-in games carry official store art (Steam, or the PlayStation / Epic store for games not on Steam). Other games use RAWG or Wikipedia art, then fall back to Steam art; games saved without art fill it in automatically.
- **Crossplay you can trust**: a built-in list of **110 popular multiplayer games** with crossplay checked in October 2026 and re-checked monthly by a scheduled task (full / partial / none, cross-progression, player counts, free-to-play), each with a link to where it was verified. Anything not on the list can be filled in by whoever suggests it.
- **"Can we all play together?" check**: every card looks at who voted 👍 or 🤷 and what they play on, then says *"All 4 can play together"* or *"3 of 4 together · split: Sam (PS)"*. It understands awkward cases like Deep Rock Galactic, where Xbox and Game Pass PC play together but Steam and PlayStation don't.
- **Game nights**: anyone can plan a night with a date, time, game (or "decide later") and a note. Everyone answers In / Maybe / Out, the card checks that everyone who's in can actually play together, and there's an **Add to calendar** button. The next night shows at the top of the queue.
- **Party-size check**: games show their max party size (e.g. "Up to 4"), and the app warns when more people want in than the game allows, so nobody gets left out on the night.
- **Activity feed**: a bell in the header shows what's new: suggestions, 👍 votes, status changes, game nights, RSVPs and new members.
- **Trailers**: a "Watch trailer" button on every game, and a trailer link on every idea.
- **Profiles**: a status line, your timezone (auto-detected, editable) and a profile picture: your Google photo, an uploaded picture, one of 12 game icons, or initials.
- **Timezone-aware game nights**: times show in your own timezone, with friends' local times when they're in a different one.
- **Your color**: each person picks their own color (purple, blue, teal, green, orange, pink, red or gold). The whole app (backgrounds, cards and accents) takes on that color for them only, it syncs across their devices, and it shows as their avatar ring on the Crew tab and in vote lists.
- **Voting**: 👍 I'm in, 🤷 maybe, 👎 not for me. The queue sorts by most wanted, with #1, #2… badges.
- **Who owns it**: each person ticks every platform they have it on (PC and PlayStation, say; PC can be Steam / Epic, Game Pass, or the game's own launcher like Path of Titans), or that they don't own it, so you can see who still needs to buy it.
- **Prices & deals**: live PC price and the best current deal (with % off) from [CheapShark](https://www.cheapshark.com), refreshed every few days. Console price, Game Pass and PS Plus are tick-boxes anyone can fill in.
- **Where to get it**: links to Steam, Epic, PlayStation Store, Xbox Store and the cheapest PC deal.
- **Status tracking**: Suggested → Up next → Playing → Finished / Dropped, with shared notes (server name, mods, game night).
- **Ideas** (＋ Add → Browse ideas): browse the 110 checked games, filter by crossplay or type (co-op, survival, party, battle royale…), and add one in a tap.
- **Crew tab**: everyone's platforms plus Steam / Epic / PSN / Xbox / Discord names with copy buttons, so adding each other is easy.
- **🎲 Pick a game** (on Nights): picks a game the crew owns and can play together, falling back to the most-wanted wishlist games.
- **Sorting**: most wanted, most owned, newest, cheapest or A–Z.
- **Google sign-in with a join code**: only people with the code you set can see the list. The leader (whoever sets the group up) can remove people and change the code.
- **Installable app (PWA)**, phone layout with bottom tabs, light / dark / system theme, controller logo.

---

## 🧩 How it works

- **Frontend:** `index.html` (HTML + CSS + vanilla JS) and `data.js` (the built-in crossplay list, party sizes and cover art). The Firebase SDK loads from Google's CDN.
- **Game details:** [RAWG API](https://rawg.io/apidocs) with a free key, or Wikipedia (no key) as the fallback.
- **PC prices:** [CheapShark API](https://apidocs.cheapshark.com) (no key).
- **Storage & sync:** Firebase **Firestore** with live updates and **Firebase Auth** (Google). The Firebase web config in `index.html` is designed to be public; access is controlled by the rules in `Firebase/firestore.rules`.
- **Demo mode:** with no Firebase config, the app runs entirely in one browser (handy for trying it out).

---

## 🚀 Setup

See **`Docs/Setup guide.md`** for the full browser-only walkthrough. In brief:

1. Create a new Firebase project, turn on **Firestore** and **Google** sign-in, add your GitHub Pages domain to *Authorized domains*.
2. Publish `Firebase/firestore.rules`.
3. Paste your Firebase web config into the `CONFIG.FIREBASE` block near the top of the script in `index.html`. *(Optional: add a free RAWG key to `CONFIG.RAWG_KEY`.)*
4. Upload the contents of `Site/` to a GitHub repo and turn on GitHub Pages.
5. Open the site, sign in, create the group and choose a join code. Send friends the link and the code.

Use `?group=NAME` on the URL to run a separate group off the same database.

---

## 🔄 Updating

Replace `index.html` (and `data.js` if the crossplay list changed) in the repo and commit. GitHub Pages redeploys in about a minute; a hard refresh (Ctrl+Shift+R) shows it immediately.

To update the crossplay list, edit `Source/crossplay.json` and regenerate `data.js` with `Source/build_data.py` (or just ask Claude to do it).

---

## ⚠️ Notes & limitations

- **Crossplay changes.** The built-in list was checked in October 2026. Games add crossplay in patches (and occasionally lose it), so anyone can correct a game's crossplay and note from its details panel.
- **Partial crossplay is simplified** to which platforms play together. Details like "opt-in toggle" or "no cross-invites" are in the note.
- **Console prices, Game Pass and PS Plus** aren't available from any free API, so they're filled in by the crew.
- **PC prices** come from CheapShark's store list (Steam, Epic, GOG, Humble, Fanatical and others), in USD.
- **Wikipedia fallback** gives a shorter description and guesses platforms from the text; check the platform boxes when suggesting.

---

## 🙏 Credits

Game data from **[RAWG](https://rawg.io)** and **[Wikipedia](https://www.wikipedia.org)**. PC prices from **[CheapShark](https://www.cheapshark.com)**. Crossplay research mainly via **[iscrossplay.com](https://iscrossplay.com)** plus publisher pages. Database, auth and realtime by **[Firebase](https://firebase.google.com)**.

---

_Last updated: October 2026 (v2.0.2). Full change history in `CHANGELOG.md`._
