# MAZE TALES

A free ad-lib story game for the MAZE DINO – Puzzle Adventures platform. One static page, no server, no build step.

- Pick a tale, fill in the blanks without seeing the story, then reveal it with your words highlighted.
- A **daily tale** is the same for everyone each day (chosen by date). Eight tales to start.
- Copy the story, copy a share link, or save it to **My tales** (up to 20, kept in this browser).
- A "keep it family-friendly" switch (on by default) rejects words from a small block list. It is a basic filter, not a guarantee.

## Files

| File | Purpose |
| --- | --- |
| `index.html` | The whole game (HTML, CSS, JS, and all stories) |
| `assets/maze-dino-logo.jpg` | The MAZE DINO logo banner, same file as the other two games |

## Publish on GitHub Pages

1. Put `index.html` in the root of the `maze-tales` repo and the logo at `assets/maze-dino-logo.jpg`.
2. Settings → Pages → "Deploy from a branch" → `main` → `/ (root)`.
3. The game appears at `https://aiontrust.github.io/maze-tales/`.

## Points (shared with Dino Daily)

MAZE TALES reads and writes the same browser storage key as Dino Daily (`mazeDinoDaily.v1`). Both games live under `aiontrust.github.io`, so they share one origin and one set of points and one day streak.

| Action | Points |
| --- | --- |
| Today's daily tale (once a day) | 60 |
| Any other tale | 15, up to 3 a day |
| First award of the day, any game | streak bonus: 5 × streak days, capped at 50 |

Reading a shared link earns nothing. Points are not MAZE tokens, never touch the blockchain, and have no cash value.

Saved tales are kept under a separate key (`mazeTales.v1`), so they never touch Dino Daily's dino collection.

**Keep in sync:** if you change how points or the streak work in one game, change it in the other. Both use the same `award` logic and the same store shape (`points`, `streak`, `lastDay`, `done`, `collection`).

## Safety notes

- Everything a player types is shown as plain text, never as HTML.
- Share links carry the words in the link itself (`#s=<tale>&w=<words>`). Words from a link are cut to 24 characters, run through the filter, and shown as plain text.

## Adding a tale

Add an entry to `STORIES` in `index.html`:

```js
{id:'my-tale', title:'My Tale',
 blanks:['adjective','noun','verb ending in -ing'],
 text:'A {0} {1} went {2}.'}
```

Every blank number from 0 up must appear in the text at least once. The same number can appear more than once. Note that adding a tale changes which tale is picked as the daily tale.
