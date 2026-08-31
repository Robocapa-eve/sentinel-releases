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
| **Current development track** | Tactical Intelligence, Security & Release Validation |
| **Platform** | Windows x64 |
| **Release channel** | Alpha / pre-release |
| **Source code** | Private |
| **Public development history** | This document |

### Signal legend

- 🛰️ **INTEL** — live intelligence, threat context and monitoring
- 🗺️ **MAP** — New Eden navigation, system awareness and tactical visualization
- 🔔 **ALERT** — notifications, sounds and attention management
- 🪟 **WINDOWS** — native desktop integration and installer behavior
- 🔐 **SECURITY** — authentication, local service hardening and supply-chain safety
- ⚙️ **ENGINEERING** — architecture, reliability and development infrastructure
- 🧪 **VALIDATION** — automated tests and quality gates

---

# 0.2.30-alpha // TACTICAL INTELLIGENCE SYSTEM

**Public pre-release · 31 August 2026**

This release is the first major expansion of SENTINEL's **Tactical Intelligence System**. It broadens the operational picture across New Eden while deliberately keeping immediate warning ranges, native Windows audio and the familiar SOLO workflow predictable.

### For pilots

- 🛰️ Added MAP INTEL profiles: **SOLO, SAFE, ROAM, ROUTE, SCOUT and CUSTOM**.
- 📡 Added Tactical Feed Depth options for **15J, 25J and 50J** strategic/tactical context.
- 🧠 Added the advanced **Tactical Intelligence Feed** with system, jump distance, age, source, ISK context and zKill access where available.
- 📊 Added **Tactical Picture** activity bands and trend context such as `RISING`, `STABLE` and `COOLING`.
- 🔥 Added the first tactical overlay: **KILL HEAT**.
- 🗺️ Live tactical events remain attached to their real New Eden systems and can stay visible at broad map scopes.
- 🗺️ MAP FOCUS now shows the concrete focused solar system instead of only the focus mode.
- 📌 System Tooltips now support **single-click pinning**, protected hover behavior, outside-click dismissal and `Escape` dismissal.
- 🕒 Added **SYSTEM VERLAUF** for recent tactical history of the selected solar system directly inside the System Tooltip.
- 📐 System Tooltips remain inside the map viewport and use internal scrolling when necessary.
- 🧹 Feed clearing is hardened across classic feed, tactical feed, tactical summary and live map markers.
- 👥 Local Scan now shows immediate Local Snapshot / Delta feedback separately from slower public ESI/zKill enrichment.
- 🧭 System labels remain more stable while panning and zooming through dense map areas.

### SOLO remains predictable

SOLO continues to use the classic SENTINEL Kill Range, Intel Range, native Windows audio and classic Live Intelligence Feed behavior.

Returning to SOLO explicitly restores Monitoring to **`AUTO · MAIN`** and the current MAIN system. A true SENTINEL process start also returns to the predictable SOLO baseline, while tray hide/show does not repeatedly reset the active session.

### Tactical context without wider danger alerts

Advanced MAP INTEL profiles can retain wider tactical context through Tactical Feed Depth without silently widening classic Kill/Intel warning ranges or native Windows audio ranges.

This means a pilot can maintain a broad tactical picture while keeping immediate danger alerts focused on the smaller range selected for local warning behavior.

### Map truth and interaction

- The active visible tactical feed is treated as the source of truth for live map event-marker visibility.
- Multiple same-system events are grouped visually instead of stacking uncontrolled markers.
- Marker and pulse lifetimes remain independently controlled by their existing settings.
- Tactical feed rows expand without automatically moving or re-centering the map.
- **SHOW ON MAP / AUF KARTE** remains the deliberate navigation action.
- New events do not force camera movement.

### System Tooltip interaction

System Tooltips now support a more deliberate two-stage interaction model:

- **Hover** — temporary preview.
- **Single click** — pins the tooltip to the selected system.

A pinned tooltip remains open when the pointer leaves, cannot be stolen by neighboring hover events, switches when another system is clicked and closes by clicking outside or pressing `Escape`. Double-click remains the deliberate map-focus action.

### Security, reliability & usability work included in this build

- 🔐 Strengthened the boundary around SENTINEL's local Windows service and browser-originated requests.
- 🔐 Hardened EVE SSO callback handling and local WebSocket protections.
- 🔐 Added automated full-history secret scanning and dependency vulnerability auditing.
- 🔐 Moved the affected `cryptography` dependency line to the patched 50.x series and revalidated the application.
- 🔔 Improved reliability of native Windows tactical alert playback on Python 3.12.
- 🪟 Added persistent **100 / 110 / 120% HUD scaling** for the side intelligence panels while leaving Tactical Map rendering independent.
- ⚙️ Added additional repository exclusions for credentials, tokens, private keys, certificates and local environment material.

### Validation

0.2.30-alpha passed the release gates before public activation:

- ✅ **SENTINEL CI**
- ✅ **SENTINEL Security**
- ✅ **SENTINEL Visual Smoke**
- ✅ Windows Python 3.12 regression suite: **133 passed**
- ✅ Python source compilation validation
- ✅ Frontend JavaScript syntax validation
- ✅ Git whitespace/error validation
- ✅ Chromium 1920×1080 real-backend visual validation
- ✅ Live Windows installation and startup validation
- ✅ SOLO + `AUTO · MAIN` startup validation
- ✅ Click-pinned System Tooltip interaction validation
- ✅ Final Windows installer SHA-256 verification

### Release delivery

The final Windows installer was published to the dedicated public release channel and independently verified against its expected file size and SHA-256 digest before the public update manifest was advanced.

[View the 0.2.30-alpha release](https://github.com/Robocapa-eve/sentinel-releases/releases/tag/v0.2.30-alpha)

---

# 0.2.29-alpha // VERIFIED UPDATE DELIVERY

**Public pre-release · 28 August 2026**

This milestone completed the first end-to-end update path. SENTINEL can now detect a newer published build, verify the installer and hand the update over to a controlled Windows installation flow.

### For pilots

- 🪟 Added in-app update availability checks.
- 🪟 Added an explicit **one-click update** flow.
- 🔐 Installer downloads are verified against their expected **SHA-256** digest before execution.
- 🪟 SENTINEL can close for installation and restart after a successful update.
- ⚙️ Update failures are handled without breaking normal monitoring operation.

### Engineering notes

- Introduced a dedicated public release/update channel separate from the private source repository.
- Update metadata validates expected product, platform, release channel and version information.
- Downloaded installers are staged under SENTINEL's local application data area.
- Installer filename and expected digest are validated before installation is allowed.
- The public update manifest acts as the activation point for a release; release assets are published **before** the manifest is advanced.

### Public test result

The `0.2.28 → 0.2.29-alpha` path was used as an end-to-end update validation covering download, SHA-256 verification, unattended installer hand-off and automatic restart.

[View the 0.2.29-alpha release](https://github.com/Robocapa-eve/sentinel-releases/releases/tag/v0.2.29-alpha)

---

# 0.2.27-alpha // TACTICAL MONITORING

This phase pushed SENTINEL from a map that displays information toward a map that understands **where the pilot is actually monitoring from**.

### For pilots

- 🛰️ Added a dedicated **monitoring origin** for threat, intel and alert relevance.
- 🛰️ Added **AUTO / MAIN-follow** behavior for pilots who want SENTINEL to track their active EVE character automatically.
- 🛰️ Added a manual monitoring mode for scouts, parked characters and deliberate observation points.
- 🗺️ Separated map camera movement from the monitoring origin — exploring the map no longer silently moves the point used for tactical alerts.
- 🗺️ Improved semantic zoom and deep-system interaction across the tactical map.
- 🗺️ Expanded System Tooltips with direct tactical actions such as map focus, route display and zKill access.
- 🔔 Added native Windows alert playback that does not depend on browser focus.
- 🔔 Added distinct audio profiles for different tactical events.
- 🛰️ Refined the intel feed so own login/location events are not presented as ordinary hostile intelligence.

### Tactical design principle

A pilot should be able to **look somewhere else without accidentally listening somewhere else**. Map focus, current character location and monitoring origin are therefore treated as separate concepts.

### Engineering notes

- Threat relevance, intel range, kill relevance, scout data, watchlist events and native audio use the monitoring origin rather than the visual camera position.
- Native audio uses queued sequential playback to avoid alert overlap.
- Clearing the visible feed no longer destroys the tactical history required by other parts of the application.

---

# 0.2.26-alpha // NATIVE WINDOWS APPLICATION

SENTINEL became a real Windows desktop application rather than merely a local web interface.

### For pilots

- 🪟 Added a native Windows application shell.
- 🪟 Added system tray operation so SENTINEL can keep monitoring while the main window is hidden.
- 🪟 Closing the window hides the interface instead of terminating monitoring.
- 🪟 Added tray actions for opening SENTINEL, accessing logs, restarting and exiting.
- 🪟 Added single-instance behavior to prevent accidental duplicate application sessions.
- 🪟 Added a native WebView window for the tactical interface.
- 🪟 Added an installable Windows build and installer workflow.
- ⚙️ Application logs moved to the user's local application data directory.

### EVE tool coexistence

- SENTINEL uses its own local listener on **`127.0.0.1:18765`**.
- The EVE SSO callback uses the same dedicated listener.
- The port choice was deliberately separated from other EVE companion software so SENTINEL can coexist with tools such as EVE Canary.

### Engineering notes

- Introduced PyInstaller OneFolder packaging for the Windows application.
- Introduced an Inno Setup installer.
- Established separate install and runtime-data locations under the user's local profile.
- Added release integrity material including installer SHA-256 output.

---

# 0.2.25-alpha // TACTICAL FOUNDATION

This milestone represents the early foundation on which the current SENTINEL architecture was built.

### Core capability foundation

- 🛰️ EVE Online SSO / ESI character connectivity.
- 🛰️ Character and location-aware monitoring foundations.
- 🛰️ EVE chat/log ingestion for intelligence parsing.
- 🛰️ zKill-based kill intelligence integration.
- 🗺️ New Eden universe data and system-graph foundations.
- 🗺️ Interactive tactical map direction established.
- 🛰️ Threat-analysis and system-context foundations.
- ⚙️ FastAPI local backend with a web-based tactical frontend.

The focus at this stage was not polish. It was proving that live EVE data, local intel, kill information and the New Eden map could be brought together into one tactical workspace.

---

# DEVELOPMENT PRINCIPLES

### Local-first where practical

SENTINEL is designed as a Windows companion application. Local application state, logs and monitoring behavior are kept on the user's machine where the architecture allows it.

### Private source, public progress

The source repository is intentionally private. Public releases, this development log and future release documentation are published here so pilots can still follow the project's direction and maturity.

### Tactical clarity over feature count

A new feature is useful only if a pilot can understand what it means during actual gameplay. SENTINEL therefore prioritizes clear monitoring origin, range context, explicit actions and visible state over hidden automation.

### Alpha means development

SENTINEL is still an alpha project. Interfaces, behavior and internal systems may change as testing exposes better solutions.

---

# WHAT COMES NEXT?

The next security/release-trust layers under consideration include:

- 🔐 Windows executable and installer **code signing**.
- 🔐 Cryptographically **signed update metadata** in addition to SHA-256 integrity verification.
- ⚙️ Further build and dependency reproducibility.
- 🔐 Additional hardening of high-value application logic in distributed binaries.
- 🛰️ Continued development of tactical intelligence, mapping and threat-analysis capabilities.

Specific features and timing are intentionally not promised until they are tested and ready to enter the public development line.

---

## About this log

This is a curated public engineering history, not a dump of private commits or security-sensitive implementation details. Entries are written to show both **what changed for the pilot** and **what engineering milestone made it possible**.

SENTINEL is an independent third-party project for EVE Online. EVE Online and related marks are property of CCP Games. Publication of SENTINEL does not imply endorsement by CCP Games.

**Developer:** Robocapa  
**Project:** SENTINEL // Tactical Intelligence