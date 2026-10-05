# Sparewise

**See why your Windows drive is full, and free space safely.**

Sparewise finds the space developer and AI tools leave behind (package caches,
local AI models, Docker and WSL disks, browser and editor caches) as well as
ordinary Windows clutter. It tells you what each item is, whether it comes back by
itself, and frees it only when you say so. Anything it moves can be put back.

**[Download the latest version](../../releases/latest)**: Windows 10 and 11, x64 and ARM.

## Why people use it

- **One answer to "why is my drive full?"** The drive in plain parts: what rebuilds itself, what can be downloaded again, what is Windows, and what exists only on this PC.
- **"Free 20 GB"**: picks the smallest set of safe caches that reaches your goal.
- **Nothing lost by mistake.** Every change goes to the Recycle Bin or an undo window. Sparewise never empties the bin and never deletes permanently.
- **Honest results.** It measures what was actually freed. If a program had files open, it says which files stayed and why.
- **No admin rights needed**, and no account.
- **Private.** No telemetry; nothing is sent anywhere.
- **Works with AI assistants.** Built-in MCP server for Claude, Cursor, VS Code, Claude Code and Codex. Agents can read and plan; they change the disk only within limits you set, and never permanently.

## Install

| | |
|---|---|
| **Installer** (recommended) | `Sparewise-win-Setup.exe`: installs for you only, no admin prompt, updates itself |
| **Portable** | `Sparewise-win-x64.zip` or `Sparewise-win-arm64.zip`: unzip and run `Sparewise.App.exe` |

Sparewise is not code-signed yet, so Windows may say **"Windows protected your PC"**.
Choose **More info → Run anyway**. Every release lists SHA-256 checksums, so you can
check that a download is the genuine one.

## Help and feedback

- **Found a problem?** Choose *Report a problem* in the app, or [open an issue](../../issues/new). It fills in the version for you, and nothing about your PC is sent.
- **Questions and ideas:** [Discussions](../../discussions).

## License

Sparewise is free to use. The source code is not public. See [LICENSE](LICENSE).
