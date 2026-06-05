# aussom-cli-examples

A public collection of example applications for the [Aussom CLI](https://aussom-lang.com/docsProduct?product=aussom), demonstrating how to build and run command-line apps with the Aussom language and runtime.

Each directory at the root of this repo is a self-contained example you can run, inspect, and adapt. The current set includes:

- **hello-world** — a minimal `.aus` application with a `HelloWorld` class and `main()` entry point. Prints a greeting and dumps `sys.getSysInfo()` to standard output.
- **hello-world-script** — the same program written as an `.auss` script, with a shebang line so it can be executed directly without a class wrapper.
- **hello-javafx** — a minimal JavaFX desktop app that opens a window and displays a `Label`, demonstrating Aussom's `fx.*` wrapper layer.
- **hello-gtk** — a minimal GTK desktop app that opens a window and displays a label, demonstrating Aussom's `gtk.*` bindings driven through the `panama` foreign-function interface.

## FXGL applications

The following examples are Aussom clones of the Java FXGL games written by Dr. Almas Baimagambetov, available at [github.com/AlmasB/FXGLGames](https://github.com/AlmasB/FXGLGames). They use the FXGL game engine through Aussom's `fxgl.*` wrappers and are meant both as larger-scale demos of the CLI and as ports that exercise the FXGL wrapper API end-to-end. The original games and the FXGL engine are Copyright (c) 2015 AlmasB and used under the MIT License.

- **cannon** — the player shoots from a cannon toward the mouse cursor and tries to land the projectile between two barriers on a hidden ground strip, scoring 1000 points per hit.
- **shooter** — red enemies spawn at random positions in the upper half of the screen; left-clicking fires a blue bullet straight up from the cursor's X. Bullets remove the enemy they hit and free a spawn slot.
- **bomberman** — the player moves on a 15x15 grid with WASD and presses F to drop bombs that destroy brick tiles within a blast radius. Destroyed bricks have a 50% chance of dropping a powerup that increases the player's max concurrent bomb count.
- **tower-defense** — the player picks a level, places towers on tower bases, and defends a path of waypoints from waves of enemies walking along it. Towers auto-target the nearest enemy and fire bullets that apply damage and on-hit effects.

## Running locally

1. Install the Aussom CLI so that the `aussom` binary is on your `PATH`.
2. Run a class-style example by passing the file to `aussom`:
   ```bash
   aussom hello-world/helloworld.aus
   ```
3. Run a script-style example either through `aussom -s` or directly (the shebang invokes it for you):
   ```bash
   aussom -s hello-world-script/helloworld.auss
   # or
   ./hello-world-script/helloworld.auss
   ```

---

Copyright 2026 Austin Lehman

Licensed under the Apache License, Version 2.0. See [LICENSE](LICENSE) for details.
