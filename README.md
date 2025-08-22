# Obsidian Notes Vault

This repository contains my personal course notes, managed with [Obsidian](https://obsidian.md/) and backed up automatically to GitHub.

## Structure

Notes are organized by course, with one folder per class:

```
CMPE 180B Database Systems/
  2025-08-21 Thu – Week 1.md
  2025-08-27 Wed – Week 2.md
CMPE 180C Operating System Design/
  2025-08-20 Wed – Week 1.md
CMPE 252 AI & Data Engineering/
  2025-08-20 Wed – Week 1.md
```

- One file per class day  
- Files are named with the date (`YYYY-MM-DD`), weekday, and week number  
- Inside each note: topics, key points, code snippets, and references

## Obsidian Setup

- Vault name: Obsidian Vault
- Plugins used:
  - [Obsidian Git](https://github.com/denolehov/obsidian-git) → auto commit & push changes
  - (Optional) [Templater](https://github.com/SilentVoid13/Templater) → daily class templates
  - (Optional) [Dataview](https://github.com/blacksmithgu/obsidian-dataview) → auto course indexes

## GitHub Sync

This repo is synced in two ways:

1. Obsidian Git Plugin  
   - Auto-commit every 10 minutes while Obsidian is open  
   - Auto-push/pull on app open/close  

2. GitHub Actions (optional)  
   - Nightly backup at 3:15 AM PT  
   - Commits only if there are changes  

## Git Ignore Rules

Certain Obsidian configuration files are excluded from version control to keep the repo clean:

```
.obsidian/workspace.json
.obsidian/appearance.json
.obsidian/graph.json
.obsidian/app.json
.obsidian/core-plugins.json
.obsidian/community-plugins.json
.obsidian/plugins/
```

This ensures only Markdown notes and essential configs are tracked.

## Usage

- Clone this repo to your local machine
- Open the folder as a vault in Obsidian
- Notes will appear organized by course
- To add a new class day note:
  - Create a file inside the course folder named `YYYY-MM-DD Ddd – Week N.md`
  - Or use a Templater/QuickAdd command to auto-generate the structure

---

These notes are for personal study and archival purposes. Feel free to adapt this setup for your own coursework!

