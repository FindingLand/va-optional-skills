# Troubleshooting

Things that go wrong, in the words you would use to describe them. Find the one that sounds like your
problem and work down from there.

**This page will not fix anything for you, and that is deliberate.** The assistant on your own machine
is the only one who can see what is actually happening on it. This page tells you what is usually
behind a symptom and what to ask her, so you end up able to solve the next one without a page.

---

## First: ask your own Claude

**She can see your machine. Nobody else can.** Not the person who wrote this page, not the group
channel, not anyone reading a screenshot. When something breaks, she is the fastest and best informed
help you have, and she is already open.

Most people ask her badly. A good diagnostic ask has four parts:

1. **What you did.** "I clicked Cloud and picked my repo"
2. **What you saw**, in the exact words on the screen. Copy them, don't summarise them
3. **What you expected instead**
4. **Ask her to find the cause here, on this machine, and tell you what she finds**

Then the line that changes the answer more than anything else:

> "Read it from the actual system, don't tell me from memory"

Without it you get a confident, plausible answer built from what she remembers of how things usually
work. With it she goes and looks. Use it on anything to do with GitHub, your hub, files, or whether
something saved.

**When she gives you a fix, ask her to explain what was wrong before she applies it.** You are trying
to end up understanding your own system, not to be carried by it.

---

## Still setting up?

Anything from your first connection lives in the **setup guide**, not here:
[`download/vera-setup.md`](../download/vera-setup.md), under "If something does not work". It covers
the ones that catch nearly everyone:

- You cannot find the GitHub connector at all
- You saw **"You don't have access to organization settings"** (your connection actually worked)
- The **Configure** button gave you a 404
- Your folder list came back empty with no error anywhere (two GitHub accounts)
- Vera cannot see a document that is open on your screen
- Vera can only see one of your Airtable bases

Come back here once you are set up and something starts misbehaving.

---

## Nothing is saving

### Vera cannot find git, or git is not recognized

**Usually:** git isn't installed. Claude runs perfectly well without it and saving just quietly does
nothing, which is why this one catches people twice.

**Try:** install it from git-scm.com/downloads, accept every default, then fully quit Claude and open
it again. Not a new chat, quit the app.

**Ask your Claude:** *"git --version says not recognized after I installed git. Find where git
actually is on this machine and tell me what's missing from my PATH"*

**#tech-help if:** it installs cleanly and still isn't found after a proper restart. Say which
operating system you're on.

### Every git command gets blocked and nothing goes through

**Usually:** not a git problem at all. She offered one long joined-up command, and joined commands are
what the permission system refuses. Your work is sitting safely on your machine the whole time.

**Try:** ask for the steps separately, and click Allow (or Always allow) on the prompts.

**Ask your Claude:** *"Don't use the combined command. Run the git steps one at a time as separate
commands: add only the files you changed, commit, pull, push, then confirm from GitHub that main has
the changes. I'll click Allow when asked"*

**Worth keeping:** any time she offers one big chained command, ask for it a step at a time. It's the
single habit that prevents this.

**#tech-help if:** the separate steps are still refused, or one of them returns an actual error rather
than a prompt.

### I don't know which folder Claude is working in

**Usually:** nothing is wrong, you just can't see it. In a local session the folder is shown as a chip
at the bottom of the message box.

**Ask your Claude:** *"What folder are we working in? Give me the full path and open it in File
Explorer"* (or Finder on a Mac)

**#tech-help if:** the path she gives you isn't a folder you recognise, or it isn't the one holding
your Memory Vault.

### There is no Code tab, or my repo will not connect

**Usually:** you're in the wrong mode. Home is the chat side of Claude and it has no connection to your
repo at all, so no token and no sequence of steps will make saving work there.

**Try:** top left of Claude there are two options, Home and Code. Home is the chat icon, Code is the
`<>` icon. Click Code. Everything in this program happens in Code.

**#tech-help if:** you're in Code and your repo still won't connect. That one is in the setup guide
first, so check there before you post.

---

## Working in the cloud

### My repo doesn't appear when I choose Cloud

**Usually:** the picker only lists repos you have granted to the Claude GitHub App, and that is a
step on GitHub's side that is easy to skip.

**Try:** go to github.com/apps/claude, Configure, pick your account, choose "Only select
repositories", tick your repo, Save. Then back in Claude, quit the app fully, open it again, and start
a new session. If Configure gives you a 404, use
github.com/apps/claude/installations/new instead, which always works.

**Check first:** the GitHub account that owns the repo has to be the one connected in Claude. Two
accounts, one personal and one for work, is behind most of these.

**#tech-help if:** you've granted the repo, restarted, and it's still not in the list. Say which
GitHub account owns it.

### The Cloud menu is empty, my repo isn't in it

**Usually:** you're reading the wrong menu, and this one is worth knowing because it looks exactly
like a fault. The Local / Cloud menu lists cloud **environments**, usually just "Default". It never
lists repos.

**Try:** look at the chips along the bottom of the message box instead. If your repo name and `main`
are sitting there, you're connected already. Click Cloud, choose Default, and just type what you want
done.

**Don't:** click "Add cloud environment". That opens a dialog asking for a name, environment variables
and a setup script. It's developer tooling and nothing in this program needs it. Cancel it.

### Vera asks me about a pull request when I close out

**Usually:** she's finished the work and is asking permission to put it on the main copy of your
Memory Vault.

**Try:** say yes. That merge is what makes the work count. Better, stop being asked: tell her to land
it herself.

**Ask your Claude:** *"From now on, at every close-out: merge everything to main and confirm from
GitHub before you finish"*

**#tech-help if:** you say yes and it still doesn't land on main.

### My work went to a claude/ branch instead of main

**Usually:** a cloud session pushed to a side branch because nothing told it to do otherwise. Nothing
is lost. A side branch is saved work that hasn't been filed into the live copy yet.

**Try:** ask her to finish the job. A cloud session can merge to main perfectly well by itself.

**Ask your Claude:** *"Merge everything to main now, then confirm from GitHub that main has today's
changes and that no claude/ branches are still ahead"*

**Also:** if she suggests branch protection or a review step, say no. You're the only person working
in there, and a review with no reviewer just recreates the do-I-approve-this question.

**#tech-help if:** the merge reports a conflict she can't resolve.

### I worked in two places at once, did I lose anything

**What it looks like:** your local session says there's unsaved work while a session on your phone or
in the browser already pushed what looks like the same thing.

**Almost always: nothing is lost.** They're two real copies of the same repo and both have your work.

**Ask your Claude:** *"I've edited this repo from two sessions. Commit what's here, pull the other
changes on top, push, then show me from GitHub that both sets of changes are on main"*

**#tech-help if:** she reports a conflict, or the check at the end shows something missing. Say what
you changed in each place.

---

## Vera can't see or reach something

### Vera says a skill from the course doesn't exist

**Usually:** the skill exists, she just never pulled it down. Your copies live in your own repo and
they only arrive when she fetches them from the library.

**Try:** point her at the library by name and ask her to look again.

**Ask your Claude:** *"Which skills have you actually pulled down into my repo? Then check the VA
Optional starter library for the one I asked about and bring it in if it's missing"*

**#tech-help if:** she lists what she has and the skill genuinely isn't in the library. Say which skill.

### Vera can't connect to my email

**Usually:** the direct connection to that provider doesn't work, which is not the same as there being
no way in. There is often another route through a connector you already have.

**Try:** push back rather than accepting the first answer. This is the general move and it works on
far more than email.

**Ask your Claude:** *"That won't work for me. Look at every connector I already have and find another
route to my mail. I don't want to do anything by hand"*

**#tech-help if:** she's genuinely out of routes. Say which email provider and which connectors you
already have on.

### Can Vera work with the tool I use

**Ask her, she'll check.** Name the tool and she'll tell you whether it has a proper connection, a
ready-made connector, or nothing, and what that means for you.

**Ask your Claude:** *"Can you connect to [tool name]? Check whether it has an API or a connector and
tell me the best way for us to work with it"*

**The one rule worth knowing up front:** she can drive a website in your browser, and she can never
touch a program installed on your computer. So the online version of a tool is usually workable and
the desktop version usually isn't. If yours is desktop only, the way through is exporting your data
rather than trying to make her click inside it.

### Vera won't send my emails, she only writes drafts

**Not a fault, and not something to remove.** Two separate things are going on and both are intended.
The mail connector itself only ever creates drafts. And Vera holds everything for a human anyway:
nothing goes to a tenant, applicant, contractor or agency without you reading it first, and that holds
even when a routine runs while you're asleep.

**What to do:** read the draft and click send. That is the design, not a step waiting to be automated
away.

**Later:** sending can be automated properly once you get to the automation module. It's a build, not
a setting.

---

## Something changed that I didn't expect

### Vera wiped the formatting on my Google Sheet

**Usually:** a hard limit rather than something you're doing wrong. The Drive connection can rename and
move a file, but it cannot edit inside a document that already exists. So every "update" is really
read the old one, build a new one, delete the old one, and your formatting, views and filters go with
it.

**Try:** move that data into your hub, where updates are real edits and formatting survives. If it has
to stay a spreadsheet, batch your changes into one pass instead of asking for an update after every
finding.

**#tech-help if:** the data itself is wrong after a rebuild, not just the look of it. That's a
different problem and worth flagging.

### There are scheduled tasks I never set up

**Usually:** something got created as a schedule when it should have been a row in your routines table.
You should only ever have one scheduled task, the morning one. Everything else Vera does each day
lives as a row she reads.

**Try:** find out where they came from before you delete anything. A schedule you don't recognise is
usually a job you do want, in the wrong place.

**Ask your Claude:** *"Where did each of these scheduled tasks come from, and what does each one do?
Then move anything that should be a routine into my routines table and remove the extra schedules"*

**Worth doing:** ask her to walk you through what each one was for. It's the cheapest way to learn how
your own system is put together.

---

## It doesn't fit how I work

### The questions are all about rentals and that isn't my business

**Not a problem, and you don't have to work around it.** The material is written in landlord language
because that's where it started, and the system underneath doesn't care. It has been run against
brokerages, finance and professional services.

**Try:** tell her about your business, plainly. What you do, who's in it, what you're trying to get off
your plate. She adapts to that rather than to the example.

**Ask your Claude:** *"My business isn't rentals, it's [what you do]. Before we go further, ask me what
you need to know about it, then adjust how you work with me to match"*

### I want projects and folders like ChatGPT has

**Try the vault instead, it does the job better.** Mirror whatever folder structure you already have in
your head as folders in your Memory Vault, tell her once, and she files things there as you go.

Then any chat, including a brand new one you open next month, can ask for what's in a folder and get
it. Chats are throwaway. The vault is the part that remembers.

**Ask your Claude:** *"Set up these folders in my Memory Vault: [your structure]. From now on, file
everything we produce into the right one and tell me where it went"*

### Can I use Safari

**Chrome, or any browser built on it.** Edge and Brave both work with the same extension. Safari and
Firefox don't.

**And it's rarely urgent.** The extension only matters when Vera has to click around a site that has no
connection of its own. Everything else works from whatever browser you like.

---

## Chats and usage

### Should I start a new chat or keep going in this one

**Start a new one, once you've closed out.** Say "that's all" or "close session", let her wrap up and
save, then open a fresh chat for the next thing.

One long chat carrying everything you did all week gets slower, more expensive and easier to confuse.
Closing out is what moves what matters into your vault, so nothing is lost by starting again.

### I keep running out of usage

**Usually:** a heavier model, and long chats. The smarter the model, the more of your allowance each
message costs, and a chat that has been open all day is re-reading everything in it every time.

**Try:** close out and start fresh more often. Keep the strongest model for real work and let a lighter
one do simple reading jobs, if you need to stretch a smaller plan.

**#tech-help if:** you're running out fast on a normal day's work. Say roughly what you were doing.

---

## When to bring it to #tech-help

Post in `#tech-help` rather than DMing, so the answer reaches everyone hitting the same thing. Private
things only, DM instead.

**Bring it when:** you've asked your own Claude, done what she suggested, and it either didn't work or
she couldn't find the cause. That's genuinely the bar. Nobody expects you to solve everything alone.

**Include these four things**, because without them the first reply is always someone asking for them:

1. What you were trying to do
2. The exact words on your screen, copied or screenshotted
3. What you already tried, including what your Claude said
4. Whether you're on Local or Cloud, and Windows or Mac

**A short screen recording beats all of it** when something looks wrong and you can't put it into
words. It's what cracked the hardest problem this cohort has had.

**Nobody can see your machine.** Every answer you get in the channel is someone reasoning from what you
described, so the description is the whole game.
