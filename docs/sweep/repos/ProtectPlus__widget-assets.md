# ProtectPlus/widget-assets

| Field | Value |
|---|---|
| Status | light pass (batch F-11a) |
| Owning lane | F |
| Reviewed at | `db3eb8fc2f6afa65ca45b4122efdb74067284afa` on `main`, last content commit 2025-08-03 |
| Classification | Dependency (of the package-protection widget): static images only. Not a feature owner (D-004). |
| Feature (diagram group) | Package protection |
| Size | Tier S, reviewable LOC 0 (2 PNG files; no source) |
| Deploy target | none in the tree. No CI, Dockerfile, Cloud Build, Fly, Vercel, Shopify, or Pages config. The files sit on public `main` (Phase 0 §2.1 anonymous clone succeeded), so GitHub can serve them as raw files. That is file hosting, not an application deploy. |
| Entrypoints | none. No server, routes, functions, or scripts. |
| Duplicate / copy of | none in this repo. No other copy is named here. |
| Risk class (D-014) | low-risk (static images), confirmed. No auth, money, refunds, orders, or customer personal data. Does not cross the Opus line. |

## Plain summary (for the diagram, 8 words max, no jargon)

Holds pictures for the protection widget

## Chunks

| Chunk | Scope (dirs) | LOC | Status | Batch |
|---|---|---|---|---|
| whole repo | repo root at `db3eb8f` (`logo-icon.png`, `moreinfo.png`) and every commit in history | 0 | done | F-11a |

## Map (facts, with path:line)

Light pass (D-015). There is no source, so facts are file-level. The pinned content commit is `db3eb8f`.

- **Routes and handlers:** none. Tracked files at `db3eb8f` are only `logo-icon.png` (4,464 bytes, 290×361 RGBA PNG, no text chunks) and `moreinfo.png` (17,551 bytes, 512×512 RGBA PNG). History has four content commits, all on 2025-08-03 within about 21 minutes, all GitHub web uploads (`Add files via upload` / renames). `moreinfo.png` was added as `more info pplus asset.png` (`c0874d0`), renamed to `moreinfo` (`97a975a`), then to `moreinfo.png` (`a4e7f0e`). `logo-icon.png` was added in `db3eb8f`. One branch (`main`) and no tags before this sweep. No `.github/`, README, `package.json`, or deploy manifest has ever been committed (`git log --all --name-status`).
- **Authentication and tenant scoping** (where `shop`, `store_id` or `merchant_id` comes from): none. No identity, no token check, no tenant field. Nothing here accepts T-1 to T-38 or a staff session.
- **Env vars and secrets** (names only): no env vars. Secrets scan (tree and full history, every blob):
  - gitleaks 8.28.0, default rules, `detect --log-opts=--all --redact`: 0 leaks. Git mode reported 1 commit scanned because the image commits have no text additions the default rules keep (debug note: "smaller than expected due to commits with no additions").
  - The same gitleaks binary, `--no-git`, on a `.txt` copy of every blob in `git rev-list --objects --all` (both PNGs plus the two sweep docs): 0 leaks, 26,871 bytes scanned.
  - A separate read of every blob for AWS keys, Stripe `sk_live_` / `sk_test_`, SendGrid, GitHub tokens, Slack tokens, private-key blocks, MongoDB URIs, JWT-shaped strings, `password`/`secret`/`api_key`/`token` assignments, and Google API keys: 0 hits.
  - PNG chunks: `logo-icon.png` is `IHDR`, `bKGD`, `IDAT`, `IEND` only. `moreinfo.png` has one text chunk, `tEXt` keyword `Software`, value `www.inkscape.org` (25 bytes). No other `tEXt`, `zTXt`, `iTXt`, or `eXIf`.
  - Nothing to fingerprint. No value looks live or shared with another repo, because no secret is present.
- **Outbound calls** (service, env var, auth): none.
- **Inbound callers:** none recorded in this repo. Phase 0 §3.2 and §4.2 already classed it as static images. Whether a widget still requests `github.com/ProtectPlus/widget-assets` or `raw.githubusercontent.com/ProtectPlus/widget-assets` is a hand-off (batch F-11a). The original filename `more info pplus asset.png` is the only in-repo hint that these are Protect+ widget pictures.
- **Data stores and collections:** none.
- **Events and webhooks** (published and consumed): none.

What the files are: `logo-icon.png` is a blue-to-purple shield with a white plus. `moreinfo.png` is a blue circle with a white "i". Both are flat graphics, not photos, and neither contains readable customer data.

## Findings

None. The light pass found no Critical, High, Medium, or Low issue.

If these files are still fetched by a live widget, the only behaviour is a public download of the two images. There is no code path that could move money, read another merchant's data, or run code.

## Node (diagram)

| Repo short | Plain name | What it does | Role | Diagram group | In use? |
|---|---|---|---|---|---|
| widgetassets | Widget images | Holds pictures for the protection widget | Dependency | Package protection | unknown (no caller in this repo; last content commit 2025-08-03; no deploy config) |

## Connections (diagram; evidence required)

No connection row. This repo does not call any service, and it does not name a caller. A row would be a guess.

| From | To | Kind | Plain label | Evidence |
|---|---|---|---|---|

## MCP tool candidates

No tools. There is no endpoint. Plan v0's package-protection widget tools (`protection_get_widget_settings`, `protection_update_widget_content`) stay on the checkout and theme code, not on this image repo. Nothing here is worth borrowing: no schemas, no auth, no handlers, no tests.

| Tool | Segment | What it does | R/W | Risk | Phase | Endpoint (path:line) |
|---|---|---|---|---|---|---|

## Open threads

- Whether any live widget still loads these two files. This repo cannot see other repos. See the F-11a hand-off.
