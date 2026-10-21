---
type: readme
title: TheDeck
description: Windows installation for people and agents, separate profiles and persistent A2A exchanges.
---

# TheDeck

**Keep your projects in view and your tools close.**

TheDeck brings repositories, worktrees, pull requests, agent sessions, terminals and notes into one Windows desktop application. TheTasks is the standalone conversational task runtime. TheDeck Capture is the independent screenshot companion.

This public repository distributes the applications and this guide. The development source code is not published here. These applications are independent projects, not official OpenAI or Anthropic products.

## Download

Delivery **0.3.0** — Windows x64 (Intel/AMD 64-bit).

| Application | Download | What you get |
| --- | --- | --- |
| TheDeck 0.3.0 | [TheDeck Windows installer](https://github.com/zeuzere/TheDeck/releases/download/v0.3.0/TheDeck-Setup-0.3.0-win-x64.exe) | Desktop application, local service and optional Capture companion. |
| TheTasks 1.1.0 | [TheTasks standalone executable](https://github.com/zeuzere/TheDeck/releases/download/v0.3.0/TheTasks-1.1.0-win-x64.exe) | Conversational task runtime and CLI/MCP, configured separately in TheDeck. |
| TheDeck Capture 0.1.2 | [Capture standalone executable](https://github.com/zeuzere/TheDeck/releases/download/v0.3.0/TheDeck-Capture-0.1.2-win-x64.exe) | Screenshot tool that works without TheDeck; independent product version. |
| TheDeck-A2AService 0.1.0 | [A2A Service standalone executable](https://github.com/zeuzere/TheDeck/releases/download/v0.3.0/TheDeck-A2AService-0.1.0-win-x64.exe) | Independent persistent mailbox between TheDeck profiles. |

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
- Maximize a terminal within its group and restore saved side-by-side groups.
- Open Workspace web tabs beside terminals, with Web, detected Links and Notes in a shared pane.
- Select provider-reported models and reasoning effort when starting Claude or Codex terminals.
- Control Workspaces, terminals and web tabs through the CLI or TheDeck MCP server, including literal terminal input.
- Save selected terminal excerpts as bookmarks.
- Configure external MCP connections and automation hooks when needed.
- Chat with Tasks in expandable dialogs without changing the desktop layout.
- Dismiss current Task notifications individually or together.
- Report bugs or suggest ideas for all three products from About.
- Find keyboard help under **Shortcuts**, and product information under **Settings → About**.

Install **Git** for repository features and **GitHub CLI (`gh`)** for GitHub features. Sign in through `gh auth login`. Install and authenticate **Codex CLI** or **Claude Code** separately to use their terminals. VS Code, Windows Terminal and Docker are optional tools for the features that use them. The application does not include those tools or their accounts.

Application data is stored under `%APPDATA%\TheDeck`. Workspaces refer to your existing project folders; project files are not copied into this repository. Updates preserve application data. Close active terminal sessions before exiting or updating TheDeck.

## Start TheTasks

Save the standalone executable in a permanent folder. In TheDeck, configure its
absolute executable path under **Settings → Tasks**. The executable includes its
.NET runtime and does not require a separate .NET installation.

Run it from a terminal with `--help` for standalone runtime, Task and MCP commands.
Agent execution requires your separately installed and signed-in Codex CLI or
Claude Code. Each Task retains its own provider session across turns. Task data
is separate from TheDeck under `%LOCALAPPDATA%\TheTasks\profiles\default` unless
an explicit data directory is selected. Closing a CLI client does not cancel an
independently running Task runtime.

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

## For Claude, Codex and other installation agents

This README is the complete binary-installation entry point. **Do not clone this
repository to build the application:** it contains distribution documentation,
not development sources. Install the latest non-prerelease Windows x64 release
from `zeuzere/TheDeck`. Node.js and the .NET SDK/runtime are not prerequisites.
Use direct executable launches with argument lists, not shell command strings.

1. Confirm Windows x64 and inspect existing installation/processes. Do not stop
   an active TheDeck or its terminals to update it. If replacement would interrupt
   work, finish downloading/verifying and report that installation must wait.
2. Retrieve `https://api.github.com/repos/zeuzere/TheDeck/releases/latest`.
   Select exactly one matching asset per product; versions are independent.
   Save downloads permanently, verify the GitHub asset's `sha256:` digest, then
   execute. If the digest is unavailable, stop before execution and obtain the
   release's published SHA-256 through a trusted channel.
3. Install TheDeck per user, keep standalone tools at stable absolute paths,
   verify Control, then configure only requested optional features.

PowerShell example for download and verification (requires outbound HTTPS;
no API key or GitHub sign-in for these public downloads):

```powershell
$ErrorActionPreference = 'Stop'
if ($env:OS -ne 'Windows_NT' -or [Runtime.InteropServices.RuntimeInformation]::OSArchitecture -ne 'X64') {
    throw 'This distribution requires Windows x64.'
}
$release = Invoke-RestMethod 'https://api.github.com/repos/zeuzere/TheDeck/releases/latest' -Headers @{ 'User-Agent' = 'TheDeck-Installer' }
$cache = Join-Path $env:LOCALAPPDATA "TheDeck-Downloads\$($release.tag_name)"
$installDir = Join-Path $env:LOCALAPPDATA 'Programs\TheDeck'
$toolsDir = Join-Path $env:LOCALAPPDATA 'Programs\TheDeck-Tools'
New-Item -ItemType Directory -Force $cache, $toolsDir | Out-Null
$patterns = @{
    Deck = '^TheDeck-Setup-\d+\.\d+\.\d+-win-x64\.exe$'
    Tasks = '^TheTasks-\d+\.\d+\.\d+-win-x64\.exe$'
    Capture = '^TheDeck-Capture-\d+\.\d+\.\d+-win-x64\.exe$'
    A2A = '^TheDeck-A2AService-\d+\.\d+\.\d+-win-x64\.exe$'
}
$downloads = @{}
foreach ($product in $patterns.Keys) {
    $assets = @($release.assets | Where-Object { $_.name -match $patterns[$product] })
    if ($assets.Count -ne 1) { throw "Expected one $product asset in $($release.tag_name)." }
    $asset = $assets[0]
    if ($asset.digest -notmatch '^sha256:([a-fA-F0-9]{64})$') { throw "Missing SHA-256 for $($asset.name)." }
    $expectedHash = $Matches[1]
    $path = Join-Path $cache $asset.name
    Invoke-WebRequest $asset.browser_download_url -OutFile $path -UseBasicParsing
    if ((Get-FileHash -LiteralPath $path -Algorithm SHA256).Hash -ine $expectedHash) { throw "Digest mismatch: $path" }
    $downloads[$product] = $path
}
```

After confirming the existing application can be updated, install silently.
NSIS `/D=ABSOLUTE_INSTALL_DIR` must be the **last** argument. Do not add another
argument after it. Check the installer exit code and installed executable.
Do not overwrite a running standalone tool; defer its update until it is idle.
See the [NSIS installer command-line reference](https://nsis.sourceforge.io/Docs/Chapter3.html#installerusage).

```powershell
if (Get-Process -Name TheDeck -ErrorAction SilentlyContinue) { throw 'TheDeck is running; preserve its terminals and defer installation.' }
if (Get-Process -Name thetasks, TheDeck-A2AService, TheDeck-Capture, TheDeck.Capture -ErrorAction SilentlyContinue) { throw 'A standalone tool is running; preserve its work and defer replacing it.' }
$installer = Start-Process -FilePath $downloads.Deck -ArgumentList @('/S', "/D=$installDir") -WindowStyle Hidden -Wait -PassThru
if ($installer.ExitCode -ne 0) { throw "Installer failed: $($installer.ExitCode)" }
$deck = Join-Path $installDir 'TheDeck.exe'
$control = Join-Path $installDir 'resources\control\TheDeck.Control.exe'
if (!(Test-Path -LiteralPath $deck) -or !(Test-Path -LiteralPath $control)) { throw 'Installed application or Control host not found.' }
Copy-Item -LiteralPath $downloads.Tasks -Destination (Join-Path $toolsDir 'thetasks.exe')
Copy-Item -LiteralPath $downloads.Capture -Destination (Join-Path $toolsDir 'TheDeck-Capture.exe')
Copy-Item -LiteralPath $downloads.A2A -Destination (Join-Path $toolsDir 'TheDeck-A2AService.exe')
& $control --help
$profile = Join-Path $env:APPDATA 'TheDeck'
& $control --user-data $profile --command workspace.list --json
if ($LASTEXITCODE -ne 0) { throw 'TheDeck Control verification failed.' }
```

Control returns `{ "ok": true, "result": ... }`; nonzero exit codes or `ok:false`
mean failure. A fresh profile has an empty Workspace list. Control may start the
matching installed desktop when needed. Do not erase an existing profile to get
an empty list. Record the installed versions, paths and verification results.

Git, GitHub CLI, Codex CLI and Claude Code are optional dependencies for their
respective features. Install/configure them only as needed. Authentication may
require the person's browser or interactive login: do not invent credentials,
reuse another user's account, or request an API key just to install TheDeck.
If Windows or endpoint protection blocks execution, report the block instead of
disabling or bypassing protection.

## Two TheDeck instances on one computer

Use **one installation with two separate profiles**, not two installers. Both
`--control-desktop` and an absolute `--user-data` path are required for this direct
desktop launch. Reopening the same profile focuses its existing instance.

```powershell
$deck = Join-Path $env:LOCALAPPDATA 'Programs\TheDeck\TheDeck.exe'
$control = Join-Path $env:LOCALAPPDATA 'Programs\TheDeck\resources\control\TheDeck.Control.exe'
$deck1 = Join-Path $env:LOCALAPPDATA 'TheDeck-Profiles\Deck1'
$deck2 = Join-Path $env:LOCALAPPDATA 'TheDeck-Profiles\Deck2'
Start-Process -FilePath $deck -ArgumentList @('--control-desktop', '--user-data', "`"$deck1`"")
Start-Process -FilePath $deck -ArgumentList @('--control-desktop', '--user-data', "`"$deck2`"")
```

Each profile has its own database, Workspaces, settings, layout and browser data.
Keep these same paths on future launches. Do not copy a configured profile to
make another identity: A2A node IDs persist inside profiles and must be distinct.
The normal unqualified launch still uses `%APPDATA%\TheDeck`.

Profiles do not isolate Windows accounts, project files or provider credentials.
Codex/Claude authentication remains shared at the Windows-user level. To separate
Tasks too, configure different TheTasks `--data-dir` paths under **Settings →
Tasks** in each profile; separate TheDeck profiles alone do not split TheTasks'
default runtime data.

## Connect both profiles through TheDeck-A2AService

This first version provides **manual requests and replies**, retained in SQLite.
It does not launch models, wake agents or automatically send follow-up requests.
Its A2A 1.0 JSON-RPC interface is an experimental subset, not full protocol
compliance. TheDeck uses the service's own REST mailbox interface.

The service is a separate process; closing TheDeck does not stop it. It is not
installed as a Windows service and does not configure automatic startup. Start
it once, with a permanent data directory, and check health before connecting:

```powershell
$service = Join-Path $env:LOCALAPPDATA 'Programs\TheDeck-Tools\TheDeck-A2AService.exe'
$serviceData = Join-Path $env:LOCALAPPDATA 'TheDeck-A2AService'
& $service --help
$health = $null
try { $health = Invoke-RestMethod 'http://127.0.0.1:17190/health' -TimeoutSec 2 } catch { }
if ($health -and $health.service -ne 'TheDeck-A2AService') { throw 'This port belongs to another service.' }
if (!$health) {
    if (!(Get-Process -Name TheDeck-A2AService -ErrorAction SilentlyContinue)) {
        Start-Process -FilePath $service -WindowStyle Hidden -ArgumentList @('--url', 'http://127.0.0.1:17190', '--data-dir', "`"$serviceData`"")
    }
    for ($attempt = 0; $attempt -lt 20 -and !$health; $attempt++) {
        Start-Sleep -Milliseconds 250
        try { $health = Invoke-RestMethod 'http://127.0.0.1:17190/health' -TimeoutSec 2 } catch { }
    }
}
if (!$health -or $health.service -ne 'TheDeck-A2AService' -or $health.status -ne 'ok') { throw 'A2A health verification failed; inspect the existing process before restarting.' }
$health
```

Health must report `status:ok`, `service:TheDeck-A2AService`, `version:0.1.0`.
Allow a brief startup interval before retrying health. Never launch a competing
instance after merely one timeout. The default address is loopback. This requested
prototype has **no authentication**: keep it local/trusted; installation does not
open firewall rules or expose it to the Internet.

Configure both running profiles through Control, without manual UI setup:

```powershell
& $control --user-data $deck1 --command a2a.configure --enabled true --service-url 'http://127.0.0.1:17190' --display-name 'Deck 1' --json
& $control --user-data $deck2 --command a2a.configure --enabled true --service-url 'http://127.0.0.1:17190' --display-name 'Deck 2' --json
& $control --user-data $deck1 --command a2a.refresh --json
$state1 = (& $control --user-data $deck1 --command a2a.state --json | ConvertFrom-Json)
$state2 = (& $control --user-data $deck2 --command a2a.state --json | ConvertFrom-Json)
if (!$state1.ok -or !$state2.ok -or !$state1.result.connected -or !$state2.result.connected) { throw 'Both A2A profiles must connect.' }
$recipientId = $state2.result.nodeId
if ($state1.result.nodeId -eq $recipientId) { throw 'Profiles must have different identities.' }
& $control --user-data $deck1 --command a2a.open --json
& $control --user-data $deck2 --command a2a.open --json
```

**Offline-delivery verification:** first register both profiles as above. Close
Deck 2 gracefully after ensuring its terminals may close. Do not kill it or send
further Control commands to that profile while testing its offline state, because
Control can reopen it. Deck 1 can send to the already known, offline recipient:

```powershell
$requestId = [guid]::NewGuid().ToString()
& $control --user-data $deck1 --command a2a.send --exchange-id $requestId --recipient-id $recipientId --subject 'Offline delivery test' --text 'Please confirm receipt after reopening Deck 2.' --json
```

The CLI calls the service's request ID `--exchange-id`; the global
`--request-id` option is reserved for Control transport retries and is separate.
Keep `$requestId` and the identical content if retrying an uncertain send. The
service queues one request, even when the recipient is offline. Restart Deck 2
with **the same** profile path, refresh, then reply once:

```powershell
Start-Process -FilePath $deck -ArgumentList @('--control-desktop', '--user-data', "`"$deck2`"")
& $control --user-data $deck2 --command a2a.refresh --json
& $control --user-data $deck2 --command a2a.state --json
$replyId = [guid]::NewGuid().ToString()
& $control --user-data $deck2 --command a2a.reply --exchange-id $requestId --reply-id $replyId --text 'Received after reopening Deck 2.' --json
& $control --user-data $deck1 --command a2a.refresh --json
& $control --user-data $deck1 --command a2a.state --json
```

Verify that this request is `completed` and contains that reply in Deck 1. Keep
the same `$replyId` and text on an uncertain retry. The sender can cancel a
pending request with `a2a.cancel --exchange-id UUID`; finished requests cannot be
reopened. Requests and responses survive service restart with the same data
directory. Closing the service makes delivery unavailable until it restarts.

An installation agent should finish by reporting product versions, executable
and profile paths, service health, distinct node IDs, both connection results,
and the request ID/status demonstrating offline receipt and the returned reply.
If preserving active work prevents closing Deck 2, report that specific remaining
verification instead of claiming the offline test passed.

## Release notes and support

The executables are not code-signed. Release notes identify the checks performed and any known limitations; verify downloaded files against the SHA-256 hashes included there.

For an issue, include the application name, version from About, Windows version and steps to reproduce. Avoid posting private project content, credentials or personal screenshots. [Report an issue](https://github.com/zeuzere/TheDeck/issues).

In TheDeck, **Settings → About → Signaler un bug / Proposer une idée** offers
forms for TheDeck, TheTasks and Capture. All three use TheDeck's GitHub Issues.
Choose a signed-in GitHub CLI account, review the text, then send. No logs or
screenshots are attached automatically.
