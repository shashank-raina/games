# CLAUDE.md

Guidance for Claude Code working in this repository.

## What this repo is

A collection of small browser games and game tools, served as static files from GitHub Pages. Currently one game: `tilescore.html`, a word-game scorekeeper.

## Hard constraints

These are the point of the repo, not preferences:

- **One self-contained HTML file per game.** Markup, CSS and JavaScript in the same file. No separate stylesheets or scripts.
- **No build step.** No bundler, no transpiler, no `package.json`, no `node_modules`. Editing the file and refreshing the browser is the whole workflow.
- **No frameworks or libraries.** Vanilla JavaScript. If something needs React, it doesn't belong here.
- **No network dependency for core function.** A game must be fully playable offline. Network calls are allowed only for optional extras, and must fail gracefully with a visible message — never a broken state or a silent hang.

Web fonts loaded from Google Fonts are the one accepted exception, and every font stack must name a real local fallback.

`index.html` is the site landing page listing every game. Adding a game means adding a card to it — same felt-and-tiles styling, no framework.

## Target environment

iOS Safari on a phone is the primary target — these get played at a table, one-handed. Desktop is secondary.

- Everything must work at 375px wide
- Tap targets no smaller than 40px
- Include the `apple-mobile-web-app-*` meta tags so Add to Home Screen works
- Test the full-screen home-screen mode, not just the browser tab

## Persistence

Use `localStorage`, wrapped in `try`/`catch` — Private Browsing throws on write, and the game must keep working when it does.

Namespace keys per game: `tilescore:game`, `tilescore:dict`. Never bare keys like `game` or `state`.

Store the whole game state as one JSON blob under one key rather than spreading it across many. When loading an older save, guard for fields that didn't exist yet:

```js
if (!state.archive) state.archive = [];
```

Never break someone's saved game with a schema change.

## Code style

- ES5-flavoured vanilla JS: `var`, `function`, no arrow functions or template literals. It reads consistently with what's there and sidesteps any old-browser surprises.
- Wrap each game's script in an IIFE
- Build DOM with `createElement` and `textContent`. Never `innerHTML` with interpolated values.
- Keep rendering in named `renderX()` functions that read from a single `state` object, with one `renderAll()` that calls them
- CSS custom properties at `:root` for the palette; no hardcoded hex values scattered through rules
- Respect `prefers-reduced-motion` and keep visible `:focus-visible` outlines

## Game rules matter

These tools get used to settle arguments, so the rules logic has to be right.

For Tile Score specifically: the 50-point bonus is added *after* word multipliers, never multiplied. Blanks score zero but still take the word multiplier. Word multipliers stack multiplicatively — two double-word squares is 4×.

If a rule varies between rule sets (challenge penalties differ between North American and Collins play, for instance), don't have the app assert one. Leave it to the table.

## Testing

There's no test suite. Before committing:

1. Open the file in a browser and play a full round
2. Check the arithmetic by hand against a known score
3. Reload to confirm state restored correctly
4. Narrow the window to phone width
5. Run the script through `node --check` to catch syntax errors

## Deployment

GitHub Pages serves the repo root from `main`. Pushing to `main` publishes. Filenames are public URLs, so renaming a file breaks anyone's home-screen shortcut — avoid it.

## Writing

UI copy in sentence case, plain verbs, no exclamation marks. Buttons say what happens when tapped: "Finish game", not "Submit". Empty states point at the next action rather than apologising.
