# games

Small browser games and game tools. No build step, no dependencies, no accounts — every game is a single HTML file you can open on a phone.

## What's here

### 🎲 Score Pad

A Scrabble scorekeeper for the table. Type the word, tap the tiles that landed on premium squares, and it does the arithmetic while you argue about whether it's a real word.

**Play it:** https://shashank-raina.github.io/games/scrabble-scorepad.html

- Adds up tile values as you type
- Tap a tile to mark it double letter, triple letter, or blank
- Word multipliers stack — 4×, 6×, 9× and beyond
- "Used all 7" adds the 50-point bonus, after multipliers where it belongs
- Checks words against an English dictionary
- Tracks turns and points-per-turn for each player
- Delete any turn when a challenge succeeds
- Saves finished games to a history list
- Scores persist, so you can close it mid-game

Works on any modern browser. On iPhone, open it in Safari and use Share → Add to Home Screen to get it full-screen.

## Running it locally

Open the `.html` file in a browser. That's it.

Because iOS Safari can't open `file://` URLs, viewing on an iPhone needs a real URL — GitHub Pages is doing that job here.

## Notes

Scores are stored in your browser's local storage. They survive closing the tab, but they're tied to that one browser on that one device — clearing website data clears the games too.

The word checker uses [dictionaryapi.dev](https://dictionaryapi.dev), a general English dictionary rather than the official Scrabble word list. Expect the occasional false negative on legal inflections, and don't let it settle a real challenge on its own.

Scrabble is a trademark of Hasbro in the US and Canada and of Mattel elsewhere. This is an unaffiliated scorekeeping tool — no board, no tiles, no word list from the game itself.

## Adding a game

One self-contained HTML file per game, dropped in the repo root. See [CLAUDE.md](CLAUDE.md) for the conventions.
