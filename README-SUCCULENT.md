## Succulent
##### By: Jonathan Vasquez (fearedbliss)
##### Build: 2021-01-10-1100

## Description

A **`Diablo II: 1.09b`** modification tailored for Single Player. Succulent
contains strong influence from **`Diablo I`**, and **`Diablo II (1.00 - 1.05b)`**.

## Quality of Life

- The game now has an Expanded Stash and Cube for both Classic and Expansion.
- The game now has an Infinite Stash for both Classic and Expansion. **`(Launch Game w/ Alpaca.exe)`**
- All new characters start out with the Horadric Cube.
- Fara (Act 2) and Ormus (Act 3) now sell more misc items.
- You can now open the Cow Level even if you kill the King.
- You can now open the Cow Level with just a Town Portal Book.
- Nihlathak's Portal no longer closes when you get the Halls of Pain WP and have
  already killed him.
- You can now make Hardcore characters without beating Softcore.
- The Battle.net button has been disabled for safety reasons.
- The ambiguity between the number "5" and "6" has been fixed.
- You can now run multiple clients of Diablo II.
- You are now able to quickly join LAN games.
- Fixed CPU usage bug in the Main Menu, Single Player, and LAN games.
- The introduction cinematics are now automatically skipped.
- The game will now work with the MPQ files included in the new Blizzard Installer.
- You no longer need the CD in order to play the game.
- The scrolling letters slowdown is now fixed for both **`DirectDraw`** and **`Glide`**.

## Gameplay Changes

#### Pre 1.07

- General monster immunities are no longer in the game. **`(Resistances Capped @ 90%)`**
  - Enchanted monsters can still be immune.
- Gambling rates are back to pre-LOD. **`(Uniques: 3%, Sets: 5%, Rares: 7%)`**
- Rares can now spawn with any affix.

#### Drop Balancing

- Improved Item and Rune Drop Rates.
- The Countess and Chests can now drop higher Runes on each difficulty. **`(Normal: Sol, NM: Ist, Hell: Zod)`**
- Perfect Gems now have a chance to drop.

## Notes

- The scrolling letters fix required the disabling of the **`fps`** command.

- If you experience extreme lag in the Main Menu, try using either
  **`cnc-ddraw`** or **`GlideWrapper`**, this should fix it. If for whatever
  reason that still doesn't work, you'll need to revert the CPU fix for the
  Main Menu specifically (You'll still have the fix for Single Player and LAN).
  Simply replace the **`D2Win.dll`** you are currently using with the one in
  the Singling **`1.09b`** Stock Directory.
  
- When using **`cnc-ddraw`**, you will also automatically gain the ability for
  the window to no longer minimize when you click out of it when using its
  window mode capabilities. Do not use Diablo II's **`-w`** flag since it will
  interfere with **`cnc-ddraw`**. You will also gain the minimize/maximize
  buttons, and the ability to dynamically resize the window as well.