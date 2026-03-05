# ShoreCalc Releases

[![Cleanup Dev Releases](https://github.com/kodevadam/ShoreCalc-Releases/actions/workflows/cleanup-dev-releases.yml/badge.svg)](https://github.com/kodevadam/ShoreCalc-Releases/actions/workflows/cleanup-dev-releases.yml)

Auto-published AppImage releases for [ShoreCalc (Beach Survey Template Generator)](https://github.com/kodevadam/Beach-Survey-Template-Generator-Web-App).

## Downloads

Check the [Releases](https://github.com/kodevadam/ShoreCalc-Releases/releases) page for the latest AppImage builds.

| Channel | Description | File |
|---------|-------------|------|
| **Stable** | Tagged releases (`v*`) | `ShoreCalc-x86_64.AppImage` |
| **Dev** | Built from every push to `main` | `ShoreCalc-dev-x86_64.AppImage` |

### Verify a download

Each release includes cosign signatures and SHA256 checksums:

```bash
# Check the checksum
sha256sum -c SHA256SUMS.txt

# Verify cosign signature (requires cosign)
cosign verify-blob \
  --signature ShoreCalc-x86_64.AppImage.sig \
  --certificate ShoreCalc-x86_64.AppImage.cert \
  --certificate-oidc-issuer https://token.actions.githubusercontent.com \
  ShoreCalc-x86_64.AppImage
```

## How it works

The [source repository](https://github.com/kodevadam/Beach-Survey-Template-Generator-Web-App) has two workflows:

- **Dev** — triggers on every push to `main`, builds an AppImage, signs it with cosign, and publishes a prerelease here.
- **Stable** — triggers on `v*` tags, builds a release AppImage, signs it, and publishes a full release here.

This repo has a cleanup workflow that automatically prunes old dev prereleases, keeping the 5 most recent.
