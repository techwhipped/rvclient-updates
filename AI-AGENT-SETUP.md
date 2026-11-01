# Install rVclient and fix problems with an AI agent's help

This file is written **for an AI agent** (Claude Code, Codex, Cursor, ...) helping a player install
the rVclient launcher for Rumbleverse, get into a match, and sort out problems when the game will
not start or crashes.

**How to use it:** open this file (or a folder containing it) in your agent and give it the prompt
at the end.

---

## 0. Ground rules for the agent

1. **Never download Rumbleverse from anywhere and never share game files.** The player needs their
   own copy. rVclient does not provide the game.
2. **Download rVclient only from this repository's [Releases](../../releases)** or the official
   rVclient website / Discord. Never from mirrors or re-uploads.
3. **Never paste or share the player's login, tokens or `rVclient.ini`.** Logs are fine to share
   with the rVclient team through a ticket.
4. **Do not turn off antivirus or add broad exclusions.** If Defender flags a file, check the file's
   MD5 against the release post and report the false positive to the rVclient team instead.
5. **Close the game before changing its files**, and ask the player first. Stop it **by its full
   path**, never by process name.
6. **Logs before fixes.** Read the logs in section 4 before suggesting anything.
7. Change one thing at a time, and say what you changed so it can be undone.

---

## 1. Install

1. Windows 10/11, 64-bit, with the player's own Rumbleverse install.
2. From the newest **`-stable`** release, download the launcher setup and run it. Check its MD5
   against the one in the release notes first.
3. Start rVclient, create an account / sign in, and let it find the game folder (or point it at the
   folder that contains `Rumbleverse\Binaries\Win64\RumbleverseClient-Win64-Shipping.exe`).
4. Press **PLAY**. The launcher puts its files next to the game on first Play. In the game: **Play >
   Game Modes** and pick a mode.

Releases tagged `-beta.N` are opt-in tests (Settings > Updates > *Try beta releases*). *Go back to
stable* undoes them.

## 2. Settings worth knowing

- **Settings > Graphics API: DirectX 11 or Vulkan.** On a PC with only Intel graphics the launcher
  starts on Vulkan; everywhere else on DirectX 11. If the game shows a black screen and closes, or
  crashes at start-up, **switching to the other one is the first thing to try** (the launcher
  swaps the files itself; start the game again afterwards).
- The launcher repairs a broken game settings file (`GameUserSettings.ini`) on start - a classic
  cause of a black screen.
- Region and server choice: the Servers / Region pages.

## 3. Common problems

| Symptom | Try, in this order |
|---|---|
| Black screen, then the game closes | switch Graphics API (section 2); update the graphics driver from Intel / NVIDIA / AMD; restart the PC |
| "Backend unavailable" in the launcher | internet / VPN / firewall blocking the launcher; wait a minute and retry - check the rVclient Discord for outages |
| Stuck searching for a match | the launcher's queue line says why it waits; try another mode or region |
| Defender removed a file | report it (rule 0.4); reinstall from the release page |
| No voice chat | Windows microphone privacy setting for the game; the launcher's voice settings |

## 4. Logs to read (and to attach to a ticket)

| What | Where |
|---|---|
| Launcher | `rVclient.log` in the launcher folder |
| Client mod | `RVClient_v1.log` next to the game exe (`Rumbleverse\Binaries\Win64\`) |
| The game | `%LOCALAPPDATA%\Rumbleverse\Saved\Logs\Rumbleverse.log` (and any crash folder in `Saved\Crashes\`) |
| Vulkan mode only | `RumbleverseClient-Win64-Shipping_d3d11.log` / `_dxgi.log` next to the game exe |

For a crash, the game log and `RVClient_v1.log` matter most - the launcher log alone rarely shows
why the game closed. Open a ticket in the launcher (or the rVclient Discord) with what happened,
when it started, and these files.

---

## Prompt to give your agent

> Read `AI-AGENT-SETUP.md` completely before doing anything and follow its ground rules at all
> times. Help me `<install rVclient | fix this problem: ...>`. My Rumbleverse install is at
> `<path to my game>`. Read the logs in section 4 first and tell me what they say before you change
> anything. Ask me before closing my game or changing any setting. Never download or share game
> files, and never touch my login details.
