---
type: readme
title: TheDeck
description: Windows downloads and getting started with TheDeck and Capture.
---

# TheDeck

**Keep your projects in view and your tools close.**

TheDeck brings repositories, worktrees, pull requests, agent sessions, terminals and notes into one Windows desktop application. TheDeck Capture is its independent screenshot companion.

This public repository distributes the applications and this guide. The development source code is not published here. Both applications are independent projects, not official OpenAI or Anthropic products.

## Download

Version **0.1.0** — Windows x64 (Intel/AMD 64-bit).

| Application | Download | What you get |
| --- | --- | --- |
| TheDeck | [TheDeck Windows installer](https://github.com/zeuzere/TheDeck/releases/download/v0.1.0/TheDeck-Setup-0.1.0-win-x64.exe) | Desktop application, local service and optional Capture companion. |
| TheDeck Capture | [Capture standalone executable](https://github.com/zeuzere/TheDeck/releases/download/v0.1.0/TheDeck-Capture-0.1.0-win-x64.exe) | Screenshot tool that works without TheDeck. |

See [all releases and release notes](https://github.com/zeuzere/TheDeck/releases). Executables are distributed through Releases; GitHub's automatic source archives contain only this public distribution repository, not the application's development source.

## Start TheDeck

1. Download and run the TheDeck installer. Choose the installation folder when prompted.
2. Open **TheDeck** from the Start menu. Pin this installed application to the taskbar if desired.
3. Add a Workspace and select the folder containing your local repositories. Configure a worktrees folder if you use one.
4. Open Settings to choose your terminal providers, Notes folder and optional integrations.

The installer includes Electron, the local service and its .NET runtime. You do not need Node.js, the .NET SDK or development build tools to run the installed application.

### Features

- Browse repositories and worktrees and open their folders, editor or terminals.
- Follow GitHub pull requests using your locally authenticated GitHub CLI.
- Browse supported local Codex and Claude Code sessions.
- Keep terminals arranged in groups, with Notes and quick questions alongside your work.
- Save selected terminal excerpts as bookmarks.
- Configure external MCP connections and automation hooks when needed.
- Find keyboard help under **Shortcuts**, and product information under **Settings → About**.

Install **Git** for repository features and **GitHub CLI (`gh`)** for GitHub features. Sign in through `gh auth login`. Install and authenticate **Codex CLI** or **Claude Code** separately to use their terminals. VS Code, Windows Terminal and Docker are optional tools for the features that use them. The application does not include those tools or their accounts.

Application data is stored under `%APPDATA%\TheDeck`. Workspaces refer to your existing project folders; project files are not copied into this repository. Updates preserve application data. Close active terminal sessions before exiting or updating TheDeck.

## Start TheDeck Capture

1. Save the standalone executable in a folder you want to keep and double-click it.
2. Find its camera icon in the Windows notification area, near the clock; it may be inside the hidden-icons menu.
3. Right-click the icon to capture an area or window, copy the last image or path, open About, or quit.

The standalone executable includes its runtime and needs no installer or separate .NET installation. It saves screenshots in **Pictures\TheDeck Capture** by default.

| Control | Action |
| --- | --- |
| Hold **Left Alt + Right Alt** | Select an area and copy the captured image. |
| Hold **Left Ctrl + Right Ctrl** | Select an area and copy the saved image's path. |
| **Space** during selection | Switch between area and window selection. |
| **Esc** or right-click during selection | Cancel. |

Both capture shortcuts save a PNG. The tray menu can swap their image/path behavior and choose the clipboard format for captures started from the menu. Only one Capture instance runs per Windows session.

TheDeck also includes Capture: enable **Settings → General → Screenshot capture → Start Capture with TheDeck** to launch it on future starts. This option is off by default. The bundled companion saves to `%APPDATA%\TheDeck\screenshots` and keeps running after TheDeck closes; quit it through its tray menu. It does not configure Windows-login startup.

## Release notes and support

This is the first Windows x64 release. The executables are not code-signed. Release notes identify the checks performed and any known limitations; verify downloaded files against the SHA-256 hashes included there.

For an issue, include the application name, version from About, Windows version and steps to reproduce. Avoid posting private project content, credentials or personal screenshots. [Report an issue](https://github.com/zeuzere/TheDeck/issues).
