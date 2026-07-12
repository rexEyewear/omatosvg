# 🐱 Run Kitty Run!

A fun, family-style 2D chase mini-game: the naughty cat has stolen something
important, and you must chase it through the house, jump over obstacles,
collect treats and power-ups, and catch that kitty before the timer runs out!

## Play it

Open `index.html` in any modern browser — no build step, no dependencies,
everything lives in one file. Works with mouse, touch, or keyboard.

## Controls

| Input | Action |
|---|---|
| Tap / click / Space / ↑ | Jump |
| Tap again mid-air | Double jump |

You auto-run — everything else happens automatically.

## Features

- **Auto-run chase gameplay** — close the gap on the cat before time runs out.
  The catch meter (top right) shows how close you are.
- **Two playable kids** — *Dash* (⚡ runs faster) and *Hop* (🦘 jumps higher).
- **Three levels** — Living Room, Kitchen (with rolling fruit!), and Garden,
  each with its own obstacles, scenery, and a faster kitty.
- **Collectibles & power-ups**
  - 🍪 Cat treats — +10 points
  - 🐭 Toy mice — +25 points
  - 🐟 Fish — speed boost
  - 🥛 Milk bowl — makes the kitty drowsy and slow
  - 🐾 Golden paw — +5 seconds on the timer
- **Funny face system** — the kids and the cat change expressions as things
  happen: shocked when you bump into obstacles, the cat laughs at you,
  gets scared when you're close, and looks guilty when caught.
- **📸 Real faces (optional)** — upload photos of your kids and your cat from
  the start screen and they appear on the cartoon bodies, with emoji reaction
  bubbles for expressions. Photos are stored only in your browser's
  localStorage — nothing is uploaded anywhere.
- **Score & best score** — treats plus a time bonus per level; your best
  total is remembered on the device.

## Level guide

1. **Living Room** — toy blocks, cushions, and toy cars. 45 seconds.
2. **Kitchen** — bowls, chairs, and rolling oranges. 50 seconds, faster cat.
3. **Garden** — flower pots and the hose. 55 seconds — the kitty is heading
   for the fence gap with the house key!

## Tech

Plain HTML5 canvas + vanilla JavaScript in a single `index.html`.
Cartoon characters, backgrounds, and expressions are all drawn procedurally,
so there are no image assets to load (except your own face photos).
