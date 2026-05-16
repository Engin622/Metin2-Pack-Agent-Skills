# ⚔️ Metin2 Client Documentation Framework (Skills Library)

Welcome to the most comprehensive technical documentation library for the Metin2 client. This repository contains a granular mapping of the game's internal file structures, interface logic, and asset hiyerarşisi.

## 🚀 Project Overview

This project serves as a foundational reference for developers interested in:
- **Client Modding:** Understanding how to modify `.py` scripts and `.epk/eix` packs.
- **UI/UX Design:** Mapping the coordinate systems and element hiyerarşisi of the Metin2 interface.
- **Automation:** Identifying memory structures and packet flows for stable tool development.
- **Web Porting:** Bridging legacy binary assets with modern web environments (Three.js/Vite).

## 📂 Repository Structure

The documentation is categorized into three main layers:

### 1. 🖥️ UIScript Layer (`/uiscript`)
Detailed documentation for every interface window in the game:
- **Inventory & Equipment:** Slot indices, grid structures, and costume systems.
- **Communication:** Messenger, whisper, and guild interfaces.
- **HUD & Radar:** Taskbar gauges, minimap logic, and floating notification buttons.
- **Systems:** Trading, private shop building, refining (blacksmith), and fishing.

### 2. 🧠 Root & Logic Layer (`/root`)
Mapping of the core Python engine:
- **Client Boot:** How the `Index` file works and the entry points (`system.py`, `prototype.py`).
- **Configuration:** MSM files (character settings), `colorinfo.py`, and `atlasinfo.txt`.
- **Game Phases:** Intro (Login/Select/Empire) and Game loop architectures.

### 3. 📦 Asset & Pack Layer (`/assets`)
Documentation for the binary pack files:
- **Indoor/Outdoor:** Dungeon and map structures.
- **NPC/Monster/PC:** 3D model hiyerarşisi and animation mapping.
- **Effect & Sound:** Visual effect triggers and background music (BGM) structures.

## 🛠️ Usage for Developers

Each directory contains a `skills.md` file that explains:
- **Functionality:** What the component manages in-game.
- **Hierarchy:** A Mermaid diagram showing the parent-child relationship of UI elements.
- **Modification Tips:** Guidelines for safely editing coordinates or adding new features.
- **Data Flow:** How data travels between the server and the client interface.

## 📜 Legal Disclaimer & License

- **Ownership:** All original Metin2 game assets, binaries, and intellectual property belong to **Gameforge 4D GmbH** and **Ymir Entertainment Co., Ltd.**
- **Documentation:** The technical analysis, mapping, and documentation provided in this repository are created by **Engin622**.
- **License:** This documentation framework is provided under the **MIT License**. You are free to use, modify, and distribute the *documentation* itself, provided that you respect the intellectual property of the original game owners.

---
*Created with ❤️ for the Metin2 development community.*
