# Vera setup guide

**Give this file to Vera at the start of your first session and she will run the setup with you.**
Download it, then drag it into the chat, or paste it in. You only need it once. After that Vera works
without it and comes back to it only if something needs re-checking.

If you are reading this yourself, everything here is written for you, not for a technician. You will
not type a single command. Vera does that part.

---

## What you are setting up, and why

Four things, about twenty minutes total.

1. **Git**, the tool that does the saving.
2. **A repository**, a private folder of your own on GitHub where your work lives.
3. **A token**, a password for that one folder so Vera can save into it.
4. **Airtable**, where your properties, leases and tasks live.

Without 1 to 3 Vera still works, she just forgets everything between sessions. Without 4 she has
nowhere to read or write your actual business data. Neither is fatal on day one, and she will tell
you which situation you are in rather than pretending.

**⛔ One warning that saves an hour.** Claude has a GitHub setting of its own, under Settings and
then Connectors. **That is not this, and switching it on does not help.** It lets Claude read code
inside a chat. Saving your work is a different mechanism that runs on your own computer. People
switch that on, see the word "Connected", and then find nothing ever saves. If that already happened
to you, nothing is broken. Just do the steps below.

---

## Step 1. Git

Git is what actually saves. Claude runs fine without it, which is precisely why this gets missed:
everything looks healthy while nothing is being kept.

**Check before installing.** Ask Vera:

> Run `git --version` and tell me what it says.

- A version number, like `git version 2.43.0`, means you are done. Go to Step 2.
- `command not found` or `not recognized` means install it:
  - **Windows:** get it from **https://git-scm.com/downloads/win**, run the installer, and click Next
    through every screen. The defaults are right. Change nothing.
  - **Mac:** open the Terminal app, type `git --version`, press Enter, and Mac offers to install the
    developer tools. Click Install and wait.
- **Close Claude completely and reopen it** after installing, or it will not see Git yet. Then ask
  Vera to check the version again and confirm you get a number.

---

## Step 2. Your repository

1. Sign in at **https://github.com**.
2. Click **+** in the top right, then **New repository**.
3. **Repository name:** `my-back-office` unless you prefer another.
4. Choose **Private**. This is your business data.
5. Tick **Add a README file**. A completely empty repository behaves oddly, and this avoids it.
6. Click **Create repository**.
7. **Copy the address from the browser bar**, like `https://github.com/yourname/my-back-office`.

---

## Step 3. Your token

A token is a password that works for this one repository and nothing else.

1. Click your **profile picture**, top right, then **Settings**.
2. At the very bottom of the left sidebar, click **Developer settings**.
3. Click **Personal access tokens**, then **Fine-grained tokens**.
4. Click **Generate new token**.
5. Fill it in:
   - **Token name:** `vera`
   - **Expiration:** the longest offered. When it expires saving stops, so a long life saves you a
     surprise months from now.
   - **Resource owner:** your own account.
   - **Repository access:** **Only select repositories**, then choose the one from Step 2.
   - **Permissions:** open **Repository permissions**, find **Contents**, set it to **Read and
     write**. That single line is the whole point of this step. Leave everything else alone.
6. Click **Generate token**.
7. **Copy it now.** It is shown once. Lose it and you simply make another, which costs nothing.

---

## Step 4. Airtable

Vera reads and writes your business data here.

1. Create a free account at **https://airtable.com** if you do not have one.
2. Create a base, or open the one you already use for your properties.
3. Tell Vera you have it. **She will check whether the two tables she needs exist, and offer to build
   them for you if not.** One holds her recurring routines, the other holds tasks. You do not need to
   design anything.

If your property data already lives somewhere else, say a rental platform, tell her that too. She
would rather pull from where the data already is than have you retype it.

---

## Step 5. Hand it over

Open Claude on the folder you work in and say **Hey Vera**, then:

> I want to set up saving. My repo is https://github.com/yourname/my-back-office

She will ask where to put the token. **Prefer writing it into the file she offers over pasting it
into the chat**, because anything typed in a conversation stays in that conversation.

From there she does the rest: writes her own settings, copies the repository to your computer, reads
it back to prove it worked, and saves for the first time.

**You are finished when she tells you in one line that saving is on and what she just saved.** If she
cannot confirm it, she will say so rather than pretend, and tell you which step to revisit.

---

## When something does not work

- **"It says GitHub is connected but nothing saves."** That is the Settings connector, not this. Do
  Steps 1 to 3.
- **"She cannot find Git."** Step 1, and remember to fully close and reopen Claude after installing.
- **"The token is not allowed."** It is almost always missing **Contents: Read and write**, or it was
  made for the wrong repository. Make a new one.
- **"I lost the token."** Delete it on GitHub and generate another. Tokens are disposable.
- **"I would rather not do any of this."** That is allowed. Vera works without it and will tell you
  each session that saving is off.

---

## For Vera

This file is the setup playbook and is deliberately kept out of your skill so your instructions stay
short. It lives at
`https://raw.githubusercontent.com/FindingLand/va-optional-skills/main/download/vera-setup.md`
and you can fetch it again any time you need to re-check a step.

Enforce it rather than describing it. Run `git --version` yourself before anything else and stop on
failure. Never claim a sync you have not verified by reading the remote back. State plainly, in one
line, whether saving is on or off before moving on to real work.
