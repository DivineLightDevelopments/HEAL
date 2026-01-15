# token-template READ ME

**Token Repository Template**

This repository is a template for Divine Light Developments token projects. It standardizes structure, transparency files, icon/metadata handling, GitHub Pages publishing, and basic validation. Use this template to create a new token repo.

**What you get**

Consistent folders: icons/, metadata/, transparency/, ledger/, governance/, services/, policy/, checksums/, registry/, ipfs/

GitHub Pages site from index.md (deployed via Actions)

Hash/metadata validation workflow (fails PRs if metadata is invalid or hashes missing)

Issue/PR templates (governance proposals, change requests, bug reports)

**Quick start (for a new token repo created from this template)**

Rename placeholders inside files with real values:

index.md

transparency/FACTS.md — Symbol, Subunit, Decimals, Supply, Features

transparency/URI.md — ipfs://<CID> and exact SHA-256 of the served JSON

transparency/ADDRESSES.md — Treasury, Gift Vault

transparency/TX_ISSUANCE.md — issuance tx + explorer link

metadata/token_metadata_FINAL.json — final JSON bytes (must match the posted hash)

Upload icons to icons/:

token_icon_solid_256.png (registry size)

token_icon_solid_512.png

token_icon_solid_1024.png

token_icon_solid.svg

Update checksums (checksums/SHA256SUMS.txt):

Add SHA-256 lines for the metadata JSON and each distributed icon.

Enable Pages: Settings → Pages → Build & deployment: GitHub Actions
The site will publish at:
https://<ORG>.github.io/<REPO>/

Protect main: Settings → Branches → Add rule (main)

Require PR

Require 1 approval

Require status checks → Validate metadata & hashes

Include administrators

**Repository layout**
.
├─ index.md                         # Site home (Transparency landing)
├─ checksums/
│  ├─ SHA256SUMS.txt                # SHA-256 entries for icons + metadata
│  └─ HOWTO_VERIFY.md               # CLI commands to verify hashes
├─ icons/
│  ├─ token_icon_solid.svg
│  ├─ token_icon_solid_1024.png
│  ├─ token_icon_solid_512.png
│  └─ token_icon_solid_256.png
├─ metadata/
│  ├─ token_metadata_FINAL.json     # Canonical metadata (exact bytes matter)
│  └─ METADATA.md                   # URI + hash notes
├─ transparency/
│  ├─ FACTS.md                      # Symbol, decimals, supply, features
│  ├─ ADDRESSES.md                  # Treasury & Gift Vault
│  ├─ URI.md                        # URI + SHA-256 + verify steps
│  ├─ TX_ISSUANCE.md                # Issuance tx + explorer link
│  ├─ CIRCULATION.md                # Circulation meter + policy
│  ├─ CHANGES.md                    # Change log (hashes, reasons)
│  └─ status/                       # Weekly notes
├─ ledger/
│  ├─ gift_ledger_template.csv
│  └─ README.md
├─ governance/
│  ├─ GOVERNANCE_LITE.md
│  ├─ PROPOSAL_TEMPLATE.md
│  └─ POLLS/
├─ services/
│  ├─ MODULE_01_TEMPLATE.md
│  └─ ROADMAP_90D.md
├─ policy/
│  ├─ TERMS.md
│  └─ PRIVACY.md
├─ ipfs/
│  ├─ CIDs.txt                      # Content-addresses for pinned files
│  └─ GATEWAY_CHECK.md              # Curl + hash recheck examples
├─ registry/
│  ├─ COREUM_ASSETS_SNIPPET.json    # JSON snippet for token registry PR
│  └─ PR_NOTES.md                   # Notes/links for registry PR(s)
└─ .github/
   ├─ ISSUE_TEMPLATE/               # Issue templates (governance/change/bug)
   ├─ PULL_REQUEST_TEMPLATE.md
   └─ workflows/
      ├─ validate-metadata.yml      # Fails if metadata invalid or hashes missing
      └─ build-pages.yml            # Publishes GitHub Pages

**Canonical facts to fill (per token)**

Symbol: <SYMBOL>

Subunit: u<symbol> (e.g., uheal)

Decimals: 6

Supply: 100,000,000 (or token-specific)

Features at launch: Burning ON; others OFF (or token-specific)

Denom: factory/<issuer_address>/u<symbol>

URI: ipfs://<CID>

URI SHA-256: <64-char hex>

Treasury: <address>

Gift Vault: <address>

Issuance tx: <hash + explorer link>

Keep these in index.md and transparency/*.md as the public source of truth.

**Hash discipline**

After any edit to metadata/token_metadata_FINAL.json or any icon file:

Recompute SHA-256 locally (see checksums/HOWTO_VERIFY.md).

Update the exact line in checksums/SHA256SUMS.txt.

If the metadata JSON changed, update transparency/URI.md and on-chain URI hash (if applicable).

Append a record to transparency/CHANGES.md (date, file, old→new hash, reason).

The Validate metadata & hashes workflow blocks merges if hashes are missing or JSON is invalid.

**GitHub Pages**

Pages publishes the repo as a static site using build-pages.yml.

The site renders Markdown from the repo root (index.md) and links to subpages.

Never embed third-party scripts; keep it static and verifiable.

**Governance (signal-only by default)**

Use Issues with the templates in .github/ISSUE_TEMPLATE/.

Publish a weekly poll and attach a CSV of raw counts in governance/POLLS/.

Document mechanics and cadence in governance/GOVERNANCE_LITE.md.

**Token registry (Coreum)**

Add a 256×256 PNG to the registry at: files/<symbol>/images/<symbol>.png

Append your JSON to mainnet/assets.json (see registry/COREUM_ASSETS_SNIPPET.json).

Track links and outcome in registry/PR_NOTES.md.

**Security**

No private keys or secrets in this repo.

Publish official addresses once in transparency/ADDRESSES.md and on the site; never DM links.

Protect main with branch rules; require the validation check to pass.

License / reuse

This template is provided for reuse across Divine Light Developments token projects. If publishing publicly for others, add a license of your choice (e.g., MIT) at the repo root as LICENSE.

**Support notes (for maintainers)**

If Pages fails: open Actions → deploy-pages job logs.

If validation fails: fix JSON syntax or update hashes in checksums/SHA256SUMS.txt.

If raw links 404: confirm branch is main and path/filename match; use the Raw button URL.

Owner: Divine Light Developments Ltd.
Template purpose: per-token transparency, assets, and metadata with verifiable integrity.
