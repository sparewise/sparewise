
# Sparewise

Sparewise runs on the person's own Windows PC as an MCP server (`sparewise.exe mcp`).
Everything it reports is measured on that PC, and it sends nothing anywhere.

## Which tool answers what

| The person asks | Call |
|---|---|
| Why is my drive full? Is it filling up? | `why_filling`, then `can_it_come_back` |
| What is using my space? | `scan` (caches, tools, AI models), `drive_map` (every folder) |
| What is this folder? Can I delete it? | `explain_folder` with the full path |
| How much of my drive could come back if lost? | `can_it_come_back` |
| Are my files backed up? | `backup_status` |
| Free up space | `plan_free_space` (caches that rebuild) or `plan_compress` (shrinks unused folders, deletes nothing), then `apply_plan` |
| Which programs take space? | `installed_apps` |
| Big Windows files, Recycle Bin, browser data | `windows_items` |
| Old iPhone or iPad backups | `phone_backups` |
| OneDrive taking space | `onedrive_space` |
| Installers already used | `used_installers` |
| Games and how to remove them | `installed_games` |
| Old Node and Java versions | `old_runtimes` |
| Apps that need updating | `app_updates` |
| Browser extensions | `browser_extensions` |
| Local AI models | `ai_models` |
| Turn off startup programs, clean Windows junk, uninstall npm tools, WSL disks | `system_actions`, then `plan_system_actions` and `apply_system_actions` |
| What is using my disk / why is it full (start here) | `storage_overview` |
| Free a set amount ("free 20 GB") | `free_space_goal` |
| A quick health summary of this PC | `machine_status` |
| Why is my PC slow? Make it faster | `why_slow`, then each of its `nextSteps` (an existing tool, or `personDecides`) |
| What is using memory? | `memory_report` |
| Which of many PCs need attention (each writes its status to a shared folder) | `fleet_status` |
| What did agents change? | `system_action_runs`; put back with `undo_system_actions` |
| The same npm or Python package in many projects | `node_copies`, `python_copies` (with the projects folder) |
| Old projects taking space; what to hibernate | `idle_projects`; the person hibernates (`sparewise hibernate` or the window) |
| Git repositories to pack | `git_loose` |
| Model files copied into projects | `project_models` |
| Old VS Code, Cursor, Windsurf extensions | `editor_leftovers` |

## Rules

- Read and plan freely. Every change goes plan, then apply. `apply_plan` runs only if the
  person's policy allows unattended changes that can be undone; otherwise give them the
  command it returns, to run themselves.
- Nothing an agent can do is permanent. Changes can be undone with `undo_run`.
- `apply_system_actions` runs only the kinds the person listed under `unattendedActions`.
  Always pass a `reason` in one plain sentence: the person reads it later next to your name.
- Never tell the person their own files are safe to delete. `OnlyHere` means not known to
  exist anywhere else.
- `NoneSeen` from `backup_status` means no backup this tool can see. It is not proof that
  there is no backup.
- If `explain_folder` returns `known: false`, say the tool does not know that folder.
  Do not guess.
- Never offer to "clean" memory or the registry: it does not make a PC faster. For which startup
  programs to turn off, ask the person; do not pick them.
- Programs, AI models and phone backups are removed by the person with each app's own
  route; the tools return it. Pass it on, do not improvise another way.

## Privacy

Tool results become part of the conversation with the AI provider. Results summarise the
person's own folders rather than listing them; `drive_map`, `large_media` and
`downloads_report` do show folder and file names, so use them only when the person asks.
