# VA Optional skills

The skills library for **VA Optional**, the program by The Lean Landlord that gives a self-managing
landlord an AI back office.

Everything here is a template. You do not work in this repo. Your own assistant reads it for you.

## Before you start

- **This is built for landlords in the United States.** Your state's rules are read from settings you
  record yourself. **City and county rules are a known gap.** Elsewhere most of it works and the legal
  parts will not.
- **These agents never tell you what the law is** and never give legal advice. They read what you have
  recorded and tell you to confirm anything legal with your own attorney.
- **Nothing is ever sent for you.** Every message to a tenant, applicant, contractor or agency is
  prepared and held for you to read. That holds even when a routine runs overnight, and there is no
  setting that changes it.
- **You will need** a GitHub account with one private repository connected to Claude (the course video
  shows the clicks), and an Airtable base for your data. Vera checks both on your first chat and walks
  you through anything missing, one step at a time.

## Your team

You talk to Vera. She decides who does the work.

| Agent | Handles |
|---|---|
| **Vera** | Your chief of staff. Loads first every session, keeps your skills current, runs your daily pass, routes everything, and holds anything legal |
| **Tessa** | Tenants and applicants: enquiries, applications, leases, tenancy messages, renewals, move-out, listings |
| **Fiona** | Money: rent and arrears, deposits, part months, charges, your own insurance renewals |
| **Owen** | Property: repairs, contractors, turnovers, seasonal work, post, access codes, filing |

## The rest of the library

| Skill | What it does for you |
|---|---|
| `landlord-inbox-handler` | Reads your email once a day, gives you a short priority brief, and drafts replies you send yourself |
| `drive-organizer` | Turns a messy Google Drive into a clear structure, previewing before it moves anything |
| `file-namer` | Gives every document one consistent name and one correct home |
| `second-brain` | Builds a written memory of your business your assistant reads at the start of every session |
| `prompt-architect` | Turns a vague request into a reusable, properly built prompt |
| `landing-page-copywriter` | Writes the words for a page that gets people to sign up or buy |
| `linkedin-writer` | Turns an idea or a story into a LinkedIn post |

More arrive during the program. You do nothing to receive them.

## How updates reach you

Your assistant keeps her own copy of every skill in **your** private repo. At the start of each run she
checks this library and folds anything new into your copies.

**Your changes are kept.** Where you have edited a skill and the library later changes the same skill,
she merges the two and shows you anything that changed on both sides so you decide. She never
overwrites your work silently.

We never see your repo. What you build on top of these templates is yours.

## One recommendation

**While you are in the program, keep your table names and skill names as they arrive.** Rename things
later, once you know what each piece does. Renaming early is the quickest way to end up with an
assistant that cannot find your data, and it is a frustrating thing to debug in week one.

## Structure

Each skill is a folder under `skills/`. `skills/index.md` lists everything with its version.
`reference/how-we-work.md` is the rulebook every agent follows.
