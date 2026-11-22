# Memory Brain

A shared notebook for Kevin Durkin and the bots that help him.

This GitHub repo is an [Obsidian](https://obsidian.md/) vault. You open the folder and the notes are there. Each bot adds what it learned to that day's note. Git keeps the history, so a lesson is not stuck inside one chat.

Nothing here is a program you have to build or run. The checks below are the only automation.

## Open it in Obsidian on a Mac

You need two things: the folder on your Mac, and Obsidian pointed at that folder.

### Get the folder

**GitHub Desktop (the simple way)**

1. Install [GitHub Desktop](https://desktop.github.com/) and sign in to GitHub.
2. If this repo is private, sign in with an account that is allowed to see it.
3. Choose **File → Clone repository**.
4. Pick `durkin7/memory-brain`, or paste `https://github.com/durkin7/memory-brain`.
5. Choose where to save it, then click **Clone**.

**From inside Obsidian**

1. Install [Obsidian](https://obsidian.md/) and open it once.
2. Go to **Settings → Community plugins** and turn **Restricted mode** off.
3. Choose **Browse**, search for **Git** (the plugin by Vinzent), install it, and turn it on.
4. Press **Command + P**. That opens the command palette.
5. Run **Git: Clone an existing remote repo**.
6. Paste `https://github.com/durkin7/memory-brain` and choose an empty folder.

### Open the folder as a vault

1. Open Obsidian.
2. Click **Open folder as vault**.
3. Choose the `memory-brain` folder you just cloned. It is the folder that contains this README.
4. If Obsidian asks you to trust the vault, choose **Trust author and enable plugins**.

The left sidebar should show `00-Inbox`, `Daily`, `Bots`, `People`, `Projects`, `Lessons`, `Templates`, and `Attachments`.

Today's starter note is `Daily/2026-11-22.md`. On a later day, press **Command + P** and run **Daily notes: Open today's daily note**. Obsidian creates `Daily/YYYY-MM-DD.md` from `Templates/Daily Note` and fills in the date.

## How bots add notes

1. Open today's file in `Daily/`.
2. Paste a block from `Templates/Bot Entry` at the bottom. In Obsidian: **Command + P → Templates: Insert template → Bot Entry**.
3. Change `## Bot name` to the bot's own name.
4. Fill in **What I learned**, **Decisions**, **Open questions**, and **Lesson to keep**.
5. When you mention a person or a project, link the note with double brackets, like `[[Jane Doe]]` or `[[Website Redesign]]`.
6. If a lesson should outlast today, also add a short note in `Lessons/` and link it.

The full rules, in plain language, are in [CONTRIBUTING-BOTS.md](CONTRIBUTING-BOTS.md). Bots should follow that file. Add to your own section only. Do not edit another bot's words.

## What the secret check does

Notes in this vault must not contain passwords, API keys, or tokens. Two checks look for them.

**On GitHub.** Every push and every pull request runs [gitleaks](https://github.com/gitleaks/gitleaks) (version 8.30.1). The workflow is `.github/workflows/gitleaks.yml`. It uses the extra rules in `.gitleaks.toml` plus gitleaks' built-in rules for known key and token shapes. If it finds a secret, the check fails and that change should not be merged. Look at the **Actions** tab and open **Secret scan** to see the result.

**On your Mac, before the commit is saved.** `.pre-commit-config.yaml` runs gitleaks on the files you are about to commit. One-time setup, in Terminal, from this folder:

```bash
brew install pre-commit
pre-commit install
```

The first commit after that can take a minute, because pre-commit downloads gitleaks. Later commits are quick. If the check complains, take the secret out of the note and commit again. Do not skip the check.

`.gitignore` also tells git to ignore `.env` files, key files (`.pem`, `.key`, `id_rsa`), and a few Obsidian files that change on each computer (workspace layout and cache). That ignore list is a convenience. The gitleaks scan is the real check, because a key pasted into a note is still just text.

Card numbers, street addresses, and phone numbers are banned too. The writing rules are in [CONTRIBUTING-BOTS.md](CONTRIBUTING-BOTS.md). Keep those in a password manager or a private address book, not in this vault.

If a secret was already pushed, change that password or key. It is exposed even after you delete the line, because git keeps the old commit.

## Folders

- `00-Inbox/` — a note you have not sorted yet
- `Daily/` — one note per day, named `YYYY-MM-DD`
- `Bots/` — who each bot is and what it does
- `People/` — one note per person
- `Projects/` — one note per project
- `Lessons/` — a lesson worth keeping after the day is over
- `Templates/` — the starting points for a daily note and a bot entry
- `Attachments/` — images and files pasted into notes

Each folder has a short README that says the same thing in a sentence or two.
