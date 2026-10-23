# Color Sort Bottles (Android)

A color-sorting bottle puzzle game written in Kotlin with no third-party dependencies.
Everything is drawn on a custom `View` (Canvas), so there are no layout files or assets.

## How to play
- Tap a bottle to pick it up, then tap another bottle to pour into it.
- You can pour onto an empty bottle or onto a bottle whose top color matches.
- All the matching layers on top move together, as many as fit.
- Fill every bottle with a single color to finish the level.
- **Undo** reverts the last pour, **Restart** resets the level, **+ Bottle** adds one extra empty bottle (once per level).
- Levels get harder (more colors) and progress is saved automatically.
- Every generated level is checked by a solver, so it is always winnable.

## Build and run
1. Install Android Studio (Koala or newer).
2. Choose **Open** and select this folder. Let Gradle sync finish.
3. Plug in a phone with USB debugging, or start an emulator, then press **Run**.

Command line (needs the Android SDK, `ANDROID_HOME` set, and Gradle 8.9 or newer):

    gradle assembleDebug
    # APK: app/build/outputs/apk/debug/app-debug.apk

Android Studio creates the Gradle wrapper for you when it opens the project.

## Project layout
- `GameLogic.kt`: pure game rules, level generator and solver (no Android imports).
- `GameView.kt`: rendering, pour animation, touch input, level progress.
- `MainActivity.kt`: hosts the view.

## Tweaking
- Bottle capacity and number of empty bottles: `LevelGenerator` in `GameLogic.kt`.
- Colors per level: `LevelGenerator.colorsFor`.
- Palette: the `palette` array in `GameView.kt`.
