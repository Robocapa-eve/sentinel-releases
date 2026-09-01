# SENTINEL // DEVELOPMENT LOG

> **Tactical Intelligence for EVE Online**  
> Public development chronicle · Windows x64 · Alpha channel

SENTINEL is being built as a focused tactical companion for pilots who want a clearer picture of what is happening around them in New Eden: live intelligence, threat context, system awareness and map-based situational analysis.

This document makes the **development journey public** while the application source code remains private. It records meaningful user-facing, reliability, security and engineering milestones without publishing sensitive implementation details.

---

## CURRENT SIGNAL

| | Status |
|---|---|
| **Latest public build** | `0.2.30-alpha` |
| **Current development line** | `0.3.0-alpha` |
| **Current development track** | Live Relay · Rolling Tactical Memory · Tactical Intelligence Brain |
| **Platform** | Windows x64 |
| **Release channel** | Alpha / pre-release |
| **Source code** | Private |
| **Public development history** | This document |

> [!IMPORTANT]
> `0.3.0-alpha` is currently a **development line**, not a published Windows installer. The public update manifest intentionally remains on `0.2.30-alpha` until a real 0.3.0 installer has been built, verified and published.

### Signal legend

- 🛰️ **INTEL** — live intelligence, threat context and monitoring
- 🗺️ **MAP** — New Eden navigation, system awareness and tactical visualization
- 🧠 **MEMORY** — bounded tactical history and explainable behavioral context
- 🔔 **ALERT** — notifications, sounds and attention management
- 🪟 **WINDOWS** — native desktop integration and installer behavior
- 🔐 **SECURITY** — authentication, service hardening and supply-chain safety
- ⚙️ **ENGINEERING** — architecture, reliability and development infrastructure
- 🧪 **VALIDATION** — automated tests and quality gates

---

# ⚡ ENGINEERING SPRINT // 31 AUG → 1 SEP 2026

Two calendar days changed the shape of SENTINEL.

The sprint started with a public Windows tactical-intelligence release and ended with a production-backed intelligence architecture: dedicated live transport, durable bounded Memory, completeness repair, backup/restore operations, two derived Intelligence Brain layers and a self-maintaining Git workflow.

### The progression

**1 · Public tactical system shipped**  
`0.2.30-alpha` delivered MAP INTEL profiles, Tactical Feed Depth, Tactical Intelligence Feed, KILL HEAT, Tactical Picture, pinned System Tooltips, SYSTEM VERLAUF and the current public map/feed experience.

**2 · Dedicated Live Relay built**  
A production HTTPS/WSS relay was added with sequential public R2Z2 ingestion, bounded queues, reconnect/resume, snapshot/resync, explicit gap handling and slow-client isolation.

**3 · SENTINEL gained durable Tactical Memory**  
PostgreSQL 16 now stores recent canonical kill observations with victim, attacker, item, organization and source-provenance context.

**4 · Memory learned to verify itself**  
Completed UTC days can be reconciled against public zKill history. Demonstrated missing IDs can be repaired idempotently, with durable scheduler state across restarts.

**5 · Historical repair was proven in production**  
A bounded one-day historical canary durably processed **13,962 public killmails** before the project committed to its long-term storage policy.

**6 · Full-history ambition was replaced with an operational decision**  
Capacity and backup footprint were measured instead of guessed. SENTINEL deliberately chose a rolling **90-day UTC Memory** so recent behavior remains useful without turning the project into an unbounded archive.

**7 · Recovery became part of the platform**  
Verified PostgreSQL backups, SHA-256/archive validation, disposable restore drills, daily local scheduling, retention guards and operator-safe ownership were added.

**8 · Tactical Intelligence Brain 1A came online**  
The read-only intelligence layer can derive observed pilot ship/weapon usage, target preferences, recurring co-attacker relationships and historical loss-fit families with evidence, recency and confidence.

**9 · Tactical Intelligence Brain 1B expanded the model**  
The Brain now profiles recent behavior for systems, corporations and alliances, including attacker/victim hull patterns, UTC activity distributions and recurring co-attacking organizations.

**10 · The repository itself was hardened**  
`main` became canonical development truth, `infra/live-relay-v1` became the controlled promotion line, obsolete rollout branches/workflows were removed, expensive CI was path-scoped and a repository-local Branch Integrity Guard was added.

### Hard validation numbers

The engineering sprint closed with verifiable gates rather than a version-number claim:

- **224 tests passed** in the combined Windows/relay repository suite on Windows / Python 3.12
- **71 PostgreSQL-backed tests passed** in the Tactical Intelligence 1B production line
- Python compile validation
- frontend JavaScript syntax validation
- Git whitespace validation
- Gitleaks secret scanning
- dependency audit
- Visual Smoke coverage for UI-affecting changes
- live HTTPS/TLS and R2Z2 ingestion checks
- WebSocket hello/snapshot/live/ping/resync validation
- Memory durability, reconciliation, retention and restore validation

At the Tactical Intelligence 1B production checkpoint, the bounded Memory contained roughly:

- **480k canonical kills**
- **2.0M attacker rows**
- **7.8M item rows**

These values are operational snapshots, not fixed product promises.

### Engineering philosophy proven during the sprint

SENTINEL does not call every correlation a fact. Historical loss fits are not presented as current fits, recurring co-attackers are not automatically labeled fleet members, and route/roam reconstruction remains a separate future inference phase with explicit confidence.

Likewise, the project did not advance the public updater just because the backend became `0.3.0-alpha`. The downloadable Windows client remains `0.2.30-alpha` until a real 0.3.0 installer is built, tested, published, verified and the update manifest is advanced **last**.

---

# 0.3.0-alpha // LIVE RELAY · ROLLING MEMORY · TACTICAL INTELLIGENCE BRAIN

**Development milestone · 1 September 2026**  
**Not yet a public Windows release**

This milestone moves SENTINEL beyond a tactical live-map client and establishes the backend foundation for a **living tactical-intelligence system**.

The core principle is simple:

> **Live data tells SENTINEL what is happening now. Memory tells it what has been happening. Intelligence turns those observations into explainable context.**

## 🛰️ Dedicated SENTINEL Live Relay

SENTINEL now operates a dedicated production relay at `relay.sentinel-eve.de`.

The relay can:

- consume sequential public R2Z2/zKill observations
- normalize live-kill packets
- maintain bounded live buffers
- distribute events through secure WebSockets
- resume clients by source sequence
- provide snapshot/resync recovery
- isolate slow clients through bounded backpressure handling
- expose source/pipeline health and latency telemetry

The current Windows application still treats **Direct R2Z2 as the authoritative live source**. Relay cutover is not automatic and remains a separate explicit future decision.

## 🧠 Rolling 90-day Tactical Memory

A PostgreSQL-backed Memory layer now records recent public combat observations for tactical analysis.

Current production policy:

- rolling **90-day UTC horizon**
- canonical identity by killmail ID
- victim and attacker observations
- attacker ship/weapon context
- victim item / historical loss-fit data
- corporation/alliance context where available
- source provenance and chronology
- automatic bounded retention

A much deeper public-history archive was capacity-tested during development. SENTINEL intentionally chose the bounded 90-day model instead: it provides recent behavioral context while keeping storage and operating cost predictable.

## 🔄 Reconciliation & safe repair

Memory is not treated as infallible just because data was received once.

The new reconciliation system can:

- compare completed UTC days with public zKill history
- track daily totals and ID/hash observations
- identify explicit missing kill IDs
- retrieve public raw daily archives only when a real gap is demonstrated
- merge repairs idempotently
- preserve scheduler state across restart

SENTINEL does **not** claim to possess every killmail in EVE. Public-source limits remain part of the truth model.

## 🧠 Tactical Intelligence Brain 1A — Pilot behavior

The first derived intelligence layer can analyze recent observed pilot behavior:

- attacker ship usage
- weapon usage
- target preferences
- recurring co-attacker relationships
- historical loss-fit families
- sample counts, recency and confidence

SENTINEL deliberately avoids fake certainty:

- a historical loss fit is **not** a current fit
- recurring co-attackers are **not automatically fleet members**
- observations and inferences remain distinguishable

## 🧠 Tactical Intelligence Brain 1B — Systems & organizations

The second layer expands from individual pilots to locations and organizations:

- solar-system activity profiles
- corporation activity profiles
- alliance activity profiles
- top observed attackers and organizations
- attacker/victim hull patterns
- UTC-hour activity distributions
- attacker-count context
- recurring co-attacking corporation/alliance relationships
- evidence/confidence metadata

Roam and route reconstruction are intentionally **not** part of 1B. Movement inference will be developed as its own explicit-confidence layer.

## 🛡️ Backup, recovery and zero-cost operation

The Memory platform now includes:

- verified PostgreSQL backups
- SHA-256 validation
- archive validation
- disposable restore drills
- daily local backup scheduling
- production recovery documentation

SENTINEL also adopted a **GitHub zero-cost policy**: production database storage is not designed around paid GitHub Artifacts, Packages or Codespaces. Durable tactical data stays on the existing project infrastructure.

## 🔐 Reliability & security hardening

Recent engineering work also includes:

- separate long-running schema-migration timeout while normal DB operations remain tightly bounded
- production recovery of a queued Memory batch after a real migration-timeout incident
- read-only Tactical Intelligence database access
- private PostgreSQL network placement
- narrow Gitleaks false-positive handling while real secret detection remains active

## ⚙️ Repository & CI hardening

The development repository now follows a deliberately narrow operating model:

- `main` is canonical development truth
- `infra/live-relay-v1` is the controlled production-promotion branch
- approved promotions keep both commit-identical
- historical feature/hotfix/rollout branches were audited and removed
- one-shot rollout workflows were retired or made manual-only
- Visual/Memory/soak CI is path-scoped to relevant changes
- Security remains active on pull requests, weekly schedule and manual execution
- a Branch Integrity Guard restores unauthorized direct `main` pushes and divergent `infra` pushes
- safely merged same-repository PR branches clean themselves up automatically unless they received post-merge work

## 🧪 Validation

The current development line has passed:

- **224-test combined Windows/relay repository suite**
- **71 PostgreSQL-backed Tactical Intelligence 1B tests**
- Python compile validation
- frontend JavaScript syntax validation
- Docker Compose validation
- backup health and disposable restore drills
- live HTTPS/TLS health
- live R2Z2 ingestion
- durable Memory-write validation
- WebSocket hello/snapshot/live/ping/resync validation
- 90-day retention health
- reconciliation health
- Tactical Intelligence production canaries

At the latest deployment gate the bounded Memory contained roughly **480k canonical kills**, **2.0M attacker rows** and **7.8M item rows**. These are operational snapshots, not fixed product promises.

## What pilots see today vs. what is being built

The public Windows build remains **0.2.30-alpha** and already includes the Tactical Intelligence System, MAP INTEL profiles, KILL HEAT, System Tooltips and related map improvements.

The new 0.3.0 Memory/Brain products are currently **backend/internal intelligence capabilities**. Their Windows UI integration comes after the data and truth model is proven.

---

# 0.2.30-alpha // TACTICAL INTELLIGENCE SYSTEM

**Public pre-release · 31 August 2026**

0.2.30-alpha was the first major expansion of SENTINEL's Tactical Intelligence System while preserving predictable SOLO behavior.

### For pilots

- 🛰️ MAP INTEL profiles: **SOLO, SAFE, ROAM, ROUTE, SCOUT and CUSTOM**.
- 📡 Tactical Feed Depth: **15J, 25J and 50J**.
- 🧠 Advanced Tactical Intelligence Feed.
- 📊 Tactical Picture activity trends.
- 🔥 First **KILL HEAT** overlay.
- 🗺️ Real-system live tactical markers and improved MAP FOCUS.
- 📌 Click-pinned System Tooltips with protected hover behavior.
- 🕒 **SYSTEM VERLAUF** recent system history.
- 🧹 Hardened feed clearing across tactical surfaces.
- 👥 Faster Local Snapshot / Delta feedback.
- 🧭 Improved map-label stability during pan/zoom.

### Validation & release delivery

- ✅ SENTINEL CI
- ✅ SENTINEL Security
- ✅ SENTINEL Visual Smoke
- ✅ Windows Python 3.12 regression suite: **133 passed**
- ✅ Final Windows installer SHA-256 verification
- ✅ Public release/update-manifest activation

[View the 0.2.30-alpha release](https://github.com/Robocapa-eve/sentinel-releases/releases/tag/v0.2.30-alpha)

---

# 0.2.29-alpha // VERIFIED UPDATE DELIVERY

**Public pre-release · 28 August 2026**

- Added in-app update discovery.
- Added explicit one-click update flow.
- Added installer filename and metadata validation.
- Added SHA-256 verification before execution.
- Added clean application shutdown / installer hand-off / restart.
- Verified the real `0.2.28 → 0.2.29-alpha` update path.

[View the 0.2.29-alpha release](https://github.com/Robocapa-eve/sentinel-releases/releases/tag/v0.2.29-alpha)

---

# 0.2.28-alpha // UPDATE DISCOVERY

- Added public release discovery through `Robocapa-eve/sentinel-releases`.
- Added startup, periodic and manual update checks.
- Added current/update-available/channel-error states.
- Added installed/latest version display.
- Added update-manifest validation.

---

# 0.2.27-alpha // TACTICAL MONITORING

- Added continuous New Eden deep zoom and semantic detail.
- Separated map camera focus from tactical Monitoring.
- Added AUTO · MAIN and manual monitoring origins.
- Unified tactical distance/relevance around the active Monitoring origin.
- Added functional System Tooltip actions.
- Added native Windows tactical alerts.
- Hardened visible-feed clearing and internal event separation.

---

# 0.2.26-alpha // NATIVE WINDOWS APPLICATION

- Added the native Windows application shell and WebView2 interface.
- Added system tray/background operation.
- Added rotating production logs.
- Added Windows installer infrastructure.
- Added SHA-256/update-manifest generation.
- Moved the local service to dedicated port `18765`.

---

## Release trust

A public version becomes active for installed clients only after its real Windows installer exists, has been verified and the public `update-manifest.json` is advanced **last**.

SENTINEL is an independent third-party application for EVE Online and is not affiliated with or endorsed by CCP Games.
