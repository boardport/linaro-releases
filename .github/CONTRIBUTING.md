# Contributing to BoardPort — Linaro Releases

Thank you for your interest in contributing to **BoardPort — Linaro Releases**!
This repository provides a reliable, permanent archival mirror of legacy Linaro releases, board firmware, and partition layouts.

---

## How to Contribute

### 1. Requesting New Board Releases

- Before requesting, check existing [GitHub Releases](https://github.com/boardport/linaro-releases/releases) and [Issues](https://github.com/boardport/linaro-releases/issues).
- Use the **[Release Request Template](./ISSUE_TEMPLATE/request_release.md)**.
- If you have Wayback Machine links or original SHA256 checksums, please include them in your request.

### 2. Reporting Corrupted Files or Hash Mismatches

- If an asset in GitHub Releases fails checksum verification, use the **[Broken Release Template](./ISSUE_TEMPLATE/broken_release.md)**.
- Include the exact release tag, file name, downloaded file hash, and expected hash.

### 3. Submitting Pull Requests

- Pull requests are welcome for updating board catalog tables, documentation, or links.
- Fork the repository and create a feature/fix branch from `main`.
- Maintain mirrored bilingual documentation (`*.md` and `*_RU.md`).
- Follow the Conventional Commits specification (e.g., `feat:`, `fix:`, `docs:`, `chore:`).
- Verify formatting locally with `npx markdownlint-cli2`.

---

## Release Publication Standards

When publishing new releases to GitHub Releases:

1. **Storage Isolation**: Downloads and hashing must be conducted strictly within `tmp/` (never committed to Git).
2. **Asset Bundle Requirements**:
   - Firmware image / archive files.
   - Dedicated `.sha256` checksum file for each binary asset.
   - `manifest.json` describing metadata, source URLs, build date, and components.
3. **Release Notes**:
   - Provide clear bilingual descriptions containing both `[RU]` and `[EN]` sections.
   - Include a markdown table with file names, sizes, and SHA256 hashes.
4. **Tag Naming**:
   - Use flat semantic naming: `<board>-<os-or-type>-<version>` (e.g., `db410c-debian-18.01`, `db410c-rescue-17.09`).

---

## Contact & Support

If you have questions, reach out to **BoardPort Team <boardport@proton.me>** or open an issue on
[GitHub Issues](https://github.com/boardport/linaro-releases/issues).
