# Package files for hellogtk

This directory holds assets `apac -ib` uses when building
the platform installers for this application.

## icons/

Drop the application icons here. Recommended sizes:

- `app.png`  - 1024x1024 PNG for Linux (referenced from
               `installer.linux.icon`).
- `app.ico`  - multi-resolution Windows ICO (referenced
               from `installer.windows.icon`).
- `app.icns` - macOS ICNS bundle (referenced from
               `installer.macos.icon`).

Generators: ImageMagick (`convert app.png -define icon:auto-resize app.ico`),
`png2icns`, or any of the online icon converters.

## license.txt

The license text shown by the installer's EULA screen.
Defaults to a copy of the project's LICENSE.txt when one
exists at scaffold time. Edit freely.

## deb/postinst, deb/prerm

Debian package maintainer scripts. `postinst` runs after
install, `prerm` runs before removal. APAC wires both into
the produced `.deb` via `jpackage --resource-dir`. The
scaffolder lays down a no-op `exit 0` skeleton with the
executable bit set — edit as needed.

Filenames jpackage looks up in this directory are literal
and case-sensitive: `preinst`, `postinst`, `prerm`,
`postrm`, `control`, `copyright`. Any file present REPLACES
jpackage's default for that hook (the docs at
https://docs.oracle.com/en/java/javase/23/jpackage/override-jpackage-resources.html
describe what each default does — paste relevant pieces
into your override if you need them).

Scripts MUST keep their executable bit if you edit them
on Windows or copy them through tools that strip perms.

## msi/wix-overrides/

Optional WiX template overrides for the Windows MSI build.
Wired into jpackage via `--resource-dir` when populated.

## pkg/  and  dmg/

Optional macOS installer assets (.pkg uses `pkg/`, .dmg
uses `dmg/`). Background images, custom welcome /
conclusion text, etc. Each dir is wired into the
matching jpackage build via `--resource-dir` when
populated.

## lib/

Platform-specific native libraries (.so / .dll / .dylib)
your app loads at runtime. APAC copies whatever is in
this directory verbatim into the installer's `lib/`
directory. APAC does NOT pick libraries for you — drop
the right ones for the platform you're building before
running `apac -ib`. A typical multi-platform workflow
has a per-platform CI step that stages the matching
libs into this dir before invoking the build.

## extra-licenses/

For every jar listed in `<plat>.bundle.extraJars`, drop
a matching `<jarname>.txt` file here containing that
jar's license text. APAC concatenates these into the
generated `THIRD_PARTY_LICENSES.txt` and fails the build
if any extra jar is missing its license file.
