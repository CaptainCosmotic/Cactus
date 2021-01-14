# Renderers

## Included Renderer Versions

- **`cnc-ddraw - 1.3.9.0`**
- **`glidewrapper - 1.4e`**

## Recommendations

Due to some very annoying compatibility issues that occur in Diablo II's Glide
implementation for versions below **`1.14`** on Windows, such as the famous
**`scrolling letters slowdown`** and **`the silent crashing/hanging of the game upon exit`**,
(Read the bottom of this page for more information on these specific issues),
I recommend people to use **`cnc-ddraw`** for versions below **`1.14`**.

**`cnc-ddraw`** is more compatible and performs better on Windows, and has more
features than **`glidewrapper`**. Specifically the ability to dynamically
resize the resolution, set any custom window resolution, easily switch between
window mode and full screen via a hotkey, and upscale the game's textures to
look much better through the use of shaders, are just a few of the features it
has. Since **`cnc-ddraw`** is a **`DirectDraw`** implementation, any Glide
related errors will no longer affect you.

For versions **`1.14+`**, Blizzard has improved compatibility of the game
with Windows (which improved the Glide compatibility as a consequence), and has
removed **`DirectDraw`** support. Due to this, **`glidewrapper`** should be use.

### For people that never ran a version older than 1.14 on their machine

Blizzard implemented some fundamental changes with how video configuration
works in **`1.14+`**, and this will cause issues if you are going back down
and your system is missing these settings.

If you have never played a version older than **`1.14`** on your computer,
that means you would have never had ran **`D2VidTst.exe`** and thus you won't
have the required registry settings for the game to work in older versions.
Please follow the instructions for the **`cnc-ddraw`** section to set
**`DirectDraw`** as your default renderer which would in turn allow
**`cnc-ddraw`** to be picked up by the game and used. Once this is done, all
your versions (except **`1.14+`**) should automatically work with this
renderer. You can use the **`-3dfx`** flag for just your **`1.14+`** versions
to use **`Glide`** just for them. With this setup, your system can use either
renderer properly on the same system.

If this isn't set up properly, you will experience crashes or weird behaviors
such as an **`Access Violation`**, etc.

## **`cnc-ddraw`**

In order to use **`cnc-ddraw`**, you will need to make sure that your Diablo II
video renderer is set to use **`DirectDraw`**. Diablo II versions starting at
**`1.14`** no longer support DirectDraw and thus you will need to use
**`glidewrapper`** instead.

The required files for **`cnc-ddraw`** are already included as part of the
Cactus Base Installation, specifically **`ddraw.dll`**, **`ddraw.ini`**,
and the **`Shaders`** directory. Thus, all of these files will be located in
the root of your Diablo II directory.

Once you start customizing **`cnc-ddraw`**, you will see your game-specific
customizations at the bottom of **`ddraw.ini`**.

### Setting your video mode to DirectDraw

### Configuration

To make sure we are starting from a clean slate, we will delete the entire
**`VideoConfig`** key located in the registry and we will set the renderer
to DirectDraw directly.

1. Open up the **`Registry Editor`** by running **`regedit`**.
1. Delete the **`HKEY_CURRENT_USER\Software\Blizzard Entertainment\Diablo II\VideoConfig`**
   key if it exists.
1. Create a new key called **`VideoConfig`** under the **`Diablo II`** key. 
1. Create a new **`REG_DWORD`** value called **`Render`** under the
   **`VideoConfig`** key. This should already be set to **`0`** for you.

That's it! Try the **`Quick Testing`** instructions below to see if the dll is
being used and working.

#### Quick Testing

Try running Diablo II (Make sure you don't have any other settings
that can conflict with the renderer such as using **`-3dfx`**, **`-opengl`**,
or **`-w`** flags) and see if the game starts up. If the game starts up, see if
you can easily switch between full screen and window mode by pressing
**`[Alt] + [Enter]`**. If you can't switch between these modes, then the dll is
not being used to render the game. If it doesn't, you will need to continue
inspecting things yourself.

### Wine (Tested on Linux)

If you are running Diablo II on Linux, you will want to make sure that your
**`WINEPREFIX`** is overriding the **`ddraw`** dll so that it can pick up the
custom **`ddraw.dll`** in the Diablo II root directory.

For example, on my system I'm using a specific prefix that just contains
Diablo II, located at **`${HOME}/prefix/diablo_2`**. If you are using the
default prefix, then you don't need to include the **`WINEPREFIX`** part for any
of the following commands. If you are, adjust the prefix location to point to
the one on your machine.

1. Open up the wine configuration by typing:
 
    ```
    $ WINEPREFIX="${HOME}/prefix/diablo_2" winecfg
    ```

1. Set the **`Windows Version`** at the bottom to **`Windows XP`** so that your
   **`Mouse 3`** button works properly.
1. Click the **`Libraries`** tab at the top.
1. In the **`New override for library`** textbox, Write in **`ddraw`** (With no
   extension) and click **`Add`**.
1. You will receive a warning saying: **`Changing the load order of this
   library is not recommended. Are you sure you want to do this?`**.
   Click **`Yes`**.
1. You should see a new element in the list below that says:
   **`ddraw (native, builtin)`**. Click **`Ok`**.

Once this is done, you can run the steps in the **`Configuration`** section
above. You can also run the **`regedit`** command in Wine as well by doing:

```
$ WINEPREFIX="${HOME}/prefix/diablo_2" regedit
```

### Tweaking **`cnc-ddraw`**

You can tweak **`ddraw.ini`** to change any settings such as the window
resolution (not the internal resolution), renderer, shaders, etc.

**`cnc-ddraw`** will cache some settings for different games you use with it at
the bottom of the file. Make sure to check that section when making changes,
or you may notice that some changes are not reflected in game.

#### Tweaking Shaders (The Game Look)

Cactus contains a carefully curated set of shaders from the upstream repository.
I'm using the **`jinc2-sharper`** shader as the default since it is an overall
good looking shader that still very closely resembles the original game.
You can play around with the included shaders and settings until you find a
combination that works for you.

You can get more shaders from
[libretro's repository](https://github.com/libretro/glsl-shaders), however only
**`.glsl`** will work, if at all. **`cnc-ddraw`** states that they've only
implemented **`preliminary shader support`**.

### Hotkeys and Other

Since **`cnc-ddraw`** already has support to switch between full screen and
window mode for the game, you need to make sure you don't use the **`-w`** flag
since it's no longer necessary.

The following hotkeys are also available for you in game:

- **`[Alt] + [Enter]`** - Switches between Full Screen and Window Mode.
- **`[Ctrl] + [Tab]`** OR **`[Right Alt] + [Right Ctrl]`** - Unlocks the cursor.

If you happen to also play Diablo 1, you can use **`cnc-ddraw`** for it as well!

### Screenshots

The following screenshots were all taken with **`cnc-ddraw`** using its
**`opengl`** renderer and using the provided **`sabr-v3.0`** shader.
These are all in full screen running at a resolution of **`1920x1200 (16:10)`**
while the game is running patch **`1.05b`**. The game has an internal resolution
of **`800x600`** in the main menu and **`640x480`** in game.

![](https://i.imgur.com/CMMDbeP.png)
![](https://i.imgur.com/zceV1Ae.png)
![](https://i.imgur.com/NMXBBpu.png)
![](https://i.imgur.com/Uzzts4B.png)
![](https://i.imgur.com/KbvqnGF.png)
![](https://i.imgur.com/zM8aTWI.png)
![](https://i.imgur.com/APQGUMB.png)
  
## **`glidewrapper`**

**`glidewrapper`** is also included in the Cactus Base Installation and thus
will be located in the root of your Diablo II directory after installation.
The particular files that belong to it are **`glide3x.dll`** and
**`glide-init.exe`**.

You can tweak any Glide settings by running **`glide-init.exe`**, and you will
need to use the **`-3dfx`** flag in order to run the game with Glide. You may
also need to run **`D2VidTst.exe`** if you are running in full screen for
versions before **`1.14`** (Follow the instructions for setting up DirectDraw
for **`cnc-ddraw`** above, but set the **`Render`** to **`3`** instead). If you
are running in window mode, you will want to not only use the **`-w`** flag so
that Diablo II runs in window mode, but you will also want to enable the
**`window-mode`** option in the Glide settings as well or you will get weird
behaviors.

### Fixing the hanging Diablo II process in Windows 10 (Build 1903+) upon exit

If you are using **`Windows 10 - Build 1903 (or greater)`**, you will want to
disable the **`GL_ARB_fragment_program`** checkbox in the **`Extensions`** tab
in the Glide settings. If not, your Diablo II game will crash and hang
when you exit the game. You will not get a message about this. Thus you will
silently have a zombie process running in the background that will prevent you
from switching versions with Cactus.

I've also noticed that if you are using Glide, and you don't have Singling's
Multiple Instances Fix (Thus the normal one instance of the game in Vanilla),
you will get a message saying only one instance is allowed, but you will now
have a zombie process running for that failed/second instance. This does not
happen with **`cnc-ddraw`**.

## General Problems

### Scrolling Letters

- Both **`Glide`** and **`DirectDraw`** have this problem, however the problem
  is experienced differently on both implementations. For **`Glide`**, it is
  much worse and more noticable. It seems it will happen not only when you
  start Diablo II, but it will also happen when you switch games as well
  (start a game, save and exit, and make a new game). For **`DirectDraw`**,
  this seems to only happen when you start Diablo II, but not in between games.
  Singling includes the Scrolling Letters Fix for both implementations.