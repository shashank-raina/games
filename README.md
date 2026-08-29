# Little Games

Small browser games. No apps, no accounts, no adverts — every game is a single HTML file you can open on a phone.

**[littlegames.uk](https://littlegames.uk)**

## What's here

### 🎲 Tile Score

A scorekeeper for tile-based word games. Type the word, tap the tiles that landed on premium squares, and it does the arithmetic while you argue about whether it's a real word.

**Play it:** [littlegames.uk/tilescore.html](https://littlegames.uk/tilescore.html)

- Adds up tile values as you type
- Tap a tile to mark it double letter, triple letter, or blank
- Word multipliers stack — 4×, 6×, 9× and beyond
- "Used all 7" adds the 50-point bonus, after multipliers where it belongs
- Checks words against Wiktionary
- Tracks turns and points-per-turn for each player
- Delete any turn when a challenge succeeds
- Saves finished games to a history list
- Scores persist, so you can close it mid-game

On iPhone, open it in Safari and use Share → Add to Home Screen to get it full-screen.

## Running it locally

Open the `.html` file in a browser. That's it.

Because iOS Safari can't open `file://` URLs, viewing on an iPhone needs a real URL — that's what the domain is for.

## Notes

Scores are stored in your browser's local storage. They survive closing the tab, but they're tied to that one browser on that one device — clearing website data clears the games too.

The word checker uses [freedictionaryapi.com](https://freedictionaryapi.com), built on Wiktionary data under CC BY-SA 4.0. It's a general English dictionary rather than a tournament word list, so expect the occasional false negative, and don't let it settle a real challenge on its own.

Tile Score is an independent scorekeeping tool. It isn't affiliated with, endorsed by, or connected to the makers of any board game, and it includes no board, tiles, or word list from one. SCRABBLE is a trademark of Hasbro in the US and Canada and of Mattel elsewhere.

## Adding a game

One self-contained HTML file per game in the repo root, plus a card on `index.html`. See [CLAUDE.md](CLAUDE.md) for the conventions.
