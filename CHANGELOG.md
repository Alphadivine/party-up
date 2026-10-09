# Changelog

## 2026-10 — Add to your library, compare inventories, own-launcher games (v1.7.0)

- **Add a game** now starts with a choice at the top: **My library · I own it** or **Wishlist · want it**. Library adds ask which platform(s) you own it on (your own is pre-ticked); wishlist adds keep the "Why should we get it?" note and your 👍. Opening Add from the Wishlist tab starts on Wishlist; anywhere else starts on My library.
- No more "Suggest" wording: buttons say **Add**, details say **Added by**, and the activity feed says "added X to their library" or "added X to the wishlist".
- **Compare** (third view in the Library, next to Cards and Who owns what): tick two or more people to see the games you all own and whether you can play them together, then the games only some of you own, with who's missing each one (and a sale note if it's on sale). Crew cards have a **Compare with me** button.
- New ownership option **PC (game's own launcher)** (shows as PC·L) for games like Path of Titans that come from their own launcher. It counts as PC for crossplay, and it's only offered under "I own it", not as a profile platform.
- Fixed: the search box in the Add dialog could stretch very tall.

## 2026-10 — Own games on more than one platform (v1.6.0)

- You can now own a game on several platforms (say PC and PlayStation). Game details show a checkbox for each platform: tick every one you have it on.
- **Who owns what** grid: tapping your cell opens a platform picker (with "I don't own it"), and each person's cell shows all their platforms.
- **I own…**: each game has platform buttons, so you can pick more than one; picking a platform ticks the game.
- **Add a game**: "I own it on" is now a set of checkboxes that follows the game's platforms.
- Crossplay checks, "Ready tonight" and stats use every platform you own a game on.
- Existing ownership (one platform per person) keeps working; no database changes needed.

## 2026-10 — Who can play what, IGDB game data (v1.5.0)

- Every card now shows who can play and on what: ✔ Quentin · XB, ✔ Sam · PC·GP, ✖ Mia · PS (plays separately). Library cards show it for everyone who owns the game, Wishlist cards for everyone interested, and game nights for everyone who's in. Game details show it for the interested players and the whole crew, with the reason when someone can't join.
- IGDB is connected (Worker: partyup-games.quentinclayton643.workers.dev). IGDB support comes through a small Cloudflare Worker (`Worker/worker.js`): accurate platforms, landscape art, genres, and online co-op player limits that fill in party size automatically. Falls back to Wikipedia + Wikidata if it's not set up or down. See `Docs/Setup guide (IGDB).md`.
- Steam store links read the official title, description and art through the Worker.
- Fixed: a pasted store link could pick up a different game if search didn't find an exact match; it now only accepts a matching title.
- A store's "cross-platform multiplayer" tag no longer auto-marks a game as full crossplay (it can mean PC + Mac only); it's added as a note to check.

## 2026-10 — Library + Wishlist, store links, sales, stats, guide (v1.4.0)

- Party Up is now the crew's game inventory. **Library** holds every game someone owns (free-to-play counts as everyone's); **Wishlist** holds games nobody owns yet, with votes and prices. The old Queue / Playing / Played tabs became status chips inside the Library.
- **I own…**: tick every game you own in one go, with the platform for each. Games not on the list (from the 110 built-in) get added automatically.
- **Who owns what**: a grid of every library game × every person. Tap your own column to mark a game, tap again to change platform or clear it.
- **Ready tonight**: games at least two people own and can play together; shown on cards, in the grid and as a filter.
- **Per-person library**: "Everyone's games" menu, plus "View library" on each Crew card.
- **Paste a store link** to add a game: Steam, Xbox, Epic and GOG links fill in the title, art and platforms. "I own it" while adding puts it straight in the Library.
- **Sale alerts**: sale badge with % off and price on cards, an "On sale" filter, lowest-price-ever in each game's details; wishlist prices refresh daily.
- **Stats** tab: library size, games ready tonight, awards (biggest collection, most games added, never misses a night, most 👍), games per person, what the crew plays, platforms, crossplay mix, most-played on game nights, most wanted on the wishlist.
- **How-to guide** in the app: opens on first visit and from the ? button.
- **Wikidata**: games looked up through Wikipedia now get their real platform list, genres, multiplayer modes and release date (RAWG signup is down).

## 2026-10 — Fix "Not on anyone's platform" (v1.3.2)

- Fixed: the "can we play together" check only looked at each person's main platform, so a game on Xbox showed "Not on anyone's platform" for people whose main platform was PC even though they also own an Xbox. It now considers every platform in each person's profile (or the one they marked as owning) and picks whichever lets the most people play together.
- Clearer messages: "Not on anyone's platforms (XB only)", "1 of 2 can play on XB · Sam doesn't have XB".
- The person who suggested a game (or the leader) can now fix its platforms in the game's details, for games whose platforms were guessed wrong.

## 2026-10 — Whole theme follows your color (v1.3.1)

- Your color now tints the whole app, not just buttons: backgrounds, cards, borders and text tints all follow it, in dark and light mode. Every color keeps text readable (4.5:1 or better).
- The phone/browser bar color matches your theme.
- Status colors (crossplay badges, warnings) stay the same in every theme so they keep their meaning.

## 2026-10 — Status line, timezones, profile pictures (v1.3.0)

- Status line: a short status on your profile ("Grinding Helldivers · free after 9"), shown on the Crew tab and when hovering your avatar.
- Timezones: each person's timezone is detected from their device and can be changed in their profile. Game night times show in your own timezone with its abbreviation, plus friends' local times when they're somewhere else ("Their time: Sam 9:00 PM EST"). Planning a night uses your timezone. The Crew tab shows each person's local time.
- Profile pictures: choose your Google photo, upload a picture (resized to a small square and saved on your profile, no extra storage needed), pick one of 12 game icons in your color, or use your initials.
- Firestore rules: profile size limits for uploaded pictures and the status line. Re-publish `Firebase/firestore.rules`.

## 2026-10 — Game nights, activity feed, your color (v1.2.0)

- New look: purple color theme (dark and light) and a controller logo, with new app icons and favicon.
- Your color: each person picks their own accent color in their profile; the app takes on that color for them only, synced across devices, and it rings their avatar so friends are easy to tell apart.
- Game nights: a new Nights tab to plan a night (date, time, game or "decide later", note), RSVP In / Maybe / Out, see whether everyone who's in can play together, and add it to a calendar. The next night shows at the top of the queue.
- Party-size check: max party size for the built-in games (editable on any game); warnings when more people want in than the game allows; "Whole crew fits" now respects it.
- Activity feed: a bell in the header with a new-items dot, listing suggestions, 👍 votes, status changes, game nights, RSVPs and new members.
- Trailer button on every game, and trailer links in Ideas.
- Cover art: official store art for all 110 built-in games; Steam art as a fallback; games saved without art (like Fortnite before) fill it in automatically; broken images fall back cleanly.
- Ideas tab shows when the crossplay list was last checked; a monthly scheduled task re-checks it.
- Firestore rules: new rules for game nights and the activity feed, and maxParty/cover added to the fields any member can update. Re-publish `Firebase/firestore.rules`.

## 2026-10 — Renamed to Party Up (v1.1.0)

- App renamed from Squad Queue to Party Up: page title, header, sign-in screen, installed-app name, README and setup guide.
- Site moved to https://alphadivine.github.io/party-up/ (GitHub repo renamed from squad-queue to party-up).
- Service worker cache renamed, so installed copies pick up the new name on their next visit.
- No data changes: the group, games, votes and Firebase project carry over as-is.

## 2026-10 — First release (v1.0.0)

- Shared game-suggestion board with Google sign-in, a join code, and a group leader.
- Suggest games by name: details and cover art from RAWG (with a key) or Wikipedia.
- Built-in crossplay list of 110 multiplayer games, researched October 2026, with a source link per game.
- "Can we all play together?" check per game, based on who voted and what platform they play or own it on, including partial-crossplay cases (e.g. Xbox + Game Pass PC only).
- 👍 / 🤷 / 👎 voting with a most-wanted ranking.
- "Who owns it" per person and platform.
- Live PC price and best deal from CheapShark; console price, Game Pass and PS Plus as shared fields.
- Store links (Steam, Epic, PlayStation Store, Xbox Store, best PC deal).
- Statuses (Suggested, Up next, Playing, Finished, Dropped) and shared notes.
- Ideas tab to browse and suggest from the checked list; Crew tab with platforms and gamer tags.
- 🎲 Pick tonight, filters and sorting, phone layout, light/dark theme, installable PWA, demo mode without Firebase.
- Firestore security rules: members only; each person can change only their own vote and ownership; leader or suggester can remove a game.
