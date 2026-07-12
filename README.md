# STZ Suite — Releases

**Public** distribution repository for STZ Suite.

This repository does **not** contain application source code. It hosts release artifacts and the official plugin catalog only.

Development source lives in a separate private repository.

## Contents

| Content | Location |
|---------|----------|
| Official plugin catalog | [`catalog/official-plugins.json`](./catalog/official-plugins.json) |
| Base installer (Windows) | [GitHub Releases](https://github.com/starzynhobr/stz-suite-releases/releases) — tag `stz-suite-base-v*` |
| Plugin packages (`.stz-plugin`) | [GitHub Releases](https://github.com/starzynhobr/stz-suite-releases/releases) — one tag per plugin |

## Base (desktop app)

The Base is an **empty shell**: no plugins bundled. Users install plugins on demand from **Settings → Plugins**.

| Field | Example |
|-------|---------|
| Tag | `stz-suite-base-v0.1.0` |
| Title | `STZ Suite 0.1.0` / `STZ Suite Base 0.1.0` |
| Assets | `STZ-Suite-Base-0.1.0-Setup.exe`, `STZ-Suite-Base-0.1.0-Setup.sha256.txt` |

Typical download URL:

```text
https://github.com/starzynhobr/stz-suite-releases/releases/download/stz-suite-base-v0.1.0/STZ-Suite-Base-0.1.0-Setup.exe
```

### Install notes

1. Download the Setup executable (and optionally the `.sha256.txt`).
2. Run the installer (per-user default: `%LocalAppData%\Programs\STZ Suite`).
3. Open **Settings → Plugins** to install official plugins from this catalog.
4. Optional: **Start with Windows** in Settings.

## Plugins

Each plugin version has **its own** GitHub Release (not one monolith with every plugin).

| Field | Example |
|-------|---------|
| Tag | `fetchora-v0.1.0` |
| Title | `Fetchora 0.1.0` |
| Asset | `Fetchora-0.1.0.stz-plugin` |

Asset filenames use the **brand** name:

```text
Fetchora-0.1.0.stz-plugin
Lumio-0.1.0.stz-plugin
Reperto-0.1.0.stz-plugin
…
```

Typical asset URL:

```text
https://github.com/starzynhobr/stz-suite-releases/releases/download/<tag>/<file>.stz-plugin
```

## How the app uses this repository

1. Downloads the catalog from `catalog/official-plugins.json` on `main`.
2. Each catalog entry declares `version`, `package_url`, and `sha256`.
3. **Install / Update** uses the catalog URL (it does **not** depend on GitHub `latest`).
4. An update is available when the installed version is lower than the catalog version.

Default catalog URL (stable path):

```text
https://raw.githubusercontent.com/starzynhobr/stz-suite-releases/refs/heads/main/catalog/official-plugins.json
```

## Security

- Prefer HTTPS URLs from this repository only.
- The app verifies plugin packages against the `sha256` declared in the catalog (when set).
- Base installer integrity: use the attached `.sha256.txt` on each Base release.
- Do not publish source code or secrets in this repository.

## Publishing workflow

### Plugin

1. Build the `.stz-plugin` in the private development repository.
2. Create a Release with tag `<brand-lowercase>-vX.Y.Z` and attach the asset.
3. Update `catalog/official-plugins.json` (`version`, `package_url`, `sha256`, `size_bytes`).
4. Commit and push the catalog to the `main` branch.

### Base

1. Build Base + Inno Setup in the private development repository.
2. Create a Release with tag `stz-suite-base-vX.Y.Z`.
3. Attach `STZ-Suite-Base-X.Y.Z-Setup.exe` and the matching `.sha256.txt`.
4. Add a short release description (install steps + notes).

## License / usage

Official binary and catalog distribution for STZ Suite.  
Application source code and product terms remain in the private development repository.
