# Skills manifest

Every skill shipped to VA Optional students. Your assistant reads this file to work out what changed
since her last run.

One folder per skill under `skills/<name>/`, holding `SKILL.md` plus any references or scripts it
needs. Every `SKILL.md` carries a `Version` line near the top, and that line is what the sync
compares against.

> **The four agents (Vera, Tessa, Fiona, Owen) are being rewritten and are deliberately not in this
> repo yet.** A first draft was written and then failed an independent review on approval boundaries,
> schema coverage and legal wording, so it was withdrawn rather than shipped. It returns once it
> passes.

### Everything else

| Folder | Version | Last update | What it does |
|---|---|---|---|
| `landlord-inbox-handler/` | 1.0 | 2026-08-10 | Reads your email once a day, gives you a short priority brief, and drafts tenant and vendor replies you send yourself |
| `drive-organizer/` | 1.0 | 2026-08-10 | Reorganizes a messy Google Drive into a clear numbered structure, moving and renaming files in place so existing links keep working |
| `file-namer/` | 1.0 | 2026-08-10 | Gives every document one consistent name and one correct home, and performs the renaming |
| `second-brain/` | 1.0 | 2026-08-10 | Builds a written memory of your business that your assistant reads at the start of every session |
| `prompt-architect/` | 1.0 | 2026-08-10 | Turns a vague request into a reusable, properly structured prompt |
| `landing-page-copywriter/` | 1.0 | 2026-08-10 | Writes conversion-focused copy for a landing or sales page |
| `linkedin-writer/` | 1.0 | 2026-08-10 | Turns an idea, a story, or existing writing into a LinkedIn post |

## Notes for whoever maintains this repo

- **Nothing specific to one business belongs here.** No API keys, tokens, webhook URLs or account
  ids. No Airtable base, table or field ids. No real tenant, vendor or property names. No portfolio
  facts such as how many units someone owns. A student is a different landlord with a different
  portfolio, and these files are public.
- **No skill may hardcode a table or field id.** Students diverge from the starter base almost
  immediately. Skills resolve tables and fields through the schema mapping their own assistant
  maintains in their own repo.
- Bump the `Version` line in a skill and its row here in the same commit, or the sync cannot tell
  anything changed.
