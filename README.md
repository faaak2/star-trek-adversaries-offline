# Star Trek Adversaries — Offline

Play Star Trek Adversaries again now that its servers are gone. A small program runs a
server on your own PC and points the game at it. Windows only.

You need your own copy of the game on Steam; this does not include it. It is an unofficial
fan project, not affiliated with the game's publisher or the Star Trek rights holders.

## How to run it

1. Install Star Trek Adversaries from Steam. Don't start it yet.
2. Download `StarTrekAdversariesOffline.exe` from the
   [latest release](https://github.com/faaak2/star-trek-adversaries-offline/releases/latest).
3. Run it. Windows will probably warn you first, see [below](#windows-warns-about-the-exe).
   It finds the game on its own (if it can't, it asks you to pick the game's folder) and
   prepares it.
4. A small window says **Game patched - server running**. Now start the game from Steam and
   log in with any username and password.
5. Keep it running while you play. Closing its window hides it to the system tray; to stop
   it, right-click its tray icon and choose **Quit**.

Good to know:

- Log in with the same username every time. A different name replaces your account,
  including its collection and decks.
- Your progress is saved in `%LOCALAPPDATA%\StarTrekAdversariesOffline`.
- If Steam verifies or updates the game's files, run the exe again.
- To undo everything, run `StarTrekAdversariesOffline.exe --restore` from a terminal, or
  use Steam's *Verify integrity of game files*.

## Windows warns about the exe

Windows will show "Windows protected your PC" when you run the exe, and some antivirus tools
may flag it. That is because the exe is not code-signed. A signing certificate costs money
every year, and this is a free project, so it ships without one. The warning means "unknown
publisher", not that anything was detected.

To run it anyway, click **More info**, then **Run anyway**.

What the exe does:

- It edits one file in your game folder, `GameSparks.Api.dll`, so the game connects to your
  own PC instead of the dead servers. The original stays beside it as
  `GameSparks.Api.dll.orig`, and `--restore` puts it back.
- It runs a server that listens on `127.0.0.1` only and makes no outgoing network
  connections.
- Apart from the game's `Managed` folder, it writes only to
  `%LOCALAPPDATA%\StarTrekAdversariesOffline`. It reads Steam's install path from the
  registry to find the game.

Each release lists the SHA-256 of the exe. To check your download, run
`Get-FileHash StarTrekAdversariesOffline.exe` in PowerShell and compare.

If your antivirus quarantines it, that is a false positive on a program that edits a game
file; add an exception if you trust it.
