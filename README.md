<p align="center">
  <img src="logo.png" alt="WarpNet" width="640"/>
</p>

<h2 align="center">⚡ WarpNet MTK<br><sub>The honest network engine for MediaTek — v1.0.0 "Phantom" 👻</sub></h2>

<p align="center">
  <a href="https://github.com/Alchemiisst/WarpNet-MTK/releases"><img src="https://img.shields.io/badge/download-v1.0.0%20Phantom-blueviolet?style=for-the-badge&logo=github"/></a>
  <img src="https://img.shields.io/badge/license-ANCL%20v1.0-orange?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/platform-MediaTek%20only-green?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/root-Magisk%20·%20KernelSU%20·%20APatch-red?style=for-the-badge"/>
</p>

<p align="center">
  📣 <a href="https://t.me/Amberlyst">Telegram Channel</a> · 🧪 <a href="https://t.me/+xx-aXBime1g5ZjZl">Become a Tester</a> · ⭐ <a href="https://github.com/Alchemiisst/WarpNet-MTK">Star the repo</a>
</p>

---

## 📖 Table of Contents

- 🌟 [What is WarpNet MTK?](#-what-is-warpnet-mtk)
- ⚙️ [How It Works](#️-how-it-works)
- 🎛️ [The Four Modes](#️-the-four-modes)
- 🚀 [Efficiency & Results](#-efficiency--results)
- 🎬 [The Experience](#-the-experience)
- 📲 [Root Manager Compatibility](#-root-manager-compatibility)
- ✅ [Tested Devices](#-tested-devices)
- 🔄 [Updates](#-updates)
- 📥 [Installation](#-installation)
- 🛡️ [The Honesty Contract](#️-the-honesty-contract)
- 🧪 [Become a Tester](#-become-a-tester)
- 📜 [License](#-license)

---

## 🌟 What is WarpNet MTK?

Your MediaTek phone's modem is a **superbike 🏍️💨** — but stock Android makes it ride with the handbrake half-pulled: tiny buffers, radio-nap penalties, packets queued on sleepy little cores.

**WarpNet MTK** is a root module that removes the handbrake — tuning **only the device side** of the network stack, with engineering you can verify:

- 🔍 **Probed before apply** — if your kernel can't do it, WarpNet tells you instead of pretending
- 📸 **Snapshotted** — every stock value saved before touching anything
- ✅ **Verified on readback** — receipts, not vibes
- ♻️ **One-command revert** — `warpnet revert` and you're 100% stock again

No "400% SPEED BOOST" snake oil 🚫🐍 — just the real bottlenecks, open-heart surgery with a working undo button.

---

## ⚙️ How It Works

| 🧩 Tweak | 🗣️ In human words |
|---|---|
| ⚡ **BBR + fq** congestion control | Google's modern TCP brain — paces packets instead of panic-flooding |
| 🧭 **RPS/XPS packet steering** | Modem traffic processed on your **big/prime cores**, not the sleepy small ones |
| 📦 **BDP-matched 12 MB buffers** | Pipes finally sized for 5G — QUIC/HTTP-3 stops choking |
| 💤 **Radio-nap penalty removal** | `tcp_slow_start_after_idle=0` — no more "first seconds are slow" after your screen idles |
| 🌱 **ECN on → L4S-ready** | Future-proofed for the low-latency standard carriers are lighting up |
| 🛣️ **Self-healing MTU probing** | Finds the real path MTU, stops silent packet drops |
| 🌊 **Queue control** | Deeper backlog + bigger netdev budget = no dropped bursts |
| 🔁 **Smart Reconnect** | Your manual airplane-mode fix, automated: measured stall → gentle L1→L2→L3 ladder (data toggle → RIL bounce → airplane), 25-min cooldown, fully logged |
| 🌙 **Screen-off saver** | CPU-side **only** — it *never* touches your radio, Power-Saver, or Smart-5G |

---

## 🎛️ The Four Modes

| # | 🏷️ Mode | 🗣️ What it really does |
|---|---------|------------------------|
| 1️⃣ | **Turn off** | 100% stock restore. Every snapshot back. Like we were never here 🫥 |
| 2️⃣ | **SpeedBoost** | Light engine + **strong** screen-off saver 🔋 |
| 3️⃣ | **WarpNet** | Full engine + light saver + Smart Reconnect — the daily driver ⭐ |
| 4️⃣ | **WarpNet++** | Mode 3 + daemon full-burst profile — **no time limit by default** ⏱️∞ (stays until you switch; `warpnet burst-min N` for a timed window) |

Switch anytime: root manager **Action** button 🎚️ (Vol ± to move, Power to apply) or `su -c warpnet` in Termux 💻.

---

## 🚀 Efficiency & Results

WarpNet doesn't cook numbers — it gives you the **bench tool to prove them yourself** (`warpnet bench`: idle RTT, loaded RTT, Mbps, SINR, saved receipts 🧾). What it consistently delivers:

- ⏱️ **Instant ramp-up after idle** — the "why is my 5G slow for 10 seconds" problem, gone
- 📈 **Throughput holds closer to your cell's real ceiling** under load (big-core packet steering + right-sized buffers)
- 🎮 **Calmer latency while downloading** — pacing + queue control keeps loaded RTT from spiking
- 🔁 **Self-recovery from zombie connections** — Smart Reconnect re-camps dying cells before you notice
- 🔋 **Zero radio-side battery cost** — the saver lives on the CPU only; 5G stays full-power when the screen is *on*

⚠️ Physics is still physics: tower congestion, spectrum and your plan cap are the ceiling. WarpNet maximizes **your** stack to meet it.

---

## 🎬 The Experience

- 🧪 **Flash flow:** AMBERLYST alchemy box → loading bar → your device card → live engine preflights → ⭐ GitHub ask → Telegram launch
- 🎚️ **Action-button menu:** live panel (radio/SA type, RSRP/SINR → plain-words verdict, live speed, engine truth) — **Vol ± moves the cursor, POWER applies**, receipts printed
- 💻 **Termux twin:** same menu, same state, same race-proof lock:
  ```bash
  su
  warpnet          # 🎛️ interactive menu — stays open after applying
  warpnet status   # 📊 dashboard
  warpnet bench    # 🧾 receipts: idle/loaded RTT, Mbps, SINR
  warpnet dnstest  # 🏎️ races resolvers on YOUR route, sets the winner
  warpnet check    # 🩺 honest diagnostics + saver warnings
  warpnet watch    # 📡 live speed + signal ticker
  warpnet revert   # ♻️ everything stock in one command
  ```

---

## 📲 Root Manager Compatibility

WarpNet MTK is a **universal root module** — one zip, every manager:

| 🧰 Root Manager | 🟢 Status |
|---|---|
| **Magisk** (official + forks) | ✅ Fully supported |
| **KernelSU / KernelSU-Next** | ✅ Fully supported — incl. 🖼️ card banner & 🔄 update checks |
| **APatch** | ✅ Fully supported |

> ⚠️ **MediaTek devices only.** The installer hard-gates the chipset: on Snapdragon it shows a styled rejection, modifies **nothing**, and points you to 👉 [WarpNet-SD](https://github.com/Alchemiisst/WarpNet-SD).

---

## ✅ Tested Devices

| 📱 Phone | 🧠 Chipset | 🤖 Android | 🔓 Root Manager | 🧪 Result |
|---|---|---|---|---|
| **Infinix Note 50 Pro** (X6870) | MediaTek Dimensity 7300 Ultimate | 16 | KernelSU | ✅ **Success** — engine applies clean, all 4 modes cycle, bench receipts verified |

> 🧪 *This sheet grows with every tester report — flash it, bench it, and your device lands here. See [Become a Tester](#-become-a-tester)!*

---

## 🔄 Updates

WarpNet MTK plugs into your root manager's **update checker** (`updateJson`) 📡. When a new build ships, the module card lights up **Update available** — tap, download, flash, done. No link-hunting in chat history 🕵️.

---

## 📥 Installation

1. 🔓 Root with **Magisk**, **KernelSU**, or **APatch**
2. 📦 Grab `warpnet-mtk-v1.0.0.zip` from [Releases](https://github.com/Alchemiisst/WarpNet-MTK/releases) → flash → **reboot** (default mode: 3️⃣ WarpNet)
3. 🎛️ Switch modes via the manager's **Action** button or `su -c warpnet` in Termux

---

## 🛡️ The Honesty Contract

- 🚫 WarpNet **never** touches modem NV, vendor radio props, or anything that needs a service center to undo
- 🔍 If a tweak isn't supported by your kernel, you get an honest **SKIP** — never a fake "applied ✔"
- 📸 Every change is snapshotted; `warpnet revert` restores **everything**
- 🧾 Every claim is measurable — `warpnet bench` receipts or it didn't happen

---

## 🧪 Become a Tester

More devices = more proof = a better engine for everyone 🌍. Testers get **early builds**, direct input on features, and their device immortalized on the [Tested Devices](#-tested-devices) sheet 🏆.

<p align="center">
  <a href="https://t.me/+xx-aXBime1g5ZjZl"><b>🧪 JOIN THE TESTER SQUAD ON TELEGRAM 🧪</b></a><br>
  <sub>Flash → bench → report. That's the whole job description ⚗️</sub>
</p>

---

## 📜 License

**ANCL v1.0 — Alchemist Non-Commercial License** (custom — see [`LICENSE`](LICENSE)).

Copyright (c) 2026 **Alchemist** · [github.com/Alchemiisst/WarpNet-MTK](https://github.com/Alchemiisst/WarpNet-MTK) — full credit required, no monetization/donation links, must link back to this repo, non-commercial redistribution only.

---

<p align="center"><b>⚡ built with honesty by Alchemist · 📣 <a href="https://t.me/Amberlyst">t.me/Amberlyst</a> ⚡</b></p>
