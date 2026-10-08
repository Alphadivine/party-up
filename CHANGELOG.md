# Changelog

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
