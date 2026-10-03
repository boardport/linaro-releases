# Project Passport and Operational Guidelines for AI Agents: Linaro Releases

> **Project:** BoardPort — Linaro Releases  
> **Organization:** [BoardPort](https://github.com/boardport) | **Repository:** `boardport/linaro-releases`  
> **Mission:** Safe archival mirror for legacy Linaro board releases  
> **Target Storage:** GitHub Releases (`gh` CLI) | **License:** [MIT](./LICENSE)  

---

## 1. AI Context Organization

The root [`AGENTS.md`](./AGENTS.md) and [`AGENTS_RU.md`](./AGENTS_RU.md) files serve as the authoritative baseline guidelines for all AI assistants.
Developers directly control, isolate, and customize secondary context for their specific tools:

- **Specialized Directories (`.(gemini|claude|cursor|continue|qwen|etc)/`):** Individual context for specific AI assistants
  (prompts, skills, reports, session dumps). These directories are isolated and excluded from git indexing (`.gitignore`).
- **Context Routing Files:** Navigation and indexing within specialized directories are organized via
  `.{ai}/README(_RU).md` or `.{ai}/AGENTS(_RU).md`. Specialized instructions complement the root guidelines and take precedence within their own context.
- **`.aiignore` File:** Defines resources strictly excluded from background indexing and scanning
  (archives, raw firmware images, temporary caches). Agents may only access these files upon explicit user instruction.
- **Staging Directory (`tmp/`):** All intermediate downloads, archive unpacking, and hashing must happen strictly inside `tmp/`.

---

## 2. Release & Storage Architecture

- **No Heavy Binaries in Git:** All large images, rescue archives, bootloaders, and firmware are strictly stored in **GitHub Releases**.
- **Release Asset Bundle:** Every published release in GitHub Releases must include:
  1. The target binary archives / image files.
  2. A dedicated `.sha256` checksum file for each archive (or `SHA256SUMS`).
  3. A machine-readable `manifest.json` describing metadata, source URLs, build dates, and components.
  4. Dual-block release notes formatted in both Russian and English (`[RU]` / `[EN]`).
- **Tagging Strategy:** Flat semantic tags per board and OS release (e.g., `db410c-debian-18.01`, `db410c-rescue-17.09`). There is no global
  repository versioning.
- **Publishing Tool:** Releases are published manually or via AI assistants using the GitHub CLI (`gh release create ...`).

---

## 3. Markdown Documentation Standards

- **Formatting Rules:** Syntax and formatting constraints are governed by `.editorconfig` and `.markdownlint-cli2.jsonc`.
- **Line Length:** Maximum 150 characters per line (`MD013`).
- **Mandatory Lint Command:** Run `npx markdownlint-cli2` (must return `0 issues in 0 files` before completing work).
- **Mirrored Bilingualism:** All public user documentation is maintained in parallel (`*.md` in English and `*_RU.md` in Russian).
- **Clarity of Presentation:** Documentation must provide clear, concise board tables and download pointers.

---

## 4. Git and GitHub Standards (`.github/`)

- Organizational policies, issue templates, PR descriptions, and CI workflows reside in [`.github/`](./.github/).
- Commit message standards follow the Conventional Commits specification.
- **Git Commits Rule:** Creating Git commits is allowed **only upon direct user confirmation**.
