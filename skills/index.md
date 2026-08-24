# Skills manifest

Everything in the library, with the version your assistant compares against. One folder per skill
under `skills/<name>/`, holding its `SKILL.md` plus anything it needs.

Two files outside `skills/` are part of the system and are versioned the same way:

| File | Version | What it is |
|---|---|---|
| `reference/how-we-work.md` | 4.3 | **The rulebook. The only copy.** Vera reads it every session; the specialists carry a short floor from it and nothing else |
| `templates/your-base.template.md` | 4.1 | The empty snapshot Vera copies into your own repo and fills in from your base |
| `templates/repo-layout.template.md` | 1.1 | The standard folder layout and naming for your second brain. Vera copies it into your repo as `reference/repo-layout.md`; you may change it and she follows your copy |

## Your team

You talk to Vera. She loads first and hands work to the other three.

| Folder | Version | What it does |
|---|---|---|
| `vera/` | 4.33 | Chief of staff. Keeps your skills current, runs the daily pass, routes everything, holds anything legal |
| `tessa/` | 4.2 | Tenants and applicants: enquiries, applications, leases, tenancy messages, renewals, move-out, listings |
| `fiona/` | 4.2 | Money: rent and arrears, deposits, part months, charges, your own insurance renewals |
| `owen/` | 4.2 | Property: repairs, contractors, turnovers, seasonal work, post, access codes, filing |

## Everything else

| Folder | Version | What it does |
|---|---|---|
| `landlord-inbox-handler/` | 1.1 | Reads your email, gives you a short priority brief, and drafts replies you send yourself |
| `cloud-vs-local/` | 2.0 | **Load before answering any "can Cloud do X" question.** Which jobs belong in a Cloud session and which need Local, what Cloud genuinely cannot do, and the rule that these are settled by testing rather than by reasoning. Every claim carries an evidence label |
| `google-drive/` | 1.3 | **Load before ANY Drive work.** The rules: the connector really does rename and move (measured), the Memory Vault must be set up first, sharing so files are visible, and never reporting a move you have not read back |
| `drive-organizer/` | 1.1 | Turns a messy Google Drive into a clear structure, previewing before it moves anything |
| `file-namer/` | 1.2 | Gives every document one consistent name and one correct home |
| `second-brain/` | 1.0 | Builds a written memory of your business your assistant reads at the start of every session |
| `daily-brain-feed/` | 1.0 | OPTIONAL. Feeds your Memory Vault every day from your emails and meeting transcripts, as one routine row. Vera offers it once; heavy on reading, so only for owners with many conversations |
| `prompt-architect/` | 1.0 | Turns a vague request into a reusable, properly built prompt |
| `landing-page-copywriter/` | 1.0 | Writes the words for a page that gets people to sign up or buy |
| `linkedin-writer/` | 1.0 | Turns an idea or a story into a LinkedIn post |

## Notes for whoever maintains this

- **Nothing specific to one business belongs here.** No keys, tokens or account ids. No Airtable base,
  table or field ids. No real tenant, vendor or property names. No portfolio facts. These files are
  public and every reader is a different landlord.
- **The rules live in `reference/how-we-work.md` and nowhere else.** The specialists carry the floor
  from the bottom of that file, verbatim, and nothing more. **Any rule that exists in two places will
  disagree within a day.** That is not a prediction, it is what happened twice.
- **No skill hardcodes a table or field name.** Read the owner's own base file.
- **No skill states a number**, a threshold, a deadline or a point of law.
- Bump a version here and in the file itself in the same commit, or the sync cannot tell anything
  changed.
