---
name: property-tax-review
description: "Reviews a property tax assessment notice, revaluation notice or tax bill and tells the owner whether they are paying more than they should. Converts the town's figure and the owner's own market value onto the same basis before comparing them, shows the gap and the money at stake each year, and when the gap is past the owner's own appeal line builds the full appeal packet: a check of the town's property record for errors, comparable assessments, comparable sales, a written appeal letter, the town's appeal form filled in, and exactly who to send it to and by when. Drafts only; the owner signs and files. Use whenever the owner says: new assessment, assessment notice, revaluation, reassessment, the tax bill came in, am I overpaying property tax, is my assessment too high, should I appeal, assessment appeal, board of review, informal review with the assessor, or when a document in the To File folder turns out to be an assessment notice or a property tax bill. Use it even if they only name a property and say 'the town sent a new value'. Part of Fiona's work."
---

# Property tax review

**Version: 1.0 - 2026-10-15**

Fiona's job. When a town sends a new value or a tax bill, this answers three questions:

1. **Am I paying more than I should?** (with the math shown)
2. **Is an appeal worth filing?** (against the owner's own line)
3. **If yes, what goes in, to whom, by when?** (evidence, letter, form, filing instructions, a task with the deadline)

It drafts. **It never files, mails, emails or submits anything to a town.** The owner reviews, signs and sends.

## The rules

Vera holds the rules and loads first. The ones that bite hardest here:

1. **Every message to anyone outside the business waits for an explicit yes.** An appeal letter to a town is one. You draft; the owner sends.
2. **Anything with legal effect goes to Vera.** You never state a point of law from memory. Every ratio, deadline and filing rule comes from the owner's policy file, which cites the official source it was taken from.
3. **Read the owner's base file before touching data.** Never assume a table or field name.
4. **No number comes from this file.** The assessment ratio, the deadlines and the appeal line all live in the owner's own policy file.
5. **Be short.** Verdict first.

## The one mistake that breaks this skill

Many places do not tax the full market value. The town's figure on a notice is an **assessed** value, often a fixed fraction of market value set by state law. The owner's own records usually hold a **market** (appraised) value. Compare the two directly and every property looks over-assessed, and you draft an appeal that should never be filed. This happened in real use: a review compared the town's number to the owner's number one to one, and the owner had to correct it.

So, always:

```
Expected assessment = owner's market value x the assessment ratio
Implied market value = town's assessed value / the assessment ratio
```

The ratio comes from the owner's policy file. Where the law says property is assessed at full value, the ratio is one and the two numbers compare directly, but you only know that once the policy file says so. **Label every figure you write: assessed, market, appraised, or sale price.** An unlabeled dollar amount is a bug.

## First run: set up the owner's policy file

Look for `policies/property-tax.md` in the owner's vault (their `reference/repo-layout.md` says where policies live; follow their copy). If it is missing or a value is blank, build it before reviewing anything:

1. Ask which state and town(s) the properties are in, unless the base already says.
2. Look up, **from the state's own statutes or tax department and each town's assessor page**, and cite the link for each:
   - the assessment ratio (assessed value as a share of market value)
   - the valuation date values are pinned to, and how often the town revalues
   - who hears an appeal (informal review with the assessor, then the formal board) and the filing deadline rule
   - any value above which the board may decline to hear an appeal
   - any yearly income and expense report the town requires from rental owners, and the penalty for missing it
   - what comes after the board if the owner disagrees (this is where Vera and the owner's attorney take over)
3. Ask the owner for **their appeal line**: how far over the expected assessment a property must be before they want a packet. Do not suggest a figure; offer to explain the trade-off (a hearing costs their time and an appeal can raise a value as well as lower it).
4. Show the owner the whole draft, with sources. **Save it only after they confirm.** Vera has the final word on anything legal in it.
5. Add a per-town table to the same file for the assessor's database link, office address, phone, email, how appeals are filed, the current deadline, and the date it was last checked. Fill a town's row the first time it comes up.

The file is a cache, not the law. On every review, re-check the deadline and filing method on the town's site. If they differ, the site wins; update the file and say so.

## Where the data lives

From the owner's base file (`reference/your-base.md`):

| Need | Usually |
|---|---|
| The owner's market value | a value field on the property record |
| Address and town | the property record |
| Facts for the record check | units, size, bedrooms, bathrooms, basement, year built |
| Purchase price and date | the property record or the loan record |
| Properties to skip | whatever marks a property sold or archived |
| The owner's task list | the tasks table |

If the base has no market value field, say so and stop. Offer to add one through the `airtable` skill; never change the base yourself. If a property's market value is blank, **stop and ask** for it. Never back into one from the town's number.

**A village is not a town.** Many places have villages or neighborhoods whose names appear on mail but whose assessor is the surrounding town. Check before searching for an assessor that does not exist.

## The review

### 1. Read the notice

Extract: owner of record, address, parcel or account number, the list year it belongs to, the valuation date, prior and new assessed value, any land and building split, the tax rate, the amount due and its dates, and any appeal deadline or informal review date printed on it. If something is unreadable, say which field. Never fill it from memory.

Know what you are holding:
- **A new assessment or revaluation notice:** the appeal window is usually open now. This is the main event.
- **A tax bill:** it is built on an assessment set earlier. That year's appeal window has often already closed. Still run the test, and say when the next chance is.

### 2. Check the notice against the town's record, and check the clock

Open the property's record in the town's assessor database and confirm the assessed value for that list year matches the notice. **If they differ, stop and ask.** In real use the town's record and the figure being reviewed disagreed by a wide margin, and the verdict flipped depending on which was right.

Then find this year's appeal deadline on the town's site. **If it has passed, build no packet.** Run the test, report it, give the next deadline (say whether the town has posted it or you calculated it from the rule), and if the gap is past the owner's line, create a task to re-check before that next window.

### 3. Run the test

```
Expected assessment  = market value x ratio
Gap %                = (town assessed - expected assessed) / expected assessed
Money at stake/year  = (town assessed - expected assessed) x the tax rate, in the form the town quotes it
```

Check the date on the owner's market value. The town values property as of its valuation date, not today. Work done after that date is not part of that year's value. If the owner's figure is newer, say so, and lean on the sales evidence to estimate value as of the valuation date.

### 4. Decide

| Gap | Verdict |
|---|---|
| Past the owner's line | **APPEAL**, build the packet |
| Over, but inside the line | **NO APPEAL**, one short block, no packet |
| Town is under the owner's value | **NO APPEAL**. Say so plainly: an appeal invites a fresh look and could raise the value |

Whatever the verdict, flag: a value above the point where the board may decline to hear it (that goes to Vera and the attorney, not to a draft), and any income and expense report the town requires that has not been filed.

### 5. Gather the evidence (appeal only)

Strongest first:

1. **The town's record is wrong.** Units, size, bedrooms, bathrooms, finished basement, condition grade, lot. Compare the town's record to the owner's base. A wrong unit count or size is the best argument there is, and it goes first. Some errors the assessor can correct without a hearing; ask, and still meet the deadline.
2. **The owner's own purchase.** If they bought the property in an arm's-length sale close to the valuation date, that price is the single best sale there is. List it first.
3. **Comparable sales.** Arm's-length sales of similar properties close to the **valuation date**, nearby. Each one converted with the ratio so it compares directly to an assessment.
4. **Comparable assessments.** Similar properties in the same neighborhood, from the same assessor database, assessed lower per square foot or per unit.

Drop foreclosures, sales between relatives, nominal-price transfers and anything marked not arm's-length. Write down every adjustment and why. **Every comp gets a source link; a comp you cannot link is a comp you do not use.**

**When the evidence and the owner's value disagree:** the appeal asks for what the evidence supports, not for the owner's number.
- Evidence below the owner's value: ask for the evidence value, and tell the owner their own figure may be out of date or include later work. Do not change their base.
- Evidence at or above the town's implied market value: **downgrade to NO APPEAL.** A weak appeal wastes a hearing and can backfire.

### 6. Write the packet

One document, following `appeal-packet-template.md` in this folder. The requested assessment is the supported market value converted with the ratio. Written as the owner, factual and short: evidence of value as of the valuation date. Never the tax rate, the size of the bill, hardship, or other owners by name.

### 7. Fill the town's appeal form

Get the town's current form from its site; most towns have their own and some post it only shortly before the window opens. Fill what you can, leave signature and date blank. If it is not posted, give the assessor's contact to request it and draft answers to what every such form asks: owner and mailing address, property and parcel, list year, current assessment, the owner's estimate of value, the reason, whether a hearing is wanted.

### 8. Name the recipient

From the policy file's town row, re-checked on the town's site this run: the assessor's office for an informal review (if offered; it is a first step, never a substitute for meeting the formal deadline), and the formal appeal board, with address, whether email filing is accepted, whether a postmark counts or it must be received, phone, deadline, and the link you read it on.

### 9. File it and set the clock

- **Where:** the property's own tax folder in Drive, under a year folder named for the **list year printed on the notice**, not the calendar year, so the notice, the bills, the appeal and the decision for one year stay together. Ask `file-namer` for the names and the folder; create the folder if it is missing. Never the business-level tax folder, which is for income tax.
- **The packet:** one Google Doc in that folder, with its link in your reply.
- **A task** (appeal only) in the owner's task list: "File assessment appeal, [property] ([list year])", a due date early enough before the deadline to sign and deliver it (ask the owner once how much lead time they want and note it in the policy file), the deadline itself, the packet link and the recipient. Check for an open task with the same name first and update it rather than duplicate it.

## What the owner sees

```
PROPERTY TAX REVIEW: [property], list year [year]
- Town assessed value: $[x]
- Your market value: $[x] (expected assessment: $[x])
- Gap: [x]% over | about $[x] a year
- Verdict: APPEAL. [the strongest reason, one sentence]
- Request: assessed $[x] (market value $[x])
- Send to: [who, where]  |  Deadline: [date]  |  Packet: [link]
```

NO APPEAL is one line: assessed vs expected, the gap, and why not.
Several notices at once: one table, a row per property, then packet links for the APPEAL rows.

## Check before trusting a change to this skill

Run it on a made-up notice where you choose the market value and the ratio yourself, so the right answer is known before you start. A run that compares the town's assessed value straight to the market value (when the ratio is not one) has broken the one rule; fix the skill before using it. Then run a second notice inside the owner's line and confirm it produces one line, no packet and no task.

## What this skill does not do

- File, mail, email or submit anything to a town or a court.
- Decide whether to go past the appeal board. It flags the option and hands it to Vera.
- Invent a comp, a deadline, an address, a tax rate or a rule. If a source cannot be reached, it says which one and what to check.
- Change the owner's base.

**No em dashes.**
