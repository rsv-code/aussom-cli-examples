# Package files for helloworld

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

Optional Debian package hook scripts run after install
and before removal. Empty by default. They MUST keep
their executable bit if you edit them on Windows.

## msi/wix-overrides/

Optional WiX template overrides for the Windows MSI
build. Leave empty unless you need to customize the
generated WiX XML.

## pkg/

Optional macOS .pkg / .dmg assets (background image,
custom welcome / conclusion text, etc.).

## gtk-native/macos and gtk-native/windows

REQUIRED when `installer.<plat>.bundle.gtk: true` for
macOS or Windows. Drop the GTK4 native libraries (`.dylib`
files for macOS, `.dll` files for Windows) here. APAC
copies the contents into the installer's `lib/` directory
so the bundled bindings can find them. Linux relies on the
user's system GTK4; no files needed there.

Typical sources:
- macOS:   `/opt/homebrew/lib/*.dylib` (Homebrew)
- Windows: `C:\msys64\mingw64\bin\*.dll` (MSYS2 mingw64)

## extra-licenses/

For every jar listed in `<plat>.bundle.extraJars`, drop
a matching `<jarname>.txt` file here containing that
jar's license text. APAC concatenates these into the
generated `THIRD_PARTY_LICENSES.txt` and fails the build
if any extra jar is missing its license file.
