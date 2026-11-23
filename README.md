# My Chessboard

A single-file chess game for students. Open `index.html`, or host it with GitHub Pages.

## Features
- **Play the computer** at 10 levels, from Beginner to Grandmaster.
- **Adaptive difficulty:**
  - The level goes up after a win (+2 for a clean win with few hints) and down after a loss.
  - During a game, the computer eases off when it's far ahead and pushes back when the student is crushing it.
- **Hints in two steps:** the first tap shows which piece to look at. The second tap shows the move and explains why it's good.
- **Coach:** grades each move (Great, Good, Okay, Mistake). After a big mistake it pauses, shows the threat with a red arrow, and offers to take the move back.
- **Two-device play** (teacher and student) through a room code, using Firebase Realtime Database.
- Saves the game and level on the device. Works by tap or keyboard (arrows, Enter, H for a hint, U to take back, N for a new game).

## Two-device setup
1. In `index.html`, find `var FIREBASE_CONFIG = null;` and replace `null` with your Firebase web app config (including `databaseURL`).
2. Make sure your Realtime Database rules allow reads and writes under `chessRooms`. For example:

```json
{ "rules": { "chessRooms": { ".read": true, ".write": true } } }
```

Merge that into your existing rules rather than replacing them.

## Two-device use
1. On one device, tap **📱 Two devices**, then **Create game**.
2. On the other device, enter the 4-character code.
3. Colors swap on each rematch. Take back undoes the last move on both devices.
