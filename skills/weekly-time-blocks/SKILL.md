---
name: weekly-time-blocks
description: "Builds the owner's time-blocked plan for the coming week and for a single day: their best hours for their business goals, meetings stacked on two meeting days, a daily selling hour, one social media block, a daily admin buffer and an operations block, around every event already on the calendar. Also sets up their booking pages so outside calls can only land in the meeting windows. Trigger on 'plan my week', 'time block my week', 'block my day', 'plan tomorrow', 'my day blew up', 'redo today's blocks', 'approve my week', 'stack my meetings', 'set up my booking links', or when a weekly planning routine fires."
---

# Weekly Time Blocks

**Version: 1.0 - 2026-10-11**

Plans the owner's week the way Dan Martell's *Buy Back Your Time* describes a Perfect Week: a
template that gets reused, with similar work stacked together so the owner switches gears as few
times as possible. The assistant proposes, the owner approves, and only then does anything reach
the calendar.

## First run: the intake

Nothing in this skill is the owner's actual schedule. Every time, day and minimum below is a
starting suggestion. The owner's answers live in one profile file in their second brain,
`reference/time-blocks-profile.md`, copied from `profile-template.md` in this folder. **Their file
wins over everything written here.** Ask one short question at a time, in this order, and write each
answer down as it comes:

1. **When it runs.** Which day and time the draft should arrive, and where (a private chat channel
   with a mention works well, so they get notified). Suggest the night before their week starts.
2. **The planning window.** Which days and hours they are open to having work planned. Do not
   assume Monday to Friday or nine to five. Anything outside the window gets no work blocks.
3. **Best work and thinking hours.** When they think sharpest and when their energy dips. Growth
   and selling go in the best hours; admin and in-the-business work go in the dips.
4. **Confirm their goals.** Read each company's `goals.md` in their vault and play the goals back
   for a yes. If none exist, interview them to write one per company: the goal, what done looks
   like, the number to watch, the next three steps. Ask which goal wins when two compete, the fewest
   goal blocks a week each company must get, and whether one time-critical item may jump ahead in a
   deadline week.
5. **Pick their block types.** Offer each as a suggestion with a starting default they can change,
   drop or rename, and ask for any others:
   - **Daily ritual:** meditation, journaling, reading or prayer, about 15 minutes at the start of
     every day, with the draft suggesting what to do in it.
   - **Workout:** how long (including travel and changing), what time, which days.
   - **Admin buffer:** a daily block left empty on purpose for the fires that show up, in the
     afternoon dip.
   - **Work IN the business:** operations, tenant communications, maintenance, leasing. One or two
     fixed weekly blocks so it stops leaking into every day.
   - **Growth and planning (goal blocks):** building systems, products and strategy toward their
     goals, in their best hours.
   - **Selling hour:** sales, follow-up, outreach, posting. A short block every working day.
   - **Social media:** ONE weekly block to plan and create next week's posts together, in the
     afternoon rebound. Never inside a goal block. Posting and engagement stay in the selling hour.
   - **Weekly priorities:** at the start of the week, 90 minutes or less.
   For each, ask how long, how often, and whether it has a fixed time or can float. Give each a
   fixed category name; the week's task goes inside it.
6. **Meeting days.** Ask which two days should hold every meeting, podcast, interview, one-to-one
   and sales call. Suggest the days that already hold the most fixed meetings, one internal (team,
   one-to-ones) and one external (outside calls, peer groups). Then ask which of their recurring
   calls are **optional** (group calls they often skip). Optional calls are planned over, never
   planned around.
7. **Fixed anchors.** Recurring calls, family commitments, meals, sleep. Booked events always win.
8. **Booking pages.** Where outside people book them, and set those pages up to open only inside
   the meeting-day windows (see below).
9. **Review-only first.** The draft never writes to the calendar until they switch it on, after a
   few weeks of drafts they would have approved as they were.

Anything left unanswered gets a sensible default, written in the file as OPEN, and the draft says
which defaults it used.

## The rules the week is built on

**Batch, never split.** Each kind of work gets ONE block, placed right next to related fixed
events. Two windows for the same thing, or a "plan on Tuesday, create on Friday" split, undoes the
batching. Offer a split only if the owner asks for one.

**Peak hours go to goal work only.** The owner's best hours hold the goal blocks: the most useful
task for one business goal, with a one-line reason. No email, chat, or admin in the peak.

**Two meeting days.** Every meeting, podcast, interview, one-to-one and sales call lands on the two
meeting days, back to back. The other days take no new meetings.
- One meeting day is usually internal (team, one-to-ones) and one external (outside calls, peer
  groups, podcasts).
- On a meeting day, put the meetings in one stretch and the workout (or the next big block) right
  after, so the day has one meeting stretch, not two.
- Any new meeting that lands on a build day goes in the plan's **collisions** list, with a
  suggested slot on the next meeting day. Exceptions: a group call the owner does not control, and
  personal appointments.

**A selling hour every weekday.** Follow-ups, outreach, direct messages, and posting. Selling is a
daily habit because follow-ups depend on timing. On meeting days, this hour is where booked sales
calls go. On build days, it is outreach only.

**One social media block a week.** Planning and creating next week's posts in one sitting, in the
afternoon energy rebound, never inside a goal block. Posting and engagement stay in the daily
selling hour.

**An admin buffer every weekday, left empty on purpose.** It catches whatever fires that day.
Never pre-fill it. Keep roughly a fifth of working time unblocked overall.

**Weekly priorities take 90 minutes or less**, at the start of the week, before the first meeting.

**Booked events always win.** Never move an event already on the calendar. If one lands on a
block, move the block to the next open slot of the same energy, the same day if possible.

## Booking pages that only open on meeting days

The calendar plan only holds if outside people cannot book around it. Set the owner's booking
pages so they offer slots ONLY inside the meeting-day windows.

- **One window per meeting day**, joined to that day's other meetings. Not two.
- **Every booking page uses the same windows**, and all of them check the same calendar, so a
  booking on one page removes that time from the others.
- **Buffer between appointments: zero.** A ten-minute buffer cuts a one-hour window from four
  fifteen-minute calls to two. Stacking is the point.
- **Tool choice:** Google Calendar booking pages allow several pages on a free account. Calendly's
  free plan allows only one event type, so a second length means paying. Check the owner's plan
  before suggesting a tool.
- **Google booking pages cannot be edited through the Calendar connector or API.** Do not promise
  to change them that way. Give the owner the exact settings (name, days, times, buffer) as a short
  table and let them make the change. If you have a browser that holds their login, you may try it,
  but say so first.
- **Renaming a page keeps its link**, so links already sent keep working.
- **Verify, do not assume.** Open each page's Preview and read the slots for NEXT week. The current
  week can hide slots because of the minimum notice setting. Report what the page offers, page by
  page.

## Building the weekly plan

Each run reads, in this order: the profile; each company's `goals.md` in the vault; the calendar
for the planning window; open tasks from their task boards (their database's tasks table, plus any
other board they use); email that needs them (through `landlord-inbox-handler/`); anything that
changed in their vault that week; and their Command Center briefing if they have one. Each goal
block gets the single most useful task for that goal, with a one-line reason and its source.

1. **Lay the anchors.** Sleep, the workout, meals, and every booked event.
2. **Name the week's ONE thing.** One outcome that makes the rest of the week easier, in one
   sentence at the top.
3. **Fill the peak with goal blocks.** Meet each business's minimum from the profile. The priority
   business gets the ONE thing and the first block on at least three days. One time-critical item
   from another business may jump ahead when it has a hard deadline inside the week; say why.
4. **Stack the meeting days**, then place the selling hour every weekday.
5. **Place the social media block, the operations block and the admin buffer.**
6. **Hand off what is not theirs.** A task the owner's delegation notes give to someone else gets
   a "hand to" line and no block.
7. **List what did not fit** under "not this week". The plan is finite on purpose.

Each block is named by its **category**, which never changes week to week (for example "Business A
Growth", "Selling Hour", "Social Media", "Admin Buffer"). The week's task for that block goes in its
description, with a one-line reason.

## Showing it and getting approval

Send a short message with the draft plus a link to a page that shows the week as a time grid (an
Artifact, see `artifacts/`), and log the run. Under the week: collisions, what was handed off, what
did not fit, and any defaults used.

On changes, revise only the affected days and ask again. No reply means nothing reaches the
calendar. Once the owner has switched calendar writes on, approval creates one event per block that
is not already booked: title = the category only, description = "Task:" then "Why:", no reminders.
After that they are ordinary events the owner moves freely; never touch them again.

## Single day

On "block my day", "plan tomorrow" or "my day blew up": read today's calendar and the approved
plan, keep the workout and any peak hours left, re-block only what moved, and show the before and
after. If the peak is already gone, move the top deep-work task to tomorrow's first block rather
than squeezing it into the dip.

## Running it every week

A weekly routine (Sunday early morning works for most owners) can draft the week automatically.
See `cloud-vs-local/` before choosing where it runs, and keep the approval step: the routine
drafts, the owner approves.

## Where the method comes from

| Thinker | What the plan does with it |
|---|---|
| Dan Martell, *Buy Back Your Time* | A reusable Perfect Week; similar work stacked; meetings batched onto set days |
| Gary Keller, *The ONE Thing* | One outcome named first, protected in the morning |
| Cal Newport, *Deep Work* | Deep work in long blocks; when the day breaks, re-block what is left |
| Daniel Pink, *When* | Analytic work at the peak, admin in the dip, creative work in the late-day rebound |
| Dan Sullivan | Buffer time planned on purpose |
| Alex Hormozi, Jeb Blount | Selling every day in a short, focused block |
| Oliver Burkeman | A finite plan with a "not this week" list |
