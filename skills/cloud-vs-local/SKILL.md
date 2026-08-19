---
name: cloud-vs-local
description: "Answers the recurring question of whether a job should run in a Cloud session or a Local one, and what each genuinely cannot do. Load this whenever someone asks can Cloud do X, why did this work locally but not in the cloud, do I need my computer on, which one should I pick, why can it not see my file, why did it not save, or when a routine or a skill has to be designed to run unattended. Also load it before ANSWERING any capability question of that shape, because the rule in here is that these are settled by testing and not by reasoning. Every claim carries an evidence label and a date. Trigger on: cloud, local, cloud session, local session, cloud vs local, which environment, does my computer need to be on, run overnight, routine, unattended, headless, it worked locally but not in the cloud, select repo, connector in the cloud."
---

# Cloud or Local

**Version: 1.0 - 2026-08-19**

Claude can run in two places and they are not equally capable. Picking the wrong one is the single
most common cause of "it said it worked and nothing happened".

- **Local** means the work runs **on your own computer**. It can see your files and drive your
  browser, and it only runs while your computer is on and awake.
- **Cloud** means the work runs **on Anthropic's servers**. It runs whether your computer is on or
  not, and it cannot see your machine at all.

---

## ⛔ Read this first: how a "can Cloud do X?" question gets answered

**By testing it. Never by reasoning about it.** This skill exists because that rule was broken and it
cost real time and real credibility.

**The rule:** if someone asks whether Cloud can do something and this file does not already say,
**the answer is "I do not know yet, let me test it"**, followed by an actual test. Not an inference
from how the technology probably works. An inference is not an answer, and stating one as if it were
a finding is worse than saying nothing.

**The standard test, which is cheap enough that there is no excuse:**

1. **Create a throwaway fixture** to act on, named so it is obviously disposable (`ZZ TEST ... DELETE ME`).
2. **Run the exact operation in the environment being questioned**, not a similar one somewhere else.
3. **Read the result back from somewhere independent** of the thing that did the work. A tool's own
   success message is not evidence.
4. **Delete the fixture** and confirm it is gone.
5. **Write the answer into this file with the date and the word MEASURED**, so nobody re-derives it.

**The case that earned this rule, 2026-08-19.** A skill had asserted since July that the Google Drive
connector could not rename or move a file and that only an Apps Script could. Nobody ever tested it.
It got taught out loud on a live training call. When a session then DID move and rename a file, the
report was explained away instead of checked. When the claim was finally questioned, the fix was to
test it Locally and then reason that Cloud would behave the same way, **which answered a question
nobody had asked.** One search of the destination folder, months earlier, would have settled all of
it.

**So every claim in this file carries a label:**

- **MEASURED** — we ran it and read the result back. The date says when.
- **DOCUMENTED** — it comes from the vendor's own documentation, not from us running it.
- **UNVERIFIED** — believed, never tested. **Treat as unknown, and say so out loud when you use it.**

---

## What Cloud genuinely cannot do

All **DOCUMENTED**, from Claude Code's own documentation, checked 2026-08-10:

1. **It cannot see your computer.** No files on your disk, no folders, no programs, nothing you have
   installed. If a job needs a file that lives on your machine, it is Local.
2. **It cannot use your browser.** Anything that means clicking through a website, signing in, or
   working in an app that has no proper connection available, is Local.
3. **It cannot finish a login that needs you to click.** Any sign-in popup, any "allow this app"
   screen, any two-factor code. This is the limit that bites most often, and it is why a job that
   depends on one is Local even when everything else about it would suit Cloud.
4. **It does not remember anything between runs.** Every run starts fresh. Anything worth keeping has
   to be written somewhere that persists, which in this system means the Memory Vault.
5. **It cannot save straight to the main copy of your Memory Vault.** It saves onto a side copy that
   then has to be merged in. The work is not lost, but it is not in the main copy until someone
   merges it.

## What each one is for

**Use Local when:**

- the job touches files on your computer
- the job needs your browser, or a login you have to click through
- you are setting things up for the first time, or running something for the first time
- the job has to write straight into the main copy of your Memory Vault
- you are doing a big one-pass sweep that runs a script in your browser

**Use Cloud when:**

- it has to run while your computer is off, overnight or early morning
- it is a scheduled routine
- the job only reads and writes through connections to online services, with no browser and no file
  on your machine involved

**The habit worth building:** start Local until you know where the edges are, then move the jobs that
genuinely do not need your machine over to Cloud. You cannot switch an open conversation from one to
the other, so open a new one and carry on there.

## The grey area, and it is the one people actually hit: connections

A **connection** (Google Drive, Airtable, Gmail, Slack, GitHub) is not your computer talking to that
service. It is Anthropic's servers talking to it. So in principle a connection works the same in
Cloud as it does Locally, and a job built only on connections should not care which one it is in.

**In principle. Which is exactly the kind of sentence this skill exists to distrust.**

| Question | Status |
|---|---|
| Can the Google Drive connection rename and move files AND folders, keeping the link, with no browser and no script? | **MEASURED 2026-08-19: yes, in a LOCAL session.** One call renames and moves; the id and the share link survive; folders behave the same as files. Test fixtures created and deleted. |
| Does that same thing work in a CLOUD session? | ⚠️ **PENDING MEASUREMENT.** Being tested properly. **Until the result is written here, do not claim either way.** Say it is unmeasured, and use Local if the job matters. |
| Are all connections available inside every Cloud context, including scheduled runs? | **UNVERIFIED.** There is reason to think a connection that needed an interactive sign-in may be missing in an unattended run. Nobody has measured it. **Design around it: if an unattended job depends on a connection, prove the connection is there in that exact context before relying on it.** |

**The practical consequence, which holds regardless of how the pending answer lands:** the more a job
depends on plain online services rather than on your machine, the more portable it is. When something
must run unattended, prefer the path with no browser and no local file in it.

## Scheduled routines

- **A scheduled run is a Cloud-or-Local decision made in advance**, and it is the decision that
  matters most, because nobody is watching when it fires.
- **A Local routine only runs while the computer is on and awake.** If the machine is off at 3am, the
  routine does not run. There is no queue and no catch-up.
- **There is a daily cap on how many scheduled runs an account gets**, and it is low enough that one
  schedule per job runs out quickly. **DOCUMENTED 2026-08-10.** So the shape that works is **one
  schedule whose only job is to read a list of work and do everything that is due**, with new
  recurring work added as a row on that list rather than as a new schedule.
- **Anything that cannot run unattended should say so on its row** rather than failing quietly at
  three in the morning.

## When something fails in Cloud, check these four before anything else

1. **Does it need a file on your computer?** Then it was never going to work. Local.
2. **Does it need your browser, or a login you click?** Same. Local.
3. **Did it save, really?** Cloud saves to a side copy that needs merging. Read the destination back
   rather than believing the report.
4. **Did it lose something from last time?** Cloud starts fresh every run. If it needed to remember,
   the memory has to be written somewhere that persists.

If none of those explain it, **stop guessing and run the test at the top of this file.**

## Answering someone else's cloud-or-local question

Three sentences, in this order, and nothing more:

1. **Which one to use, and the one reason.**
2. **What they would lose by choosing the other.**
3. **If you do not actually know, say you do not know and that you will test it.** Never fill the gap
   with a plausible explanation. A confident wrong answer here sends someone off to rebuild something
   that was never broken.
