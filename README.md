# STZ Suite — Releases

**Public** distribution repository for [STZ Suite](https://github.com/starzynhobr/stz-suite).

This repository does **not** contain application source code. It hosts release artifacts and the official plugin catalog only.

## Contents

| Content | Location |
|---------|----------|
| Official plugin catalog | `catalog/official-plugins.json` |
| Plugin packages (`.stz-plugin`) | [GitHub Releases](https://github.com/starzynhobr/stz-suite-releases/releases) |
| (Optional) Base / installer | Releases |

## How the app uses this repository

1. The app downloads the catalog from `catalog/official-plugins.json`.
2. Each catalog entry declares `version`, `package_url`, and `sha256`.
3. **Install / Update** uses the catalog URL (it does not depend on GitHub `latest`).
4. An update is available when the installed version is lower than the catalog version.

## Release format (plugins)

Suggested tags (one plugin per version):

```text
fetchora-v0.1.0
lumio-v0.1.0
```

Or a grouped release:

```text
plugins-v0.1.0
```

Asset filenames use the plugin brand name, for example:

```text
Fetchora-0.1.0.stz-plugin
Lumio-0.1.0.stz-plugin
```

Typical asset URL:

```text
https://github.com/starzynhobr/stz-suite-releases/releases/download/<tag>/<file>.stz-plugin
```

## Security

- Prefer HTTPS URLs from this repository only.
- The app verifies packages against the `sha256` declared in the catalog (when set).
- Do not publish source code or secrets in this repository.

## Publishing workflow

1. Build the `.stz-plugin` in the private development repository.
2. Create or update a GitHub Release and attach the asset.
3. Update `catalog/official-plugins.json` (`version`, `package_url`, `sha256`, `size_bytes`).
4. Commit and push the catalog to the `main` branch.

## License / usage

Official binary and catalog distribution for STZ Suite.  
Application source code and product terms remain in the private development repository.
