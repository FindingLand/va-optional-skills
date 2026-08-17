# Vera setup guide

**Give this file to Vera in your first chat. Drag it into the chat, or paste it in.**

If you followed the Week 1 walkthrough, GitHub is already connected and Vera simply confirms it in one
line and pulls your Memory Vault onto your computer. If something is not connected yet, she walks you through the steps below, one step at a time.
You never type a command. Vera does that part.

You only need this file once.

---

## What Vera checks first

1. **Is your Memory Vault connected?** That is your GitHub folder, where Vera saves your work so it
   is still there tomorrow.
2. **Is your team in your Memory Vault?** Vera asks which GitHub folder is yours (you made it in
   pre-work), then copies Vera, Tessa, Fiona, Owen and the tool skills from the course library into
   it. From then on those copies are yours: you customize them, and that is your second brain.
3. **Is your central hub connected?** That is your Airtable, where your properties, leases and tasks
   live.

If all is fine, she says so and you start working. If something is not, she takes you through the
steps for that one thing, and only that one.

---

## Part A. Your Memory Vault on GitHub (Vera guides you through this if needed)

### Step 1. A GitHub account

1. Go to **https://github.com**.
2. Click **Sign up** and create a free account. If you already have one, sign in.

### Step 2. Your Memory Vault (a private folder on GitHub, called a repository)

**You made this in pre-work. Skip to Step 3 if you have it.** If not:

1. Sign in at **https://github.com**.
2. Click the **+** in the top right corner.
3. Click **New repository**.
4. In the name box type: **second-brain**
5. Click **Private**.
6. Tick the box **Add a README file**.
7. Click the green **Create repository** button.

### Step 3. Let Claude into your Memory Vault

1. Open the **Claude Desktop** app.
2. Click **Code** at the top.
3. Click **Connect GitHub** (it may say "Install GitHub app").
4. A GitHub page opens. Click **Install** (or "Install & Authorize").
5. Choose **Only select repositories**.
6. Pick **second-brain** from the list.
7. Click **Install** (or "Save").
8. Go back to Claude Desktop.

### Step 4. Open Claude on your computer (Local)

1. In Claude Desktop, in the **Code** tab, choose **Local**.
2. Click **Select folder** and pick the folder you made in pre-work (for example **My Claude Code
   Work**). If you do not have one, make an empty folder anywhere and pick it.
3. Type **Hey Vera** and press Enter.

Vera brings your Memory Vault into that folder herself. **The first time, a GitHub window may pop
up asking you to sign in: click "Sign in with your browser", then "Authorize", and come back.** That
is all. She then tells you in one line whether saving is on.

You start on Local for all of setup. Later, when you know what Cloud can and cannot do, you may switch
to Cloud for everyday work.

---

## Part B. Your central hub on Airtable

1. In Claude Desktop, click your name at the bottom left, then **Settings**, then **Connectors**.
2. Find **Airtable** and click **Connect**. Sign in to Airtable when it asks and allow access.
3. Fully quit Claude and open it again, so it sees the new connection.
4. Tell Vera: **"My Airtable is connected."**

She checks whether the three small tables she needs are there (routines, tasks, skills) and builds
them for you if not. Then she fills the skills table with your team, so you can see in Airtable every
skill you have and what each one does. You do not design anything.

**Only if Vera says the connector cannot do something** (she will name it), she asks you for an
Airtable token. Steps, one at a time:

1. Go to **https://airtable.com/create/tokens**.
2. Click **Create new token**.
3. Name: **vera**
4. Under **Scopes**, click **Add a scope** and tick these four: **data.records:read**,
   **data.records:write**, **schema.bases:read**, **schema.bases:write**.
5. Under **Access**, click **Add a base** and pick your central hub.
6. Click **Create token**.
7. **Copy it now.** It is shown once. Paste it where Vera tells you, not into the chat if she offers
   a file instead.

---

## If something does not work

- **Vera says your Memory Vault is not connected.** Do Part A, Step 3 again. The most common miss is
  Step 6, the folder was not ticked when Claude was let in.
- **A GitHub sign-in window popped up and you closed it.** Tell Vera "try again" and this time click
  "Sign in with your browser", then "Authorize".
- **Vera cannot find Git (Windows).** Install it from **https://git-scm.com/downloads/win**, click Next
  through every screen, then fully quit Claude and open it again.
- **You named your folder something else.** That is fine. Use that name wherever this guide says
  second-brain.
- **Vera says Airtable is not connected.** Do Part B, Steps 1 to 3 again, and remember to fully quit
  Claude and reopen it.

---

## For Vera

This file is the setup playbook and is kept out of your skill so your instructions stay short. It
lives at `https://raw.githubusercontent.com/FindingLand/va-optional-skills/main/download/vera-setup.md`
and you can fetch it any time.

**Check, do not lecture.** On a first session (Local, a folder on their computer):

1. Run `git --version`. No version on Windows means Git for Windows is missing: send them to the
   "cannot find Git" line above, then they quit and reopen Claude. Stop until it passes.
2. Is the working folder already a clone of their Memory Vault? Run `git remote -v`. If not, ask
   which repository is their vault (usually `second-brain`), then clone it into the working folder:
   `git clone https://github.com/<user>/second-brain`. On Windows a GitHub sign-in window opens the
   first time (Git Credential Manager): tell them, in one line, to click "Sign in with your browser"
   and "Authorize". If git instead asks for a username and password in the output, that is the token
   path in the last section: guide it, one step at a time.
3. Prove saving: add one line to `log.md` (create it if missing), commit, push, then read the remote
   back with `git ls-remote origin` and confirm the new commit is there.
4. Say in ONE line whether saving is on or off.
5. Then bring the team home (your skill says how): copy every library skill into the vault under
   `.claude/skills/`, push, read back, and say it in two lines.
6. Then Airtable: try the connector first. Only when the connector cannot do a specific thing you
   need do you walk them through the token steps in Part B, and you say which thing it could not do.

**Only if a check fails**, walk them through the matching step above, in these plain words, ONE step at
a time. Give one numbered step, wait for them to say done, then give the next. Never paste the whole
list, never explain why, never use the words repository, remote, clone, branch, commit or token unless
they use them first. Say "your Memory Vault" for the repository.

**If they later switch to Cloud** (a session opened on the repo at claude.ai/code or in the Code tab):
nothing to configure, the working folder IS the vault; a push may land on a `claude/...` branch, which
still counts as saved. Say which branch.

**Token path (only when git asks for a password, typically Mac):** a fine-grained GitHub token for
that one repository with Contents set to Read and write, stored in `~/.config/vera/` on Mac or
`%USERPROFILE%\.vera\` on Windows. Offer to write that file with the token line blank so they paste
the token into the file, not into the chat. Baby steps: github.com, profile picture, Settings,
Developer settings, Personal access tokens, Fine-grained tokens, Generate new token, name it vera,
longest expiration, only select repositories, pick second-brain, Repository permissions, Contents,
Read and write, Generate, copy it once.
