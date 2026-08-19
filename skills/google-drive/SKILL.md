---
name: google-drive
description: "How this system works with Google Drive, and the rules that stop Drive jobs failing quietly. Load this BEFORE any Drive work: moving a file, renaming one, building a folder structure, filing a document, sharing something, or answering where did you put X. Covers which Drive jobs work in a Cloud session and which need Local (it is about volume, not about Cloud), what must be set up before Drive work is attempted at all, sharing so the assistant can actually see a file, and never reporting a move or rename without reading the destination back. The two skills that do the work are drive-organizer for a whole messy folder and file-namer for one or a few files. Trigger on: google drive, my drive, move this file, rename this file, file this, organize my drive, set up my folders, share this document, where did you put this, shared drive, folder structure."
---

# Google Drive

**Version: 1.1 - 2026-08-19**

This skill is the rules. The work itself lives in two other skills:

- **`drive-organizer`** for a whole messy folder: build a structure, then move and rename everything.
- **`file-namer`** for one file or a few: name it, put it in the right place.

Load this one first. It exists because Drive is where this system fails quietly, and every rule below
came from a real session going wrong rather than from a manual.

---

## 1. ⛔ Before any Drive work at all: is the Memory Vault actually set up?

**Do not start Drive work until the owner's Memory Vault is connected, the team has been brought home
into it, and this skill and the two Drive skills are loaded.** If any of that is missing, say so in
one line and finish the setup first.

Why this is a hard gate and not a preference: a Drive job produces decisions (what the folder
structure is, what the naming convention is, where a document belongs). **Without the vault there is
nowhere to save those decisions, so they die with the conversation and the next session starts from
nothing.** That has already happened to a real owner: a naming convention was agreed in one thread,
the work moved to a second thread, and the second thread had never heard of it.

The same applies to the skills. If the owner does not yet have their own copies of `drive-organizer`
and `file-namer`, they are relying on whatever happens to be loaded right now, which is exactly how
inconsistent results appear.

## 2. The Cloud-or-Local question, settled by testing rather than by belief

**The connector renames and moves files and folders on its own, in one call, and it works the same in
a Cloud session and a Local one. The dividing line is VOLUME, not Cloud versus Local.**

| Drive job | Where it runs |
|---|---|
| Search, read a file, list a folder, answer "where is X" | Cloud or Local, either is fine |
| Create a folder or a document | Cloud or Local, either is fine |
| **Rename a file or folder. Move a file or folder. One at a time or a handful** | **Cloud or Local, either is fine.** The connector does it directly |
| **A whole-drive sweep: hundreds of files, recursive, one pass** | **Local**, because the Apps Script that does it in one run needs a browser and a permission grant |

**Verified against the live connector on 2026-08-19**, not assumed: a document was renamed and moved
into a different folder in a single call, then read back from the destination to confirm it; a folder
was renamed and moved the same way; **the file id and the share link were unchanged**, so nothing
that pointed at the file broke. No browser, no Apps Script, no permission popup.

**⛔ The old rule was wrong and it was taught out loud, so expect to meet it.** Until this was tested,
these skills said the connector could not rename or move at all and that only the Apps Script could,
and that a Cloud session therefore could not do Drive work. **That is not true.** If an owner tells
you they were taught to switch to Local before filing a document, they were told that in good faith
and it is simply out of date. Say so in one line and get on with the job.

**Why the bulk case still goes Local, and this part was always right:** a whole messy drive means
hundreds of individual calls, and the bundled Apps Script does the same work in one run. That script
needs a browser and a one-time Google permission grant, and **a Cloud session has neither.** So the
`drive-organizer` bulk flow is a Local job. Filing one document is not.

## 3. Never report a move or a rename you have not read back

**Do not trust the response to the write.** After any change, **re-list the destination folder with a
separate search and confirm the file is there under its new name.** Say what you verified, in one
line. If you cannot verify it, say the change is unconfirmed rather than done.

This matters more in Drive than almost anywhere else, because a misfiled document is not visibly
broken. It is simply lost, and nobody notices for months. It is also the check that would have
settled the Cloud argument above months earlier: someone reported a move, nobody looked at the
destination, and a true report got treated as a false one for want of one search.

## 4. The assistant cannot see a private file

**A file or folder must be shared as "anyone with the link can view" before this system can read or
act on it.** View is enough, edit is not required. A private file is invisible, and the symptom is
confusing: the assistant says it cannot find something the owner is looking straight at.

**The pattern worth setting up once:** a single catch-all folder, named something obvious like
`To File`, with that share setting applied **to the folder**. Everything dropped into it inherits the
setting, so the owner never has to think about sharing again. Filing then becomes a routine: read the
catch-all folder, file what is in it, report what moved where.

## 5. Moving a file keeps its link. Say so, because it is the reassuring part

A move and a rename keep the file's identity, so **every existing link to it keeps working**, in
emails, in documents, in other people's bookmarks. Nothing breaks and nothing has to be re-shared.

Copying does not do this. A copy gets a new link, and the old link keeps pointing at the old file,
which then quietly diverges as people edit the wrong one. **Only copy when the owner explicitly wants
a duplicate**, and say plainly what it means when they do.

## 6. Do not reorganize what you were not asked to reorganize

Three separate jobs, and they are not the same:

1. **Agree a naming convention for new files from here on.**
2. **File specific documents** into the right place.
3. **Retrospectively clean up everything that already exists.**

**Job 3 is never implied by jobs 1 or 2.** Ask which one they want. A real owner had to interrupt to
say it: "I think she's planning on renaming all your documents. We're not doing that. We're talking
about what the naming convention is going to be going forward."

A retrospective clean-up on a drive with years of history in it touches other people's links,
permissions and habits, so it is always the owner's decision to ask for, never yours to start.

**When building a new structure, offer to build it alongside what exists and touch nothing.** New
empty folders, named so they stand out and are easy to delete if the owner changes their mind. Then
they decide, with the thing in front of them, whether anything actually moves.

## 7. Google Drive is not the Memory Vault, and the split matters

- **Google Drive is working IN the business:** the documents themselves, the ones a person opens and
  reads. Contracts, statements, forms, photos, anything with a human reader.
- **The Memory Vault is working ON the business:** decisions, policies, procedures, what the
  assistant knows and how it works. Written for the assistant to read.

They are not competing and neither replaces the other. **A naming convention or a folder standard is
a decision, so it goes in the Memory Vault**, even though the files it governs live in Drive.
