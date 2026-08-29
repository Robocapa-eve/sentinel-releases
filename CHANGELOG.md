# SENTINEL // DEVELOPMENT LOG

> **Tactical Intelligence for EVE Online**  
> Public development chronicle · Windows x64 · Alpha channel

SENTINEL is being built as a focused tactical companion for pilots who want a clearer picture of what is happening around them in New Eden: live intelligence, threat context, system awareness and map-based situational analysis.

This document makes the **development journey public** while the application source code remains private. It records meaningful user-facing, reliability, security and engineering milestones without publishing sensitive implementation details.

---

## CURRENT SIGNAL

| | Status |
|---|---|
| **Latest public build** | `0.2.29-alpha` |
| **Current development track** | Security & Reliability Foundation |
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

# UNRELEASED // SECURITY & RELIABILITY FOUNDATION

**Development milestone · 29 August 2026**

The current development track is focused on making SENTINEL safer and more predictable before broader public testing. The goal is simple: tactical software should be trustworthy when it is running quietly in the background for hours.

### For pilots

- 🔐 Strengthened the boundary around SENTINEL's local Windows service.
- 🔐 Improved validation of local application requests and browser-originated traffic.
- 🔐 Hardened authentication callback handling used by EVE SSO.
- 🔐 Added additional protection around local WebSocket connections.
- ⚙️ Improved dependency hygiene and ongoing vulnerability monitoring.
- 🧪 Expanded automated validation before changes are accepted into the main development line.

### Security engineering

- Added automated **full-history secret scanning** with Gitleaks.
- Added automated **Python dependency vulnerability auditing** with `pip-audit`.
- Security scans now run on relevant development changes and on a recurring weekly schedule.
- A dependency audit immediately identified known issues in the previously allowed `cryptography 46.x` line; SENTINEL was moved to the patched `50.x` line and revalidated.
- Hardened repository exclusions for credentials, tokens, private keys, certificates, signing material and local environment files.
- Added dedicated `SECURITY.md`, `PRIVACY.md` and a proprietary software license to the private source repository.

### Continuous validation

- 🧪 Automated Windows CI now validates SENTINEL on Python 3.12.
- 🧪 Current automated suite: **85 tests**.
- 🧪 Python source compilation is validated automatically.
- 🧪 Frontend JavaScript syntax is validated automatically.
- 🧪 Git whitespace/error checks run as part of CI.
- 🔐 Security scanning and normal application CI are intentionally separate so failures remain easy to diagnose.

> [!NOTE]
> This milestone improves the security baseline; it is not a claim that any desktop application can be made impossible to reverse engineer or completely free of vulnerabilities.

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
- 🗺️ Expanded system dossiers with direct tactical actions such as map focus, route display and zKill access.
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
