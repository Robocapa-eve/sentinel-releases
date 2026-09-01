# SENTINEL 0.3.0-alpha

**Release candidate notes · not yet publicly activated**

The current public Windows build remains **0.2.30-alpha** until the final installer is published, independently verified and the public `update-manifest.json` is advanced **last**.

## From tactical map to tactical-intelligence platform

`0.3.0-alpha` is the biggest architectural step in SENTINEL so far.

SENTINEL now combines the native Windows tactical client with a dedicated Live Relay, rolling Tactical Memory, reconciliation and recovery tooling, and the first two evidence-backed Tactical Intelligence Brain layers.

> **Live data tells SENTINEL what is happening now. Memory shows what has been happening. Intelligence turns those observations into explainable tactical context.**

The release also introduces the new SENTINEL brand identity across the Windows application and installer surfaces.

---

## What pilots receive in the Windows build

The Windows package carries forward the complete 0.2.30 Tactical Intelligence System and adopts the new SENTINEL identity for:

- application / executable branding
- startup presentation
- header and footer branding
- taskbar and tray iconography
- WebView / favicon surfaces
- installer branding
- optimized icon sizes for small Windows surfaces

Existing tactical features remain available, including:

- MAP INTEL profiles: `SOLO`, `SAFE`, `ROAM`, `ROUTE`, `SCOUT`, `CUSTOM`
- Tactical Feed Depth: `15J`, `25J`, `50J`
- Tactical Intelligence Feed
- Tactical Picture
- `KILL HEAT`
- live tactical map markers
- MAP FOCUS
- pinned System Tooltips
- SYSTEM VERLAUF
- Local Snapshot / Delta feedback

### Important truth boundary

The new Tactical Memory and Brain layers are already validated backend intelligence capabilities. They are **not yet presented as finished new full Brain panels inside the Windows UI**.

SENTINEL deliberately separates a proven data/truth model from future presentation work instead of advertising backend capability as a UI feature that does not yet exist.

---

# What changed behind SENTINEL

## Dedicated Live Relay

A dedicated production relay at `relay.sentinel-eve.de` now provides:

- sequential public R2Z2 / zKill ingestion
- normalized live-kill packets
- bounded live buffers
- secure WSS distribution
- reconnect / resume by source sequence
- snapshot / resync recovery
- explicit gap handling
- slow-client isolation
- source and pipeline telemetry

The current Windows client still treats **Direct R2Z2 as its authoritative live-event path**. Relay cutover remains a separate explicit decision.

## Rolling 90-day Tactical Memory

A PostgreSQL-backed Tactical Memory now retains a rolling **90-day UTC** window of recent public combat observations.

Observed context includes canonical kill identity, victim / attacker information, ships, weapons, items, organization IDs, provenance and chronology where available.

A much deeper archive was capacity-tested and intentionally rejected for the current deployment target. The bounded 90-day model keeps recent tactical behavior useful while keeping storage and backup costs predictable.

## Reconciliation and safe repair

Memory can now compare completed UTC days with public zKill history, identify demonstrated missing IDs and repair those gaps idempotently from public raw archives.

SENTINEL does **not** claim to possess every killmail in EVE. Public-source availability remains part of the truth model.

## Tactical Intelligence Brain 1A — Pilot behavior

Read-only derived intelligence can analyze observed pilot behavior such as:

- attacker ship usage
- weapon usage
- target preferences
- recurring co-attacker relationships
- historical loss-fit families
- sample count, recency and confidence

Truth boundaries are explicit: a historical loss fit is not a current fit, and recurring co-attackers are not automatically fleet members.

## Tactical Intelligence Brain 1B — Systems and organizations

The second intelligence layer adds recent activity profiles for:

- solar systems
- corporations
- alliances
- attacker / victim hull patterns
- UTC-hour activity distributions
- recurring co-attacking organizations
- evidence / confidence metadata

Route and roam reconstruction remain a separate future inference phase.

---

## Backup, recovery and security

The 0.3.0 engineering line also added:

- verified PostgreSQL backups
- SHA-256 and archive validation
- disposable restore drills
- daily local backup scheduling
- private PostgreSQL network boundaries
- separate read-only Intelligence DB access
- migration-timeout hardening
- narrow Gitleaks false-positive handling while real secret detection remains active

Production Tactical Memory storage remains on the existing project infrastructure rather than relying on paid GitHub storage products.

---

## Validation numbers

The current 0.3.0 development line has passed:

- **224 tests** in the combined Windows / relay repository suite
- **71 PostgreSQL-backed tests** in the Tactical Intelligence 1B production line
- Python compile validation
- JavaScript syntax validation
- Git whitespace validation
- Gitleaks secret scanning
- dependency audit
- Visual Smoke for UI-affecting work
- live HTTPS / TLS checks
- live R2Z2 ingestion checks
- WebSocket hello / snapshot / live / ping / resync validation
- Memory durability, reconciliation and 90-day retention checks
- backup health and disposable restore drills
- Tactical Intelligence production canaries

At one Tactical Intelligence 1B production checkpoint, bounded Memory contained roughly:

- **480k canonical kills**
- **2.0M attacker rows**
- **7.8M item rows**

These are operational snapshots, not product guarantees.

A bounded historical-repair canary also durably processed **13,962 public killmails** before the long-term storage model was selected.

---

## Windows release-path proof

A clean GitHub-hosted Windows runner successfully built and validated a disposable `SENTINEL-Setup-0.3.0-alpha.exe` candidate from tracked Git sources.

The rehearsal verified:

- 8 packaging / version regression tests
- frozen application identity
- embedded `0.3.0-alpha` VERSION
- new SENTINEL brand assets in the frozen and installed app
- Inno Setup compilation
- local update-manifest fields
- installer SHA-256 / manifest / sidecar agreement
- silent install
- installed executable / VERSION / brand presence
- silent uninstall

The rehearsal retained **no GitHub build artifact** and did **not** modify the public update manifest.

The dry-run hash was:

`85337c7f925cc93e0008be09b78df919a975ebcd86173fddd42ae55939e21d90`

That hash belongs only to the disposable rehearsal build. The final published installer receives and publishes its own independently verified SHA-256.

---

## Release trust

The final activation order is intentionally strict:

1. freeze the exact release candidate source
2. re-run the release gate on that exact state
3. build the final installer
4. verify installer identity, installation behavior and SHA-256
5. publish installer and release notes
6. independently verify the published asset
7. advance `update-manifest.json` to `0.3.0-alpha` **last**

Until that last step, installed clients continue to see **0.2.30-alpha** as the current public update target.

SENTINEL is an independent third-party application for EVE Online and is not affiliated with or endorsed by CCP Games.
