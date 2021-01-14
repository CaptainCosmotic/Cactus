## Singling
##### By: Jonathan Vasquez (fearedbliss)
##### Build: 2020-12-22-1544

## Description

A collection of non-gameplay modifications and fixes in order to improve the
Vanilla Diablo II Single Player & LAN Experience.

## Supported Versions

- **`1.00`**
- **`1.05b`**
- **`1.07`**
- **`1.08`**
- **`1.09b`**
- **`1.13d`**
- **`1.14d`**

## Features

- You can now run multiple clients of Diablo II.
- You are now able to quickly join LAN games.
- Fixed CPU usage bug in Main Menu, Single Player, and LAN games.
- The Battle.net button has been disabled for safety reasons.
- The introduction cinematics are now automatically skipped.

- **`[1.00-1.09b]`** You no longer need the CD in order to play the game.
- **`[1.00-1.09b]`** You can now make Hardcore characters without beating Softcore.

- **`[1.00-1.13d]`** The scrolling letters slowdown is now fixed for both
  **`DirectDraw`** and **`Glide`**.

- **`[1.08/1.13d-1.14d]`** Ladder Runewords are now enabled on Single Player.

- **`[1.08/1.13d]`** The game will now work with the MPQ files included in the
  new Blizzard Installer.

## Notes

- The scrolling letters fix required the disabling of the **`/fps`** command.

- When using **`cnc-ddraw`**, you will also automatically gain the ability for
  the window to no longer minimize when you click out of it when using its
  window mode capabilities. Do not use Diablo II's **`-w`** flag since it will
  interfere with **`cnc-ddraw`**. You will also gain the minimize/maximize
  buttons, and the ability to dynamically resize the window as well.

- Blizzard removed **`DirectDraw`** support starting in version **`1.14`**.
  Thus, you can only use **`GlideWrapper`** as an alternative renderer,
  not **`cnc-ddraw`**.

- If you experience extreme lag in the Main Menu for versions **`1.00-1.09b`**,
  try using either **`cnc-ddraw`** or **`GlideWrapper`**, this should fix it.
  If for whatever reason that still doesn't work, you'll need to revert the CPU
  fix for the Main Menu specifically (You'll still have the fix for Single
  Player and LAN). Simply replace the **`D2Win.dll`** you are currently using
  with the one in the Singling Stock Directory for the affected version.

## Patch Rationale

#### Patch 1.00

This patch was selected due to it simply being the first version of Diablo II
released. There are some things possible in this version that were quickly
patched out, however, there are also many instabilities in the game that may
result in crashes or even the character becoming corrupted.

#### Patch 1.05b

This patch was picked because it is the most stable and balanced version
of the game before **`Lord of Destruction`**. It was also picked over
**`1.06`** since the main reason **`1.06`** was released was to implement
anti-duping code. Due to the way item generation works in these patches,
you can legitimately find items that have the same fingerprint, and the
anti-duping code would delete those items.

#### Patch 1.07

This patch was selected because it is the first version of
**`Lord of Destruction`** that was released and was the first massive change to
Diablo II. Due to this, it contains a lot of features, behaviors, and item
generation combinations that were immediately patched out in patches **`1.08`**
and **`1.09`**. It also contains some bugs that are fun to play with such as the
Rejuvenation Potion Bug or Mana Per Kill (MPK) rings. Overall, **`1.07`** at
this stage is still basically a beta patch and this was why this patch was never
played on the realms (immediately patched to **`1.08`**) and was only available
on Single Player from the Expansion CD upon release.

#### Patch 1.08

This patch was selected because it is a more stable version of **`1.07`**
but still contains a lot of bugs, the famous **`1.08`** unique items, and a lot
of crafting recipes that were disabled in **`1.09`**. This patch is sometimes
considered the best patch to craft in since it has more activated recipes and
sometimes higher ranges than **`1.07`** and **`1.09`**, however some people
argue that **`1.07`** is better for crafting.

#### Patch 1.09b

This patch was picked over **`1.09d`** because it is the most stable version of
Diablo II before the massive changes implemented in 1.10, and also because it
contains **`players 64`** and working CtC. **`1.09d`** has broken CtC which
means that you will see the animation of your CtC effect, but it actually won't
do anything.

#### Patch 1.13d

This patch was selected because it is the last patch released by Blizzard
that still retains the original program architecture, which contained all
code in their own separate dlls. **`Alpaca`** is optimized and only supports
this version.

#### Patch 1.14d

This patch was selected because it is the latest version of the game (at the
time of writing) and contains compatibility fixes to run on modern versions
of Windows. **`DirectDraw`** was also removed in this version, so you will
only be able to use **`GlideWrapper`** and not **`cnc-ddraw`**. Besides that,
this version is identical to **`1.13d`**.