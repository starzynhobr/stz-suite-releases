# Publishing STZ Suite releases

This document records the maintenance contract for the public distribution repository. It is intended for release operators, not end users.

## Repository contents

| Content                 | Location                                                                                                             |
| ----------------------- | -------------------------------------------------------------------------------------------------------------------- |
| Official plugin catalog | [`catalog/official-plugins.json`](./catalog/official-plugins.json)                                                   |
| App update metadata     | [`catalog/app-update.json`](./catalog/app-update.json)                                                               |
| Base installers         | [GitHub Releases](https://github.com/starzynhobr/stz-suite-releases/releases) with tags matching `stz-suite-base-v*` |
| Plugin packages         | GitHub Releases with one tag per plugin                                                                              |

Development source, build workflows, and provenance tags live in the private source repository. Do not publish source code, secrets, temporary build outputs, or unrelated artifacts here.

## Base release contract

- Tag: `stz-suite-base-vX.Y.Z`
- Title: `STZ Suite Base X.Y.Z`
- Installer: `STZ-Suite-Base-X.Y.Z-Setup.exe`
- Checksum: `STZ-Suite-Base-X.Y.Z-Setup.sha256.txt`
- Default install location: `%LocalAppData%\Programs\STZ Suite`

The Base is an empty shell. Official plugins are installed on demand from **Settings → Plugins**.

## Plugin release contract

- Tag: `<plugin-id>-vX.Y.Z`
- Title: `<Brand> X.Y.Z`
- Package: `<Brand>-X.Y.Z.stz-plugin`

Each catalog entry declares the published version, package URL, SHA-256, and size. Install and update use the URL declared in the catalog; they do not depend on GitHub's `latest` release.

Stable catalog URL:

```text
https://raw.githubusercontent.com/starzynhobr/stz-suite-releases/refs/heads/main/catalog/official-plugins.json
```

## Publishing sequence

### Plugin

1. Build and validate the `.stz-plugin` in the private source repository.
2. Publish the release as a prerelease.
3. Download the uploaded asset and reconcile SHA-256 and size.
4. Promote the release to stable.
5. Update `catalog/official-plugins.json` with the final URL, hash, size, and version.
6. Run final catalog and installation validation.

### Base

1. Build and validate the Base and Inno Setup installer in the private source repository.
2. Publish the release as a prerelease with the installer and checksum file.
3. Download the uploaded installer and reconcile SHA-256 and size.
4. Confirm update metadata references the final asset.
5. Promote the release to stable/Latest.
6. Verify a clean install and update path.

Publishing releases, tags, catalog changes, or replacing assets requires explicit authorization.
