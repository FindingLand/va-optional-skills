---
name: file-namer
description: "Name, rename, audit, and file documents in Google Drive with total consistency, and ACTUALLY rename and move them in place (not just suggest names) so links never break. Works for ANY use case, not just real estate: client files, business documents, marketing assets, personal files, or a landlord/property drive. Use whenever the user wants to name a new document, rename an existing file or folder, decide where a file belongs, clean up messy or inconsistent names, audit a folder for naming consistency, or set up folders. Triggers on: name this file, rename this doc, what should I call this, where does this go, file this for me, clean up these names, fix these file names, audit my folder, set up folders. For rebuilding a whole messy drive at once, use the drive-organizer skill instead. Real estate is one supported example (see the appendix)."
---

# File Namer (general purpose, any use case)

**Version: 1.0 - 2026-07-14**

> ## ⛔ HARD RULE: renames and moves are ALWAYS executed via the Apps Script
> The Google Drive connector CANNOT rename or move an existing file. The ONLY execution
> mechanism for this skill is the bundled Apps Script (`scripts/drive_rename_move.gs`), run FOR
> the user in the browser per "Executing the Rename" below. NEVER rename files one-by-one
> through the Drive UI or connector, NEVER just suggest names without offering to execute, and
> NEVER hand a non-technical user the script with written steps. If you catch yourself doing a
> rename any other way, stop: you are using this skill wrong (or running an outdated copy of
> it, so check for a newer version of the skill).

Give documents one consistent name and one correct home, every time, and then actually carry
out the rename and the move in Google Drive. This is the single-file / few-file tool; for a
whole-drive backlog cleanup use the drive-organizer skill (same engine, bulk flow).

It replaces guesswork ("what did I call that file again?") with a simple, consistent rule set,
and it does the renaming for you instead of leaving you a to-do list. It works **in place**, so
the file keeps its ID and every existing link keeps working.

It is **not** limited to real estate. The naming principles below apply to client documents,
business paperwork, marketing assets, or personal files. Real estate has a dedicated template in
the appendix (five-domain structure, shortcodes, category codes) for when that is the use case.

**It handles files AND folders, and it is great for BULK.** Point it at a HIGH parent folder and
one run can sweep every file and subfolder underneath (fix inconsistent or non-English folder
names in the same pass). Enumerate the parent recursively to build the full operation list.

---

## First Run: Learn the Setup (ask once, then remember)

Before naming anything, get what you need. If it is already in the conversation, do not re-ask.

1. **The file(s) or folder to work on.** For a single file, its name/ID. For a bulk job, the
   parent folder link (the ID is the part of the URL after `/folders/`).
2. **Context / convention.** Does the user already have a naming convention to match, or should
   you propose one from the best practices below? One line about what these documents are helps
   you name them well (a client's contracts, invoices, marketing exports, property leases).
3. **(Real estate only)** the company name, to derive the all-caps company shortcode. Skip this
   for a general use case; clean human-readable names are enough.

---

## Naming Best Practices (use these unless the user has their own convention)

A good filename tells you what the document is at a glance and sorts sensibly next to its
siblings. Apply these:

- **Be descriptive first.** Lead with what the document IS (`Signed-Lease`, `Q3-Invoice`,
  `Buy-Box-Criteria`), not a scan number or `final FINAL v2`.
- **Consistent casing, no raw spaces.** Use Hyphen-Case or PascalCase (`Cold-Calling-List`,
  `MortgageStatement`). Avoid spaces and random capitalization so names are clean and
  machine-friendly.
- **Date anything time-bound**, one format throughout: `YYYY-MM-DD` (sorts chronologically) or
  `MMDDYYYY`. Use the document's effective date when visible, else the filing date, and note it.
- **Version when it matters.** Add `-v2`, `-v3` for revisions; keep the prior version, do not
  overwrite it.
- **Keep the extension** on uploaded files (`.pdf`, `.xlsx`, `.mkv`). For a NEW native Google
  file, omit the extension (the title is the name).
- **One home per document.** Decide the right folder; if it could live in two places, pick the
  primary and note the secondary in the name.
- **When unsure what a document is, ASK.** Do not name or file a doubtful file on a guess. A
  misnamed or misfiled document is effectively lost, so a question is always cheaper.

---

## Executing the Rename (the part that actually changes Drive)

This is what makes the skill more than advice. The Google Drive connection can read, search, and
create files, but it CANNOT rename or move an existing file. So you produce and run a one-time
Apps Script that does it for them, in place.

1. **Identify the item(s).** Use Drive search to get each file/folder **ID**, current name, and
   location. Never guess an ID.
2. **Decide the new name + destination** with the best practices above (or the user's convention).
3. **Show the plan** as a table (`Current Name | New Name | Destination | Notes`) and confirm
   anything ambiguous BEFORE running.
4. **Fill the Apps Script** `scripts/drive_rename_move.gs`: set `ROOT_FOLDER_ID` (a HIGH parent
   for bulk), the `FOLDERS` skeleton if you are creating folders, and one `OPERATIONS` row per
   item: `{ fileId, newName, destPath }`, plus `isFolder: true` for a folder. `newName` does the
   rename, `destPath` does the move; the same single run does both.
5. **RUN IT FOR THEM in the browser. Do NOT hand a non-technical user a script plus written
   steps.** Drive script.google.com yourself with the Claude-in-Chrome tools; the user's ONLY
   step is the one-time Google permission grant. Flow:
   a. Open `https://script.google.com/home/projects/create` (fresh project).
   b. Click into `Code.gs`, select all, delete, then **PASTE** the filled script (Ctrl/Cmd+V).
      PASTE, never type it: the editor auto-closes brackets/quotes and corrupts typed code.
   c. Save (Ctrl/Cmd+S). Confirm the function dropdown shows `organizeDrive`.
   d. **Run directly to apply** (the script ships with `DRY_RUN = false`). Do NOT force a dry-run
      preview: you already showed the plan in step 3, and the memory index in the next section is
      the real revert net. Offer a `DRY_RUN = true` preview only if the user asks or for a large,
      high-risk run.
   e. **The one user step:** approve Google's popup: *Review permissions -> their account ->
      "Google hasn't verified this app" -> Advanced -> Go to <project> (unsafe) -> Allow.*
   f. **After Allow, the script RUNS AUTOMATICALLY.** Do not click Run again or click it yourself.
      Wait a few seconds, then read the log until it says **Finished**.
   g. **Verify, and tell the user first WHY.** Say something like "I'll re-list the folder to
      confirm each item got its new name, so we catch any mistake while it's easy to fix," then
      re-list via Drive search and confirm. Report the result.
   h. **Write the memory index** (next section) so nothing is ever lost and any change can be
      reverted.
   Hand over the script + written steps ONLY as a fallback when browser tools are unavailable.

Why in place and not copy-then-delete: `moveTo` and `setName` keep the file's original ID, so
**every existing link keeps working**. A copy creates a new link and orphans the old one. Only
offer copy-based handling if the user explicitly wants a duplicate.

---

## The Index (so you can answer "where did you put X?" and revert)

Memory lives in a bundled markdown file, `references/file-index.md` (create if missing). Each
run, append a row: `Date | Original name | New name | Destination path | File ID/link | Notes`.
Record the file ID and original location so any change can be reverted (build a reversing
OPERATIONS list from the index and run the same engine).

When the user later asks "where is the Doe lease?" or "what did you rename Scan_0423 to?", answer
from the index (match on original name, party, or destination). If it is not there, fall back to
a live Drive title search.

---

## Audit Mode

When asked to audit a folder:
1. Pull the file/folder list from Drive (titles + IDs).
2. Check each item against the convention: descriptive? consistent casing, no stray spaces?
   date format consistent? version where needed? correct destination folder?
3. Return a table: `Current Name | Recommended Name | Destination | Action | Notes`.
4. Flag anything whose correct home is ambiguous and ask before recommending a move.
5. Offer to execute the fixes via the Apps Script (Executing the Rename, above).

---

## Appendix: Real Estate / Landlord Template

When the documents ARE landlord/property paperwork, use this convention.

**Five-domain structure:** `[COMPANY]/ 01_Legal, 02_Finance{Banking, Accounting, Taxes,
Insurance-Portfolio-Level, Lending}, 03_Operations, 04_Properties/[Address]/{Finance, Leasing/
[Tenant]/{01_Due-Diligence,02_Lease,03_Tenant-Communication}, Maintenance, Asset-Docs}, 05_Archive`.

**Filename formula:** `[DESCRIPTOR]-v[N]-[PARTY]-[SCOPE]-[CATEGORY]-[MMDDYYYY].[ext]`
(PascalCase descriptors, version from v1, party = last name or company first word).

**Property shortcode:** `[StreetNumber][StreetNameAbbrev]` (4-6 caps, drop St/Ave/Rd; add `-U[N]`
for unit-specific files). Examples: `123 Main St -> 123MAIN`, `456 Oak Ave -> 456OAK`.

**Category codes:** LEGAL, FINANCE, TAX, INS, OPS, VENDOR (company); PURCHASE, LOAN, MORT, MAINT,
RENO, PERMIT, WARRANTY, PHOTO (property); APP, LEASE, NOTICE, COMM (tenant).

Examples: `SignedLease-v1-Doe-123MAIN-LEASE-02152026.pdf`,
`Statement-Mar2026-v1-123MAIN-MORT-04012026.pdf`, `W9-v1-ABCPlumbing-ACME-VENDOR-03012026.pdf`.
Keep a running shortcode list in `references/file-index.md` so the same property reuses one code.
