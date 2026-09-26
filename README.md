# HNH-Client-Public

Compiled binaries for the Haven & Hearth client (Gifciak custom version). This package contains **only compiled `.jar` and supporting files** — no Java source code is included.

## What's Included

- `hafen.jar` — Main client runtime
- `Play.bat` / `Play_Linux.sh` — Launch scripts for Windows/Unix environments
- `launcher.hl` / `hafen.hl` — Helper scripts
- `haven-config.properties` — Client configuration
- All resource jars (jogl, lwjgl, gluegen, steamworks, sqlite, etc.)
- Custom client resources under `res/customclient/`
- Game data files (hitboxes.db, static_data.db, etc.)

## How to Run

**Windows:**
```batch
Play.bat
```

**Linux/Unix:**
```bash
Play_Linux.sh
```

**Manual Java execution:**
```bash
java -jar hafen.jar
```

## How to Get Updates

Game updates are distributed through this updater tool:

1. Download `HNHClientUpdater.jar` from the [GitHub Releases](https://github.com/Gifciak/HNH-Client-Public/releases) section
2. Place your local client binaries in a folder (e.g., `C:\Users\YourName\HNHClient`)
3. Run the updater:
   ```bash
   java -jar HNHClientUpdater.jar
   ```
4. Select your install folder and click "Check and Update"

The updater will:
- Download new/changed files from this repository's `Release/` folder
- Verify SHA-256 hashes for integrity
- Create backups of old files before replacement
- Update your local `manifest.json`

## Important Notes

- **Backup retention**: If you have custom modifications, increase the "Backups to keep" setting to preserve more history
- **Stale file removal**: The "Remove files that are no longer in the remote manifest" option should be used cautiously — it may delete custom `.res` files if they're no longer distributed
- **Line endings**: Files in the `Release/` folder are marked with `.gitattributes` to preserve byte-exact content (including line endings) for SHA-256 verification

## Repository Structure

```
Release/
  ├── manifest.json          # File manifest with paths, sizes, and SHA-256 hashes
  ├── hafen.jar              # Main client JAR
  ├── Play.bat               # Windows launch script
  ├── launcher.hl            # Launcher helper
  ├── ...                    # All other distributable files
```

The updater fetches files from:
```
https://raw.githubusercontent.com/Gifciak/HNH-Client-Public/main/Release/{path}
```
