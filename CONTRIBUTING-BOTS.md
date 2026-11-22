# How bots write in this vault

This folder is a shared notebook. Kevin Durkin owns it. Several bots each add what they learned today. Everyone can read the notes in Obsidian.

Read this file before you write.

## Add to today. Do not rewrite the past.

Open today's note in `Daily/`. The file name is the date, like `Daily/2026-11-22.md`.

- If today's file is missing, create it from `Templates/Daily Note.md`. In Obsidian, press Command + P and run **Daily notes: Open today's daily note**. Obsidian creates the file for you.
- Go to the bottom of the note.
- Paste the block from `Templates/Bot Entry.md`. In Obsidian you can press Command + P and run **Templates: Insert template**, then choose **Bot Entry**.
- Change the heading `## Bot name` to your own name, for example `## Agent Memory Brain Setup`.
- Fill in the four parts under your heading:
  - **What I learned**
  - **Decisions**
  - **Open questions**
  - **Lesson to keep**

If you already have a heading today, add new sentences under that same heading. Do not make a second heading for yourself.

Do not edit another bot's heading or text. Do not delete or rewrite an older daily note to tidy it up.

## Never write secrets or private details

Do not put any of these in a note, an attachment, a file name, or a commit message:

- Passwords
- API keys
- Tokens
- Card numbers
- Street addresses
- Phone numbers

Say "the login is in the password manager" instead of pasting the login.

GitHub runs a secret check on every push and every pull request. If a password, key, or token is in the commit, the check fails. Do not turn the check off. Take the secret out and commit again.

There is a matching check for your own computer. It runs just before a commit is saved, after a one-time setup. The README explains that setup.

If a secret was already pushed, treat it as exposed. Change that password or key right away. Deleting the line in a newer commit is not enough, because the old commit still has it. Ask Kevin for help cleaning the git history.

## Link people and projects

When you mention a person, link their note:

```
[[Jane Doe]]
```

When you mention a project, link it:

```
[[Website Redesign]]
```

Create the note if it is not there yet. People live in `People/`. Projects live in `Projects/`. In Obsidian, type `[[` and pick the note from the list.

## Keep one lasting lesson

Daily notes get long. If something should still matter next month, write a short note in `Lessons/` and link it from **Lesson to keep**:

```
[[Keep secrets out of the vault]]
```

One durable lesson is enough. If nothing should be kept, say so in one line and move on.

## Your bot page

Add a note in `Bots/` with your name and a few lines about your role. Use that same name as your daily heading.

Your day-to-day writing still goes in `Daily/`, not on the bot page.

## Saving

Commit with a short message about what you added, then push. If the secret check fails, remove the secret and try again. Do not skip the check.
