# Vera setup guide

**Give this file to Vera in your first chat. Drag it into the chat, or paste it in.**

If you followed the video, GitHub is already connected and Vera will simply confirm it in one line.
If something is not connected yet, she walks you through the steps below, one step at a time. You never
type a command. Vera does that part.

You only need this file once.

---

## What Vera checks first

1. **Is GitHub connected?** That is where Vera saves your work so it is still there tomorrow.
2. **Is Airtable connected?** That is where your properties, leases and tasks live.

If both are fine, she says so and you start working. If one is not, she takes you through the steps
for that one, and only that one.

---

## Part A. Connect GitHub (Vera guides you through this if needed)

### Step 1. A GitHub account

1. Go to **https://github.com**.
2. Click **Sign up** and create a free account. If you already have one, sign in.

### Step 2. A private folder for your work (called a repository)

1. Sign in at **https://github.com**.
2. Click the **+** in the top right corner.
3. Click **New repository**.
4. In the name box type: **my-back-office**
5. Click **Private**.
6. Tick the box **Add a README file**.
7. Click the green **Create repository** button.

### Step 3. Let Claude into that folder

1. Go to **https://claude.ai/code**.
2. Click the button to **connect GitHub** (it may say "Connect GitHub" or "Install GitHub app").
3. A GitHub page opens. Click **Install** (or "Install & Authorize").
4. Choose **Only select repositories**.
5. Pick **my-back-office** from the list.
6. Click **Install** (or "Save").
7. You are sent back to Claude. If not, go to **https://claude.ai/code** again.

### Step 4. Open Claude on your folder

1. At **https://claude.ai/code**, find the box where you choose a repository.
2. Choose **my-back-office**.
3. Type **Hey Vera** and press Enter.

That is it. Vera checks the connection herself and tells you in one line whether saving is on.

---

## Part B. Connect Airtable

1. Go to **https://airtable.com** and create a free account, or sign in.
2. Create a base, or open the one you already use for your properties.
3. Tell Vera: **"My Airtable is ready."**

She checks whether the two small tables she needs are there, and offers to build them for you if not.
You do not design anything.

---

## If something does not work

- **Vera says GitHub is not connected.** Do Part A, Step 3 again. The most common miss is Step 5,
  the folder was not ticked when Claude was let in.
- **Vera cannot see the repository.** Do Part A, Step 4 again and make sure **my-back-office** is
  the one chosen.
- **You made the folder with a different name.** That is fine. Use that name wherever this guide says
  my-back-office.

---

## For Vera

This file is the setup playbook and is kept out of your skill so your instructions stay short. It
lives at `https://raw.githubusercontent.com/FindingLand/va-optional-skills/main/download/vera-setup.md`
and you can fetch it any time.

**Check, do not lecture.** On a first session:

1. Run `git remote -v` and `git ls-remote --heads origin`. Both working means GitHub is connected.
2. Prove saving: add one line to `log.md` (create it if missing), commit, push, then read the remote
   back with `git ls-remote origin` and confirm the new commit is there. If the push landed on a
   branch named `claude/...`, that still counts as saved. Say which branch.
3. Say in ONE line whether saving is on or off. Then move on.

**Only if a check fails**, walk them through the matching step above, in these plain words, ONE step at
a time. Give one numbered step, wait for them to say done, then give the next. Never paste the whole
list, never explain why, never use the words repository, remote, clone, branch, commit or token unless
they use them first. Say "your folder on GitHub" instead of "repository".

**Working on their own computer instead of claude.ai/code:** git must be installed (`git --version`),
and saving needs a fine-grained GitHub token for that one repository with Contents set to Read and
write, stored in `~/.config/vera/` on Mac or `%USERPROFILE%\.vera\` on Windows. Offer to write that
file with the token line blank so they paste the token into the file, not into the chat. This is the
exception, not the normal path.
