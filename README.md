<div align="center">

<img src="sentinel-brand.png" width="32" alt="SENTINEL Logo">

# SENTINEL // TACTICAL INTELLIGENCE

### **Your Tactical Intelligence HQ for New Eden.**

**LIVE KILL MAP · TACTICAL WARNING · MULTI-CHANNEL INTEL · ROLLING MEMORY · INTELLIGENCE BRAIN**

<br>

![Status](https://img.shields.io/badge/STATUS-ACTIVE%20DEVELOPMENT-35c98b?style=flat-square)
![Channel](https://img.shields.io/badge/CHANNEL-ALPHA-4da3d9?style=flat-square)
![Platform](https://img.shields.io/badge/PLATFORM-WINDOWS-737d8c?style=flat-square)
![Public](https://img.shields.io/badge/PUBLIC%20BUILD-0.2.30--alpha-8b6fd9?style=flat-square)
![Development](https://img.shields.io/badge/DEV%20LINE-0.3.0--alpha-d86f45?style=flat-square)

<br>

**🇬🇧 English** · [🇩🇪 Deutsch](README_DE.md)

</div>

<p align="center">
  <a href="https://raw.githubusercontent.com/Robocapa-eve/sentinel-releases/main/assets/screenshots/sentinel-tactical-intelligence-overview-full.jpg">
    <img src="assets/screenshots/sentinel-tactical-intelligence-overview.webp" width="460" alt="SENTINEL Tactical Intelligence Overview">
  </a>
</p>

<p align="center"><sub>SENTINEL Tactical Intelligence Overview · Click to enlarge</sub></p>

---

## NOT ANOTHER KILLBOARD. NOT ANOTHER STATIC MAP.

SENTINEL is being built as a dedicated tactical-intelligence command center for **EVE Online**.

It combines live kill activity, Intel channels, New Eden map context, monitoring origin, jump distance, Scouts, Local Scan, route awareness and native Windows alerts into one operational picture.

> **SENTINEL doesn't just show events. It turns observations into actionable tactical context.**

### **See the threat. Know the distance. Understand the pattern. React sooner.**

---

# CURRENT PUBLIC BUILD

| | |
|---|---|
| **Latest public build** | `0.2.30-alpha` |
| **Current development line** | `0.3.0-alpha` |
| **Channel** | Alpha / pre-release |
| **Platform** | Windows x64 |
| **Source code** | Private |

### 🚀 [Download / Releases](https://github.com/Robocapa-eve/sentinel-releases/releases)

> [!IMPORTANT]
> `0.3.0-alpha` is currently a **development line**, not a downloadable 0.3.0 Windows build. Installed clients remain on `0.2.30-alpha` until a real 0.3.0 installer is built, verified and the update manifest is advanced.

---

# ⚡ LATEST ENGINEERING SPRINT // 31 AUG → 1 SEP

The last two calendar days were the largest architecture jump in SENTINEL so far.

The project moved from shipping the public `0.2.30-alpha` Tactical Intelligence System to running a validated backend intelligence foundation with:

- 🛰️ dedicated HTTPS/WSS Live Relay
- 🧠 PostgreSQL 16-backed Tactical Memory
- 🔄 completed-day reconciliation and safe missing-ID repair
- 📦 a proven **13,962-killmail** historical production canary
- 🕒 rolling **90-day UTC** retention
- 🛡️ verified backup/restore operations
- 🧠 Tactical Intelligence Brain **1A** for pilot behavior
- 🧠 Tactical Intelligence Brain **1B** for systems, corporations and alliances
- 🔐 hardened CI, security and repository integrity automation

**Validation snapshot:** **224 tests passed** in the combined Windows/relay suite, **71 PostgreSQL-backed Intelligence tests passed**, and the latest 1B production checkpoint held roughly **480k canonical kills · 2.0M attacker rows · 7.8M item rows**.

### 📡 [Read the full two-day engineering chronicle](CHANGELOG.md#-engineering-sprint--31-aug--1-sep-2026)

---

# THREE OPERATOR SYSTEMS DEFINE SENTINEL

## 💀 LIVE KILL MAP

Public kill observations are resolved against the New Eden universe graph and placed into tactical map context with system, distance, freshness and ship/kill information where available.

## 🚨 TACTICAL LIVE MAP WARNING SYSTEM

Relevant activity becomes a warning layer around the system the pilot is actually monitoring, with configurable ranges, map markers, persistence and native Windows audio.

## 🛰️ MULTI-CHANNEL INTEL MAP

User-enabled EVE Intel channels can be parsed and resolved into the same map/distance/monitoring context as kill, Scout and Watchlist information.

---

# 0.3.0 DEVELOPMENT — THE INTELLIGENCE FOUNDATION

The current development milestone adds a server-side layer behind the existing Windows application.

## 🛰️ Dedicated Live Relay

SENTINEL now operates a dedicated HTTPS/WSS relay at `relay.sentinel-eve.de` with sequential public R2Z2 ingestion, bounded buffers, reconnect/resume and explicit resync handling.

**Direct R2Z2 remains the authoritative desktop live source.** Relay cutover is not automatic.

## 🧠 Rolling 90-day Tactical Memory

Recent public combat observations can now be stored in a bounded PostgreSQL-backed Memory containing victim, attacker, item, organization and source-provenance context.

The production policy is intentionally **90 days**. Older data is pruned automatically so the system remains useful, predictable and affordable.

## 🔄 Reconciliation

Completed UTC days can be compared against public zKill history. Demonstrated gaps can be repaired idempotently without pretending the public source chain contains every EVE killmail.

## 🧠 Tactical Intelligence Brain 1A

Read-only pilot analysis can derive:

- observed ship/weapon usage
- target preferences
- recurring co-attacker relationships
- historical loss-fit families
- evidence, recency and confidence

Historical loss fits are **not** presented as current fits, and recurring co-attackers are **not** automatically called fleet members.

## 🧠 Tactical Intelligence Brain 1B

The intelligence layer now also understands recent activity patterns for:

- solar systems
- corporations
- alliances
- attacker/victim hulls
- UTC activity hours
- recurring co-attacking organizations

Route/roam reconstruction remains a future, separately confidence-scored phase.

---

# CURRENT WINDOWS CAPABILITIES

The public 0.2.30-alpha build already includes:

- MAP INTEL profiles: SOLO / SAFE / ROAM / ROUTE / SCOUT / CUSTOM
- 15J / 25J / 50J Tactical Feed Depth
- Tactical Intelligence Feed
- KILL HEAT
- Tactical Picture activity trends
- pinned System Tooltips
- SYSTEM VERLAUF
- AUTO · MAIN and manual Monitoring
- Local Scan Snapshot / Delta
- EVE SSO / ESI integration
- native Windows alerts
- Dark / Light / OLED themes
- German and English UI
- verified one-click updates with SHA-256 integrity checks

SENTINEL supports gameplay decisions and **does not automate gameplay input**.

---

# DEVELOPMENT & RELEASE TRUST

The private source repository contains implementation, tests and engineering details. This public repository exists for Windows releases and a transparent development chronicle.

### 📡 [Public Development Log / Changelog](CHANGELOG.md)

Release activation follows a strict order:

`Build → Test → Installer → SHA-256 → Publish assets → Verify → update-manifest.json last`

The public manifest is never advanced to a version without a real verified installer.

SENTINEL also follows a **GitHub zero-cost policy** for project infrastructure: production tactical database storage is not designed around paid GitHub Artifacts, Packages or Codespaces.

---

<div align="center">

## SENTINEL // TACTICAL INTELLIGENCE

### **KEEP YOUR TOOLS. ADD INTELLIGENCE.**

**Protect yourself. Find the action. Understand what is happening beyond your grid.**

<br>

**🇬🇧 English** · [🇩🇪 Deutsch](README_DE.md)

<br><br>

<sub>
SENTINEL is an independent third-party application for EVE Online and is not affiliated with or endorsed by CCP Games.<br>
EVE Online and related marks are property of CCP hf.
</sub>

<br>

**Developed & maintained by Robocapa**

</div>
