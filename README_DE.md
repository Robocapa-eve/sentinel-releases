<div align="center">

<img src="sentinel-brand.png" width="32" alt="SENTINEL Logo">

# SENTINEL // TACTICAL INTELLIGENCE

### **Deine Tactical Intelligence Zentrale für New Eden.**

**LIVE KILL MAP · TACTICAL WARNING · MULTI-CHANNEL INTEL · ROLLING MEMORY · INTELLIGENCE BRAIN**

<br>

![Status](https://img.shields.io/badge/STATUS-AKTIVE%20ENTWICKLUNG-35c98b?style=flat-square)
![Kanal](https://img.shields.io/badge/KANAL-ALPHA-4da3d9?style=flat-square)
![Plattform](https://img.shields.io/badge/PLATTFORM-WINDOWS-737d8c?style=flat-square)
![Public](https://img.shields.io/badge/PUBLIC%20BUILD-0.2.30--alpha-8b6fd9?style=flat-square)
![Development](https://img.shields.io/badge/DEV%20LINE-0.3.0--alpha-d86f45?style=flat-square)

<br>

[🇬🇧 English](README.md) · **🇩🇪 Deutsch**

</div>

<p align="center">
  <a href="https://raw.githubusercontent.com/Robocapa-eve/sentinel-releases/main/assets/screenshots/sentinel-tactical-intelligence-overview-full.jpg">
    <img src="assets/screenshots/sentinel-tactical-intelligence-overview.webp" width="460" alt="SENTINEL Tactical-Intelligence-Übersicht">
  </a>
</p>

<p align="center"><sub>SENTINEL Tactical-Intelligence-Übersicht · Zum Vergrößern anklicken</sub></p>

---

## KEIN WEITERES KILLBOARD. KEINE WEITERE STATISCHE MAP.

SENTINEL wird als dedizierte Tactical-Intelligence-Zentrale für **EVE Online** entwickelt.

Die Plattform verbindet Live-Kill-Aktivität, Intel-Channels, New-Eden-Map-Kontext, Monitoring Origin, Jump-Distanzen, Scouts, Local Scan, Route Awareness und native Windows-Warnungen zu einem gemeinsamen operativen Lagebild.

> **SENTINEL zeigt Ereignisse nicht nur an. Es verwandelt Beobachtungen in verwertbaren taktischen Kontext.**

### **Gefahr sehen. Entfernung kennen. Muster verstehen. Früher reagieren.**

---

# AKTUELLER ÖFFENTLICHER BUILD

| | |
|---|---|
| **Letzter öffentlicher Build** | `0.2.30-alpha` |
| **Aktuelle Entwicklungslinie** | `0.3.0-alpha` |
| **Channel** | Alpha / pre-release |
| **Plattform** | Windows x64 |
| **Source Code** | Privat |

### 🚀 [Downloads / Releases](https://github.com/Robocapa-eve/sentinel-releases/releases)

> [!IMPORTANT]
> `0.3.0-alpha` ist derzeit eine **Entwicklungslinie**, noch kein herunterladbarer 0.3.0-Windows-Build. Installierte Clients bleiben auf `0.2.30-alpha`, bis ein echter 0.3.0-Installer gebaut, verifiziert und das Update-Manifest anschließend aktiviert wurde.

---

# ⚡ AKTUELLER ENGINEERING SPRINT // 31. AUG → 1. SEP

Die letzten zwei Kalendertage waren der bisher größte Architektur-Sprung von SENTINEL.

Aus dem veröffentlichten `0.2.30-alpha` Tactical Intelligence System entstand parallel eine validierte Backend-Intelligence-Plattform mit:

- 🛰️ eigenem HTTPS/WSS Live Relay
- 🧠 PostgreSQL-16-basiertem Tactical Memory
- 🔄 Completed-Day Reconciliation und sicherer Missing-ID-Reparatur
- 📦 einem bewiesenen **13.962-Killmail** Historical Production Canary
- 🕒 rollierendem **90-Tage-UTC** Memory
- 🛡️ verifizierten Backup-/Restore-Abläufen
- 🧠 Tactical Intelligence Brain **1A** für Pilot-Verhalten
- 🧠 Tactical Intelligence Brain **1B** für Systeme, Corporations und Alliances
- 🔐 gehärteter CI-, Security- und Repository-Automation

**Validierungs-Snapshot:** **224 Tests bestanden** im kombinierten Windows-/Relay-Testlauf, **71 PostgreSQL-basierte Intelligence-Tests bestanden** und der letzte 1B-Produktionscheckpoint enthielt ungefähr **480k kanonische Kills · 2,0 Mio. Attacker Rows · 7,8 Mio. Item Rows**.

### 📡 [Die komplette Zwei-Tage-Engineering-Chronik](CHANGELOG.md#-engineering-sprint--31-aug--1-sep-2026)

---

# DREI OPERATOR-SYSTEME DEFINIEREN SENTINEL

## 💀 LIVE KILL MAP

Öffentliche Kill-Beobachtungen werden gegen den New-Eden-Universe-Graph aufgelöst und mit System, Entfernung, Aktualität und Ship-/Kill-Kontext auf der Tactical Map eingeordnet.

## 🚨 TACTICAL LIVE MAP WARNING SYSTEM

Relevante Aktivität wird zu einer Warning-Layer rund um das tatsächlich überwachte System – mit konfigurierbaren Ranges, Map Markern, Persistence und nativen Windows-Audio-Warnungen.

## 🛰️ MULTI-CHANNEL INTEL MAP

Vom Benutzer aktivierte EVE-Intel-Channels werden in denselben Map-, Distance- und Monitoring-Kontext eingeordnet wie Kill-, Scout- und Watchlist-Informationen.

---

# 0.3.0 DEVELOPMENT — DAS INTELLIGENCE-FUNDAMENT

Der aktuelle Entwicklungsmeilenstein ergänzt hinter der bestehenden Windows-Anwendung eine eigene serverseitige Intelligence-Schicht.

## 🛰️ Dedizierter Live Relay

SENTINEL betreibt jetzt einen eigenen HTTPS/WSS-Relay unter `relay.sentinel-eve.de` mit sequenzieller öffentlicher R2Z2-Verarbeitung, begrenzten Puffern, Reconnect/Resume und explizitem Resync.

**Direct R2Z2 bleibt im Desktop die autoritative Live-Quelle.** Ein Relay-Cutover erfolgt nicht automatisch.

## 🧠 Rollierendes 90-Tage Tactical Memory

Aktuelle öffentliche Combat-Beobachtungen können nun in einem begrenzten PostgreSQL-Memory gespeichert werden – einschließlich Victim-, Attacker-, Item-, Organisations- und Source-Provenance-Kontext.

Die Produktionsregel ist bewusst **90 Tage**. Ältere Daten werden automatisch entfernt, damit das System nützlich, vorhersehbar und kostenseitig kontrollierbar bleibt.

## 🔄 Reconciliation

Abgeschlossene UTC-Tage können gegen die öffentliche zKill-Historie geprüft werden. Nachgewiesene Lücken lassen sich idempotent reparieren, ohne so zu tun, als würde die öffentliche Quellenkette jeden EVE-Killmail enthalten.

## 🧠 Tactical Intelligence Brain 1A

Die read-only Pilotanalyse kann unter anderem ableiten:

- beobachtete Ship-/Weapon-Nutzung
- Target Preferences
- wiederkehrende Co-Attacker-Beziehungen
- historische Loss-Fit-Familien
- Evidence, Recency und Confidence

Historische Loss Fits werden **nicht** als aktuelles Fit ausgegeben, und wiederkehrende Co-Attacker werden **nicht automatisch als Fleet Members** bezeichnet.

## 🧠 Tactical Intelligence Brain 1B

Die Intelligence-Schicht versteht jetzt außerdem aktuelle Aktivitätsmuster für:

- Sonnensysteme
- Corporations
- Alliances
- Attacker-/Victim-Hulls
- UTC-Aktivitätszeiten
- wiederkehrende gemeinsam beobachtete Organisationen

Roam- und Route-Rekonstruktion bleibt eine spätere, separat confidence-bewertete Phase.

---

# AKTUELLE WINDOWS-FUNKTIONEN

Der öffentliche Build 0.2.30-alpha enthält bereits:

- MAP INTEL Profile: SOLO / SAFE / ROAM / ROUTE / SCOUT / CUSTOM
- 15J / 25J / 50J Tactical Feed Depth
- Tactical Intelligence Feed
- KILL HEAT
- Tactical Picture Activity Trends
- angepinnte System Tooltips
- SYSTEM VERLAUF
- AUTO · MAIN und manuelles Monitoring
- Local Scan Snapshot / Delta
- EVE SSO / ESI Integration
- native Windows Alerts
- Dark / Light / OLED Themes
- deutsche und englische UI
- verifizierte One-Click-Updates mit SHA-256

SENTINEL unterstützt Gameplay-Entscheidungen und **automatisiert keine Gameplay-Eingaben**.

---

# ENTWICKLUNG & RELEASE TRUST

Das private Source Repository enthält Implementierung, Tests und Engineering-Details. Dieses öffentliche Repository existiert für Windows-Releases und eine nachvollziehbare Entwicklungschronik.

### 📡 [Öffentlicher Development Log / Changelog](CHANGELOG.md)

Release-Aktivierung folgt einer festen Reihenfolge:

`Build → Test → Installer → SHA-256 → Assets veröffentlichen → verifizieren → update-manifest.json zuletzt`

Das öffentliche Manifest wird niemals auf eine Version gesetzt, für die kein realer verifizierter Installer existiert.

SENTINEL folgt außerdem einer **GitHub-Zero-Cost-Regel**: Produktionsdatenbank-Speicher wird nicht auf kostenpflichtige GitHub Artifacts, Packages oder Codespaces aufgebaut.

---

<div align="center">

## SENTINEL // TACTICAL INTELLIGENCE

### **KEEP YOUR TOOLS. ADD INTELLIGENCE.**

**Schütze dich. Finde die Action. Verstehe, was jenseits deines Grids passiert.**

<br>

[🇬🇧 English](README.md) · **🇩🇪 Deutsch**

<br><br>

<sub>
SENTINEL ist ein unabhängiges Drittanbieter-Projekt für EVE Online und steht in keiner Verbindung zu CCP Games und wird nicht von CCP Games unterstützt oder empfohlen.<br>
EVE Online und zugehörige Marken sind Eigentum von CCP hf.
</sub>

<br>

**Entwickelt & gepflegt von Robocapa**

</div>
