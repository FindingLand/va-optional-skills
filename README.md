# VA Optional skills

This is the skills library for **VA Optional**, the program by The Lean Landlord that gives a
self-managing landlord an AI back office.

Everything here is a template. You do not work in this repo, and you do not need a GitHub account
that can write to it. Your own assistant reads it for you.

## How it works

Your assistant, **Vera**, keeps her own copy of every skill in **your** private repo. At the start of
each run she checks this library, sees what changed, and folds our updates into your copies.

The important part: **your changes are never overwritten.** When you have edited a skill and we later
update the same skill, Vera merges the two. Our version wins on the shared parts, yours wins on
anything you personalized, and anything that changed on both sides gets shown to you so you decide.

We never see your repo. What you build on top of these templates is yours.

## Before you start

- **This is built for landlords in the United States.** Your state and city rules are read from
  settings you fill in yourself rather than assumed, but the shape of the system and its vocabulary
  are American. Elsewhere, most of it works and the legal parts will not.
- **These agents never give legal advice**, and they will tell you to confirm anything legal with
  your own attorney. City and county rules are a known gap: settings are recorded by state, so
  anywhere with local rent, deposit or notice rules is not covered.
- **Nothing is ever sent for you.** Every message to a tenant, applicant, vendor or agency is
  prepared and held for you to read. That holds even when a routine is running overnight.
- **You will need** a GitHub account and a token so your assistant can keep your own copies in sync,
  an Airtable base for your data, and a Claude that can run commands on your machine. Your assistant
  walks you through all of it.

## Your team

You talk to Vera. Vera decides who does the work.

| Agent | Handles |
|---|---|
| **Vera** | Your chief of staff. Loads first every session, keeps your skills current, runs your daily pass, routes everything, and holds anything legal |
| **Tessa** | Tenants: leads, applications, leases, notices, renewals, move-out, listings |
| **Fiona** | Money: rent, arrears, deposits, proration, charges, insurance renewals |
| **Owen** | Property: repairs, vendors, turnovers, seasonal work, mail, access codes, filing |

## The rest of the library

| Skill | What it does for you |
|---|---|
| `landlord-inbox-handler` | Reads your email once a day, gives you a short priority brief, and drafts replies to tenants and vendors that you send yourself |
| `drive-organizer` | Turns a messy Google Drive into a clear numbered structure, and actually moves and renames the files, so your old links keep working |
| `file-namer` | Gives every document one consistent name and one correct home, and does the renaming for you |
| `second-brain` | Builds a written memory of your business that your assistant reads at the start of every session, so you never explain yourself twice |
| `prompt-architect` | Turns a vague request into a properly built prompt you can reuse in any AI tool |
| `landing-page-copywriter` | Writes the words for a page that gets visitors to sign up, download, or buy |
| `linkedin-writer` | Turns an idea or a story into a LinkedIn post people actually stop and read |

More arrive during the program. You do not have to do anything to receive them.

## A recommendation worth following

While you are in the program, **keep the table names in your Airtable base and the names of your
skills as they come.** You can rename things later, once the system is running and you know what each
piece does. Renaming early is the fastest way to end up with an assistant that cannot find your data,
and it is a confusing problem to debug in your first weeks.

After the four weeks, change whatever you like. Your assistant will keep up.

## Structure

Each skill is one folder under `skills/`, holding its `SKILL.md` and any reference files or scripts
it needs. `skills/index.md` lists everything with its current version.
