# Security and privacy

Sparewise changes files on your computer, so how it does that, and what it never does, is set out
here as plainly as possible.

## Reporting a problem

Please report security problems privately, not in a public issue:
use **[Report a vulnerability](https://github.com/sparewise/sparewise/security/advisories/new)** on GitHub (private: only you and the developer see it).
Include what you saw, the version (Settings or `sparewise --version`), and steps to reproduce on test
files. We aim to reply within a few days and will credit you if you wish.

## What Sparewise sends over the network

No telemetry, no account, no analytics. It goes online only in these places:

| When | Where it connects | What it sends |
|---|---|---|
| Once a day after you open the window (turn off in Settings), and when you press **Updates** | GitHub releases of Sparewise (github.com, objects.githubusercontent.com) | A normal download request, with no ID or data about your PC |
| You ask the drive map what an unknown folder is, with Ollama installed | Ollama on your own PC (127.0.0.1); nothing leaves the PC | The folder's name and the names inside it |
| You press **Check for app updates** | winget, Windows' own package tool, which uses Microsoft's sources | What winget itself sends |
| An npm tool is put back after an uninstall | npm's registry, through npm itself | What npm itself sends |
| You press **Report a problem** | Opens your browser on a new-issue page | Only what you choose to type |

A test (`NetworkGuardTests`) fails the build if network code appears anywhere else.

Whatever a tool returns to an AI agent you connect (folder names, sizes) becomes part of that
agent's chat and goes to that agent's provider, like any file the agent reads. Sparewise itself
sends nothing to it.

## How changes are made safe

- **One path for every change.** Plan → confirmation (or policy) → each step checked again against
  the rules at the moment it runs → applied → measured → recorded in the audit log.
- **Deterministic rules decide what may be removed.** No AI model decides whether something is safe.
- **Nothing is deleted outright** by normal use: items go to the Recycle Bin, an undo window on the
  same drive, or are compressed in place (reversible). Permanent release needs a person at a console
  and is not available to agents.
- **Agents act only under your policy** (`%LocalAppData%\DevStorage\policy.json`): reversible changes
  up to a size cap, listed system actions, excluded folders. With no policy, nothing runs unattended.
- **Folders that are yours or Windows'** (Documents, Desktop, Downloads, profile templates, AppData of
  other accounts, Windows and program folders) are never offered for removal.
- **Keys and credentials are never removed** (.env, .pem, SSH keys, password vaults, .ssh, .aws and similar), and a folder holding one stays.
- **Links are not followed** (junctions, symbolic links, mount points).
- **Files in use are left in place** and reported, never forced.

## What the policy is not

The policy stops well-behaved agents and mistakes. It is not a security boundary against malicious
software already running as you, which could change files without Sparewise.

## Where Sparewise keeps its own files

`%LocalAppData%\DevStorage`: scan history (SQLite), plans, policy, audit log, the undo window and logs.
Nothing else is written outside the folders you ask it to clean.
