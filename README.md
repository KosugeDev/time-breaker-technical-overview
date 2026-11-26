<div align="center">

# ⚔️ Time Breaker: Action & Runner

**A 3D Unity mobile auto-runner and hack-and-slash action game blending time manipulation, color-based sword abilities, and burst mechanics.**

[![Engine](https://img.shields.io/badge/Engine-Unity%202022.3%20LTS-000000?style=flat-square&logo=unity)](https://unity.com/)
[![Platform](https://img.shields.io/badge/Platform-Android%20%7C%20Google%20Play-3DDC84?style=flat-square&logo=android)](https://play.google.com/)
[![Language](https://img.shields.io/badge/Code-C%23-239120?style=flat-square&logo=csharp)](https://learn.microsoft.com/en-us/dotnet/csharp/)

<br>

📱 **[View on Google Play](https://play.google.com/store/apps/details?id=YOUR_PACKAGE_NAME)**

</div>

---

## 📖 Overview

**Time Breaker: Action & Runner** is a mobile 3D action-runner developed in **Unity (`2022.3.62f3`)** for **Android** and published on **Google Play**. It combines continuous lane/path running with responsive melee combos, time-rewind movement, elemental sword skills, and area-of-effect burst abilities across structured stages, special areas, and boss encounters.

This repository presents a high-level architectural and engineering overview of the project without exposing proprietary source code or sensitive security internals.

---

## ✨ Key Gameplay & System Features

- **🏃 Directional Auto-Runner & Speed Control:** Continuous forward movement with smooth 90° platform turn handling, four-tier speed selection (Slow, Normal, Fast, Turbo), and dedicated control schemes for desktop testing, two-finger touch, and one-finger swipe play.
- **⚔️ Melee Combos, Self-Dash & Auto-Aim:** Multi-stage sword combos synchronized with animation events, aerial/slam/kick attacks, horizontal target alignment assistance, and a **Self-Dash** mechanic that records recent movement history to rewind position and manipulate flow.
- **🌈 8 Color-Based Sword Skills:** Charging the skill meter unlocks distinct elemental effects tailored to the active color—including enemy/time slow, poison damage-over-time, ranged slash waves, fireballs, orbiting rings, life steal, shadow copies, and fast nearest-target selection powered by a **Kd-Tree** spatial structure.
- **💥 Burst Abilities:** Area-of-effect bursts (`Normal`, `Blue`, `Green`) that trigger environmental spikes, enemy position rewind, or toxic cloud zones.
- **🧟 Diverse Enemies, Hard Mode & Bosses:** Multiple enemy archetypes spawned per stage with optional **Hard Mode** reinforcements, distance-based culling, and multi-attack boss encounters.
- **📈 Progression, Upgrades & Customization:** Stage rank evaluations (`S` through `F`), sword power/duration upgrades, burst enhancements, head and backplane skins, and an **EN / TR** localization system driven by structured **JSON** data.

---

## 🏗️ Architectural Overview

Rather than relying on a heavy global singleton graph, the project uses explicit scene flow and centralized per-scene wiring:

- **Scene Pipeline & Progression:** Starts with an initialization/boot flow (`FirstScene`), optional first-time narrative and tutorial sequences (`_NarrativeScene`, `_TutorialScene`), and playable levels (`Level1`–`Level30` in the current release build, with progression structures designed to scale toward higher stages, special zones, and boss milestones).
- **Scene-Level Dependency Wiring:** Each level initializes its core runtime references and UI bindings during startup (`Awake`) so gameplay systems remain decoupled and predictable across scene loads.
- **Save & Migration Layer:** Persistent player progression, unlocks, economy state, and preferences are serialized to binary files with backup recovery, schema/array migration across updates, and integrity verification.
- **Spatial Indexing & Culling:** Uses distance culling and a **Kd-Tree** implementation for efficient spatial queries during high-action combat without unnecessary per-frame scanning.
- **Localization System:** Loads **English** and **Turkish** strings from pre-authored **JSON** tables for consistent UI and gameplay text.

---

## 🛠️ Tech Stack & Integrations

- **Core Engine:** Unity `2022.3.62f3` (Android / Google Play target)
- **Camera & Motion:** Cinemachine (including impulse feedback) & DOTween
- **Content & UI:** TextMeshPro, Addressables, JSON-based EN/TR localization
- **Monetization & Compliance:** Google Mobile Ads (AdMob with UMP consent and mediation) & Unity IAP

---

## 🔒 Repository Scope & Intellectual Property

- **Source & Assets:** Gameplay source code, custom shaders, 3D assets, audio, and internal security/anti-tamper mechanisms are **proprietary / closed-source** and are not included in this repository.
- **Purpose:** Maintained as a technical portfolio and architecture reference for **Time Breaker: Action & Runner**.
