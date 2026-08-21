# Vera setup guide

**Give this file to Vera in your first chat. Drag it into the chat, or paste it in.**

If you followed the Week 1 walkthrough, GitHub is already connected and Vera simply confirms it in one
line and pulls your Memory Vault onto your computer. If something is not connected yet, she walks you through the steps below, one step at a time.
You never type a command. Vera does that part.

You only need this file once.

---

## Before you start: three things from your pre-work

These take a couple of minutes each, and every one of them has stalled a session before.

### 1. Update Claude Desktop and relaunch it

Open the Claude Desktop app. If it offers **Relaunch to update** anywhere, a small banner or a line in
the menu, click it and let it restart. If it offers nothing, quit the app completely and open it again
anyway.

Do this before your first session with Vera, and again on the morning of your live session. On our
test run, the person whose setup worked had done it and the person whose setup broke had not.

### 2. Have your Central Hub link to hand

Your pre-work email includes a link to the **TLL Central Hub**, the starter Airtable base for the
course, **and the password that opens it**. Have both to hand before your first session. You are not
asked to do anything with them yet, and you will be told when to use them.

**If either is missing from your pre-work email, ask in the group channel now.** Hunting for it in the
middle of a live session is exactly what this line exists to prevent.

### 3. Your Memory Vault and your working folder

You made both in pre-work: a private GitHub folder called **second-brain**, and an empty folder on
your own computer for Claude to work in. If either is missing, Part A below has the steps.

---

## What Vera checks first

1. **Is your Memory Vault connected?** That is your GitHub folder, where Vera saves your work so it
   is still there tomorrow.
2. **Is your team in your Memory Vault?** Vera asks which GitHub folder is yours (you made it in
   pre-work), then copies Vera, Tessa, Fiona, Owen and the tool skills from the course library into
   it. From then on those copies are yours: you customize them, and that is your second brain.
3. **Is your central hub connected?** That is your Airtable, where your properties, leases and tasks
   live.
4. **Can she see your files?** That is Google Drive, and anything else you have connected.

She answers all of it in **one line**, saying what she can see and what she cannot. Read that line. It
is the cheapest moment in the whole setup to catch something missing.

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

**⚠️ On a Claude Team or Enterprise account, do this part first.** The GitHub connector does not
appear anywhere until someone switches it on for the organisation. Go to **Organization Settings**,
then **Connectors**, and enable GitHub there. Then switch it on again in your own personal settings.
Two passes, in that order. On a personal Pro or Max account there is no organisation, so skip this and
start at step 1.

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
2. Find **Airtable** and click **Connect**. Sign in to Airtable when it asks.
3. **Airtable then asks which bases Claude may use. Choose all of them.** There is an option along the
   lines of **All current and future bases**. Pick that one, then allow access.
4. Fully quit Claude and open it again, so it sees the new connection.
5. Tell Vera: **"My Airtable is connected."**

### Why step 3 matters more than it looks

**That choice is made once, at the moment you connect, and it cannot be widened afterwards.** Pick one
base and Vera can only ever see that one base, however many you own. On our test run somebody
connected this way, and the restriction did not surface until three steps later, when things stopped
working and nobody could see why.

**So check it straight away.** When you tell Vera your Airtable is connected, she answers in one line
with what she can and cannot see. If a base you expected is missing from that line, fix it now: see
**"Vera can only see one of your Airtable bases"** below.

The same is true of every other connection you make, Google Drive and Slack included. The access is
set at the moment you connect, so that one line from Vera is your check on all of them at once.

### What Vera does next

She checks whether the three small tables she needs are there (routines, tasks, skills) and builds
them for you if not. Then she fills the skills table with your team, so you can see in Airtable every
skill you have and what each one does. You do not design anything.

### If Vera asks you for an Airtable token

**Only if she says the connector cannot do something** (she will name it), she asks you for a token.
Steps, one at a time:

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

## Part C. Your files on Google Drive

Vera reads, names and files your documents, but only the ones she can actually see.

1. In Claude Desktop, click your name at the bottom left, then **Settings**, then **Connectors**.
2. Find **Google Drive** and click **Connect**. Sign in and allow access.
3. Fully quit Claude and open it again.

### The one rule that catches everyone

**Vera cannot see a private file.** A file or folder has to be shared as **anyone with the link can
view** before she can read it, rename it or move it. View is enough. She never needs edit.

The symptom is confusing when it happens: you are looking straight at a document on your screen and
Vera tells you she cannot find it.

### Set it up once and stop thinking about it

Make one catch-all folder and share the folder rather than the files:

1. In Google Drive, click **New**, then **New folder**, and name it **To File**.
2. Right click the folder and click **Share**.
3. Under **General access**, change **Restricted** to **Anyone with the link**.
4. Leave the role as **Viewer**. Click **Done**.

**Everything you drop into that folder inherits the setting**, so you never share anything by hand
again. Drop documents in as they arrive, then tell Vera to file them.

---

## If something does not work

- **Vera says your Memory Vault is not connected.** Do Part A, Step 3 again. The most common miss is
  Step 6, the folder was not ticked when Claude was let in.
- **You cannot find the GitHub connector at all.** You are on a Claude **Team or Enterprise** account,
  where it stays hidden until someone enables it for the organisation. Go to **Organization Settings**,
  then **Connectors**, switch GitHub on there, then switch it on again in your own settings. It has to
  be both, in that order.
- **You saw "You don't have access to organization settings", and the GitHub connection never
  finished.** This is not a real permission limit, and pressing Connect again does not clear it. One
  thing fixes it: **uninstall** the Claude GitHub App completely, install it again from
  **https://github.com/apps/claude**, and then click **Finish connecting GitHub** back in Claude.
- **A GitHub sign-in window popped up and you closed it.** Tell Vera "try again" and this time click
  "Sign in with your browser", then "Authorize".
- **Vera cannot find Git (Windows).** Install it from **https://git-scm.com/downloads/win**, click Next
  through every screen, then fully quit Claude and open it again.
- **You named your folder something else.** That is fine. Use that name wherever this guide says
  second-brain.
- **Vera says Airtable is not connected.** Do Part B, Steps 1 to 4 again, and remember to fully quit
  Claude and reopen it.
- **Vera can only see one of your Airtable bases.** The access was set at the moment you connected, so
  it cannot be widened from Vera's side. In **Settings**, then **Connectors**, disconnect **Airtable**,
  connect it again, and this time choose **all** bases on the Airtable screen. Then fully quit Claude,
  open it again, and ask Vera what she can see.
- **Vera says she cannot see Google Drive, or Slack, or something else you connected.** Same cause.
  Connect that one in **Settings**, then **Connectors**, then fully quit Claude and open it again.
- **Vera cannot find a document that is open on your screen.** It is not shared with her. Share it as
  **anyone with the link can view**, or drop it into your **To File** folder, then ask her again.
- **You do not have the Central Hub link, or its password.** Ask in the group channel. Do not save it
  for the live session.
- **Claude is behaving oddly and nothing above fixes it.** Quit the app completely and open it again,
  and take **Relaunch to update** if it is offered.

---

## For Vera

This file is the setup playbook and is kept out of your skill so your instructions stay short. It
lives at `https://raw.githubusercontent.com/FindingLand/va-optional-skills/main/download/vera-setup.md`
and you can fetch it any time.

**Three pre-work items go missing more often than anything else, and each one stalls a session: Claude
Desktop not updated and relaunched, the Central Hub link never received, and Airtable connected to one
base instead of all.** Surface all three in the one line you open with, rather than letting them
appear halfway through a task.

**Check, do not lecture.** On a first session (Local, a folder on their computer):

1. Run `git --version`. No version on Windows means Git for Windows is missing: send them to the
   "cannot find Git" line above, then they quit and reopen Claude. Stop until it passes.
1b. **If GitHub is not connected at all, find out which of the two known causes it is before guiding
   anything.** If they cannot see the GitHub connector in the first place, they are on a Team or
   Enterprise account and it has to be enabled at the organisation level first, then personally. If
   they saw "You don't have access to organization settings" and the connection hung, the only fix is
   uninstall the GitHub App, reinstall from github.com/apps/claude, then "Finish connecting GitHub".
   Both are in the troubleshooting list above. **Neither clears by retrying**, so do not let them sit
   pressing Connect.
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
6. **Then Airtable, and name what you can see rather than only saying connected.** Try the connector
   first. **List the bases you can actually reach, and say whether Google Drive and Slack are there
   too.** If a base they expected is missing, that is the connector's access scope, fixed at the
   moment they connected it: send them to the "can only see one of your Airtable bases" line above,
   which means disconnecting Airtable and connecting it again with all bases chosen. Only when the
   connector cannot do a specific thing you need do you walk them through the token steps in Part B,
   and you say which thing it could not do.
7. **Drive, when filing comes up.** A document they can see and you cannot is a sharing problem, not a
   missing document. Send them to Part C and get the **To File** folder shared once, rather than
   sharing files one at a time for the rest of the course.

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
