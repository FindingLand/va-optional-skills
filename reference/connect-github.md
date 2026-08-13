# Connecting GitHub, once, at the start

This is the only setup in the whole system that you do by hand. It takes about ten minutes and you
never touch it again. Do it before your first working session.

**What it is for:** everything your assistant learns, every skill she improves, and every note she
keeps lives in a folder of your own on GitHub. That is what makes tomorrow smoother than today.
Without it she still works perfectly well, she just starts from scratch every time.

**⛔ Read this before you start, it is the thing that trips everyone up.** Claude has a GitHub
setting in its own Settings screen, under Connectors. **That is not this, and switching it on does
not help.** That one lets Claude read code in a chat. Saving your work is a different mechanism that
runs on your own computer. People switch on the connector, see the word "Connected", and then find
nothing ever saves. If that happened to you, nothing is broken, you just have not done the four
steps below yet.

---

## Step 1. Make sure Git is on your computer

Git is the tool that does the actual saving. Claude works without it, which is exactly why this gets
missed.

**Check first, do not install blindly.** In your Claude session, type this and send it:

> Run `git --version` and tell me what it says.

- If it answers with a version number like `git version 2.43.0`, you already have it. **Go to Step 2.**
- If it says something like `command not found` or `not recognized`, install it:
  - **Windows:** download from **https://git-scm.com/downloads/win**, run the installer, and click
    Next through every screen. The defaults are correct. Do not change anything.
  - **Mac:** open the Terminal app and type `git --version`, then press Enter. Mac offers to install
    the developer tools for you. Click Install and wait.
- **Close Claude completely and open it again** after installing, otherwise it will not see Git yet.
  Then ask it to run `git --version` once more and confirm you get a version number.

---

## Step 2. Create your own repository

A repository, or repo, is just a folder that lives on GitHub.

1. Sign in at **https://github.com**.
2. Click the **+** in the top right corner, then **New repository**.
3. **Repository name:** call it `my-back-office` unless you have a better idea.
4. Choose **Private**. This is your business data.
5. Tick **Add a README file**. This matters: a completely empty repo behaves oddly, and the tick box
   avoids it.
6. Click **Create repository**.
7. **Copy the address from your browser's address bar.** It looks like
   `https://github.com/yourname/my-back-office`. You will paste it in Step 4.

---

## Step 3. Create a token

A token is a password that only works for this one repo. Your assistant needs it to save.

1. Click your **profile picture**, top right, then **Settings**.
2. Scroll to the very bottom of the left sidebar and click **Developer settings**.
3. Click **Personal access tokens**, then **Fine-grained tokens**.
4. Click **Generate new token**.
5. Fill it in:
   - **Token name:** `assistant`
   - **Expiration:** pick the longest offered. When it expires, saving stops until you make a new
     one, so a long life saves you a surprise later.
   - **Resource owner:** your own account.
   - **Repository access:** choose **Only select repositories**, then pick the repo from Step 2.
   - **Permissions:** open **Repository permissions**, find **Contents**, and set it to
     **Read and write**. This one line is the whole point of the step. Leave everything else alone.
6. Click **Generate token**.
7. **Copy the token now.** It is shown once and never again. If you lose it, delete it and make
   another, which costs nothing.

---

## Step 4. Hand both to your assistant

Open Claude on the folder you work in and say **Hey Vera**. Then tell her:

> I want to set up saving. My repo is https://github.com/yourname/my-back-office

She will ask where to put the token. **Prefer writing it into the file she offers rather than pasting
it into the chat**, because anything you type in a conversation stays in that conversation.

From there she does the rest herself: writes her own settings, copies the repo down to your computer,
reads it back to prove it worked, and saves for the first time. **You do not type a single command.**

**You are done when she tells you, in a line, that saving is on and what she just saved.** If she
cannot confirm it, she will say so plainly rather than pretend. Ask her what failed and she will tell
you which of the four steps to revisit.

---

## If something goes wrong

- **"It says GitHub is connected but nothing saves."** You connected the Settings connector, not
  this. Do the four steps above.
- **"She cannot find Git."** Step 1, and remember to fully close and reopen Claude after installing.
- **"She says the token is not allowed."** The token is almost certainly missing **Contents: Read and
  write**, or it was made for the wrong repo. Make a new one, it takes a minute.
- **"I lost the token."** Delete it on GitHub and generate another. Tokens are disposable.
- **"I do not want to do this at all."** That is allowed. Your assistant works fine without it and
  will tell you each session that saving is off.
