# 🧭 TorqueNav

**A SatNav for Dual Universe.** A touch-screen list of all your saved locations: pick one, press **ENGAGE**, and your ship's autopilot flies there.

> 🧑‍🚀 **Brand new to this?** This guide assumes you know nothing. Follow [Quick start](#-quick-start-5-minutes) in order.

---

## 📖 Table of contents

1. [✨ What is TorqueNav?](#-what-is-torquenav)
2. [🔌 What to link](#-what-to-link)
3. [⚡ Quick start (5 minutes)](#-quick-start-5-minutes)
4. [🖥️ The screen explained](#️-the-screen-explained)
5. [📍 Everyday how-to](#-everyday-how-to)
6. [🎨 Colors](#-colors)
7. [💬 Chat commands](#-chat-commands)
8. [⚙️ Settings](#️-settings)
9. [💾 Copying your data to a new ship](#-copying-your-data-to-a-new-ship)
10. [🛠️ Troubleshooting](#️-troubleshooting)
11. [❓ FAQ](#-faq)
12. [📚 Glossary](#-glossary)
13. [🔧 Building from source](#-building-from-source)

---

## ✨ What is TorqueNav?

| | Feature | What it does |
|---|---|---|
| 📋 | **One list** | All your saved locations in one place, with **folders**, **search** and **sort** (by name or nearest). |
| 👆 | **Touch to select** | Click a location on the screen to select it. |
| 🚀 | **ENGAGE** | Sends the selected location to the seat's autopilot (needs TorqueHUD on the seat). |
| 📍 | **SAVE HERE / ADD ::POS** | Save where you are, or paste coordinates. |
| 🛣️ | **Routes** | Build a multi-stop trip and start it with one button. |
| 🪐 | **Planets** | The planets from the seat's atlas show up in the list too. |
| 🎨 | **Six color themes** | Cyan, amber, green, red, purple, white. |
| 🖼️ | **Logo on idle screens** | Your own image when the program is off. |
| 💾 | **Data copy** | Move all your data to a new ship with one Yes/No question. |

TorqueNav works **on its own**. With **TorqueHUD** on the seat and the **same databank** linked to both, the list becomes the seat's target list.

---

## 🔌 What to link

"Linking" means connecting an element to the **programming board** so the script can use it.

| Element | Needed? | Why |
|---|---|---|
| 🖥️ **Screen** (1 to 3) | ✅ **At least one** | Where the SatNav is drawn. More screens = more views at once. |
| 💽 **Databank** | ✅ **Yes**, the **same** one the seat uses | Saves your locations and shares them with TorqueHUD. |
| 🧠 **Core unit** | optional | |

📌 **Databanks are never linked for you.** You link them yourself.

---

## ⚡ Quick start (5 minutes)

1. 📥 Download `TorqueNav_config.json` from the [`release/`](release/) folder.
2. 📋 Open it in any text editor (Notepad is fine), **select everything** (`Ctrl+A`), **copy** (`Ctrl+C`). Don't change anything.
3. 🖱️ In game, **right-click your programming board** → **Advanced** → **Paste Lua configuration from clipboard**.
4. 🔌 Link the **screen(s)** and the **databank** (see above).
5. ▶️ **Activate** the programming board. The SatNav appears on the screen. 🎉

> 🗒️ Menu wording can differ slightly between game versions.

---

## 🖥️ The screen explained

**Top bar**

| Button | What it does |
|---|---|
| **LOCATIONS** | The list of places |
| **ROUTE** | Your multi-stop route |
| **SORT: NAME / NEAREST** | Switch how the list is ordered |
| **SEND n TO SEAT** | Appears when the board holds locations the seat doesn't have yet. Press it to send them over. |
| **SEAT LINKED** (green) / **STANDALONE** (amber) / **NO DATABANK** | Whether TorqueNav can talk to the seat. |
| **SET** | Settings (color theme) |

**Locations page buttons**

| Button | What it does |
|---|---|
| **SAVE HERE** | Saves your current position |
| **ADD ::POS** | Opens a box to type or paste a `::pos{...}` |
| **RENAME** | Renames the selected location |
| **DELETE** | Deletes the selected location (**press twice**) |
| **FOLDER** | Puts the selected location in a folder |
| **+ ROUTE** | Adds the selected location to your route |
| **ENGAGE / DISENGAGE** | Sends it to the autopilot (**press twice** to confirm) / stops it |
| **< PREV / NEXT >** | Page through long lists |

**Route page buttons:** **START ROUTE** (or **RESTART**), **STOP**, **CLEAR ROUTE** (press twice), **+ SELECTED**.

🛡️ **Press-twice protection.** DELETE, ENGAGE and CLEAR ROUTE ask you to press again within `confirmSeconds` (5 s by default), so a stray click does nothing.

🪐 **Planets** in the list can't be renamed or deleted. They come from the seat.

---

## 📍 Everyday how-to

**➕ Save where I am:** press **SAVE HERE**.

**📋 Save pasted coordinates:** copy a `::pos{...}` from the game, press **ADD ::POS**, paste it, confirm. Or in chat: `add My Mine ::pos{...}`.

**🚀 Fly to a place:** click it, then press **ENGAGE** twice. Needs the seat running TorqueHUD, linked through the same databank. If it says *ENGAGE NEEDS THE SEAT*, check the link chip in the top bar.

**🗂️ Use folders:** select a location, press **FOLDER**, type a name. Use `folder none` in chat to clear it. Use `open <name>` to show just one folder, `all` to see everything.

**🔍 Search:** `find <text>` in chat.

**🛣️ Build a route:** select places and press **+ ROUTE** for each, then open **ROUTE** and press **START ROUTE**. The autopilot visits each stop in order.

---

## 🎨 Colors

Press **SET** on the screen and tap a color swatch. It's saved and kept next time.

🩵 **cyan** · 🟠 **amber** · 🟢 **green** · 🔴 **red** · 🟣 **purple** · ⚪ **white**

Or type `theme purple` in the chat. You can also set the starting theme in the Lua parameters.

🖼️ **Idle logo:** when the program is off, the screens show a logo. Set `splashLogo` to your own image link, or leave it blank for a text title.

---

## 💬 Chat commands

Type these in the **Lua chat**. `help` lists them in game.

| Command | What it does |
|---|---|
| `find <text>` / `all` | Search / show everything |
| `folder <name>` (`none` clears) | Set the selected location's folder |
| `open <name>` | Show only one folder |
| `sort` | Change the sort order |
| `add [name] [::pos{...}]` | Save a location (pasted, or here) |
| `here [name]` | Save a location where you are |
| `rename <new name>` | Rename the selected location |
| `del` | Delete the selected location |
| `go <number or name>` | Select a location |
| `engage` | Send the selected location to the autopilot |
| `route` / `list` | Switch to the route / list page |
| `theme <name>` | cyan, amber, green, red, purple or white |
| `link` | Show what is linked |
| `render script\|html`, `rstest` | Screen drawing mode and a self-test (troubleshooting) |
| `mouse` | Click diagnostics (troubleshooting) |

---

## ⚙️ Settings

Right-click the programming board → **Edit Lua parameters**.

| Setting | Default | Meaning |
|---|---|---|
| `theme` | cyan | Color theme (the SET button on the screen also changes it and is remembered) |
| `splashLogo` | a logo link | Image on idle screens. Set your own link, or clear it. |
| `confirmSeconds` | 5 | Seconds you have to press DELETE / ENGAGE a second time |
| `screenMode` | script | `script` uses the game's drawing calls. `html` is the older way, in case script mode shows nothing. |
| `startPage` | list | First page of the first screen: `list` or `route` |

---

## 💾 Copying your data to a new ship

Built a new ship? Copy everything instead of typing it all again.

**You need:** your normal databank (with your data) and **one brand-new, empty databank**.

1. 🔌 Link **both** databanks to the programming board. **Link the empty one last.** The last one linked is the copy.
2. ▶️ Activate the board (or restart it).
3. ❓ A box appears: **"2nd databank recognized. Would you like to copy data?"**
4. ✅ Press **YES**. Your data is copied to the new databank.
5. 🚀 Unlink the old databank. Link the new one to your new ship's board and seat.

**What happens**

| Choice | Result |
|---|---|
| **YES** | Copies waypoints, settings (including autopilot settings), the saved route and TorqueNav's lists. |
| **NO** | Does nothing. It asks again next start, as long as the empty second databank stays linked. |
| Second databank **not empty** | Nothing is asked and nothing is written. Your data is safe. |

❌ **Not copied:** the ship's fuel calibration and hover/landed/takeoff heights. Those belong to the old ship.

🛡️ The old databank is only **read**, never changed.

---

## 🛠️ Troubleshooting

<details><summary><b>🖥️ The screen is blank.</b></summary>

Is a screen linked? Did you activate the board? Try `render html` in the chat. If that fixes it, set `screenMode` to `html`.
</details>

<details><summary><b>🚀 ENGAGE says "needs the seat".</b></summary>

The seat must run **TorqueHUD**, and the board and the seat must share the **same databank**. The chip in the top bar shows **SEAT LINKED** when it works.
</details>

<details><summary><b>👆 Clicks do nothing.</b></summary>

Aim at the screen from in front of it. Type `mouse` in the chat for click diagnostics.
</details>

<details><summary><b>📍 My locations are gone.</b></summary>

A databank must be linked. If you changed databanks, link the original again.
</details>

<details><summary><b>💾 The copy question never appears.</b></summary>

It only appears when a **second, empty** databank is linked. If it already holds data, nothing is asked.
</details>

---

## ❓ FAQ

**Do I need TorqueHUD?** No. TorqueNav works alone as a location list. ENGAGE and the shared list need TorqueHUD on the seat.

**Can I use several screens?** Yes, one to three. Each can show a different page.

**Can I delete a planet?** No. Planets come from the seat's atlas.

**Is this tested?** It's tested against a mock game. Real in-game behavior can differ, so please open an Issue if something misbehaves.

---

## 📚 Glossary

| Word | Meaning |
|---|---|
| **Programming board** | The element TorqueNav runs on. |
| **Link** | Connecting an element to the board so the script can use it. |
| **Databank** | An element that stores data between sessions. |
| **Waypoint / location** | A saved place. |
| **`::pos{...}`** | The game's coordinate format. |
| **Autopilot** | The ship flies to the target for you (TorqueHUD does this). |
| **Engage** | Send the selected location to the autopilot. |

---

## 🔧 Building from source

Only needed to change the code. Everyone else uses `release/`.

```
TorqueNav/
├── src/        Lua source parts
├── tools/      build script
├── tests/      mock-game tests
├── release/    the finished file to install
└── build.sh
```

```bash
# needs Lua 5.3/5.4 and Python 3
LUA=/path/to/lua ./build.sh
LUA=/path/to/lua ./tests/run_tests.sh
```

---

Fly safe, pilot! 🚀✨ Found a bug? Open an **Issue**.
