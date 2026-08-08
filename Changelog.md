# Changelog — WarpNet MTK

## v1.0.0 "Phantom" (2026-08-08)

### 🐛 Hot-fix release (field feedback from first testers)
- **FIX: Action menu spam** — each volume-key press reprinted the whole menu (2-3 screens of text). Now: **one line per press**, cursor moves cleanly.
- **FIX: double-trigger on keys** — hardware DOWN+UP event pairs were double-counted; now only real DOWN presses count.
- **FIX: 60s timeout removed** — Power/Vol selection now waits as long as you need.
- **FIX: Power-button screen-off fight** — added wake-guard loop so the apply/process output is actually visible.
- **FIX: Speed meter** — broken on roms where `ip route` parse missed; new multi-fallback detector + **adaptive units (kbps/Mbps)**.
- **FIX: "Radio: offline" misread** — dumpsys output cached wrongly on some devices; now 3-second shared cache + prop fallback + numeric network-type mapping.
- **FIX: Termux menu exited after applying** — menu now **stays open**, refreshes panel, keeps you in control.
- **NEW: Termux big AMBERLYST art** on interactive launch.
- **NEW: Bold Termux invite box** at the end of Action apply.
- **NEW: apply receipts** — every apply writes a receipt line; `warpnet bench` receipts unchanged.
- **NEW: Snapdragon redirect** — flashing on SD fails safe, waits 5s, and points to [WarpNet-SD](https://github.com/Alchemiisst/WarpNet-SD).
- **NEW: codename system** — v1.0.0 = **Phantom**.

## v1.0 (2026-08-07)
- First public build: MTK hard gate, 4 modes, BBR+fq, RPS/XPS steering, 12MB BDP buffers, QUIC-fed UDP, ECN, Smart Reconnect L1-L3, Action menu + Termux CLI, AMBERLYST flash flow.

## v1.0.0 "Phantom" — hotfix 2 (2026-08-08)
- **CRITICAL FIX: "engine busy" after first apply** — boot daemon silently inherited the engine lock fd and held it forever. Lock fd now explicitly closed at daemon spawn (`9>&-`); lock system upgraded to a 15s self-healing wait; eunlock actually closes the fd now. Mode switching is deadlock-proof.
- **FIX: flash loading bar spam** — the 15→40→65→88→100% re-print saga is gone. Flash now narrates one evolving line (mixing alchemy → charging cores → sealing engine) and prints the bar ONCE.
- **NEW: mode picker look** — "cursor" text deleted; selection shows as a clean `→` arrow gliding through the 4-mode list with `[ACTIVE]` pinned to the live mode (blank-line framed, exactly per design mock).
- **FIX: Telegram didn't open after flashing** — full-path `/system/bin/am` + wake key + https→tg:// scheme fallback + honest fallback message.
- **FIX: daemon lost burst state** — step-down receipt + mode file always written.
- versionCode 11 → 12 (update detection).

## v1.0.0 "Phantom" — hotfix 3 (2026-08-08)
- **Menu reverted to the proven single-line style** (`cursor ❯ N. Mode`) — one line per press, zero redraw spam.
- **POWER press no longer kills the screen** — kernel wakelock held while the selector is open (`/sys/power/wake_lock`), released right before apply.
- **WarpNet++ burst time-limit REMOVED** — ∞ by default, stays until you switch. Timed window still available: `warpnet burst-min N` (0 = no limit).
- **FIX: Termux mode-switch crash** — robust tty read (works under `su -c warpnet` where /dev/tty may be absent), daemon-lock hardening, full error shielding.
- **NEW: official WarpNet banner** (module card banner.png for KernelSU/MMRL + GitHub logo).
- versionCode 12 → 13.

## v1.0.0 "Phantom" — hotfix 4 (2026-08-08)
- **NEW: banner v2 — full-bleed module-card art** — transparent-extracted WarpNet wordmark on an icy warp-streak canvas (giant faded ghost mark, cyan accent underline, `M T K` tag). Replaces the white-box slab from hotfix 3. Renders as the card background in KernelSU-Next / MMRL-style managers, EnCorinVest-style.
- **FIX: GitHub `logo.png` is now transparent** — no more white rectangle on GitHub dark theme.
- versionCode 13 → 14 (flash the new zip or let your manager offer the update).

## v1.0.0 "Phantom" — hotfix 5 (2026-08-08)
- **NEW: in-app update checks** — `updateJson` wired into `module.prop`; root managers with updateJson support (KernelSU-Next / MMRL / Magisk forks) flag **Update available** on the module card the moment a new build ships. Update manifest lives at [`update.json`](update.json) in the repo root.
- **NEW: ANCL v1.0 copyright headers** stamped into all 12 engine scripts.
- versionCode 14 → 15.
