# aussom-cli-examples

A public collection of example applications for the [Aussom CLI](https://aussom-lang.com/docsProduct?product=aussom), demonstrating how to build and run command-line apps with the Aussom language and runtime.

Each directory at the root of this repo is a self-contained example you can run, inspect, and adapt. The current set includes:

- **hello-world** — a minimal `.aus` application with a `HelloWorld` class and `main()` entry point. Prints a greeting and dumps `sys.getSysInfo()` to standard output.
- **hello-world-script** — the same program written as an `.auss` script, with a shebang line so it can be executed directly without a class wrapper.

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
