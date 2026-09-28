# Working rules for this project

The whole value of this site is that nothing on it is guessed. Protect that above speed.

## The one rule

Never write a rule into `data/states.json` that you did not read in a primary source.
A primary source is the program administrator's own guidelines, FAQ or application
materials, or the enabling statute. A capital provider's marketing page is not a
primary source, even when it is probably right.

If a field is unknown, the value is the literal string `"Not verified"`. The site
renders that in amber. An unknown displayed honestly is worth more than a plausible
number, because the entire pitch is that the other maps guess.

## What counts as done for a state

Every field in the schema filled or explicitly `"Not verified"`, plus:
- at least one entry in `sources` with a working URL
- at least one entry in `administrators` with a name, a role and a URL
- `verified_on` set to the date you actually read the source
- `verification` set to `"verified"`, or `"partial"` if the state has no single
  statewide program and the state-level answer is therefore incomplete

## When two sources disagree

Do not pick one silently. Fill the `conflict` object with both claims and a
`resolution` naming which governs. This has already happened twice and it is the
site's most distinctive feature, not an edge case. Administrators outrank government
agency pages on their own program's terms.

## Things that are easy to get wrong

- Many states have no statewide program. Ohio runs on Energy Special Improvement
  Districts, Florida on interlocal districts, Pennsylvania county by county, Nevada
  jurisdiction by jurisdiction, Missouri through several districts, California across
  several platforms. For these, `verification` is `"partial"` and `access` must explain
  the mechanism rather than implying a single answer.
- A state can have more than one administrator. Texas has the Texas PACE Authority and
  Lone Star PACE. New York splits between NYCEEC and EIC. List them all.
- Program terms change by statute. Minnesota went from 20 years to 30 in 2024 and the
  EPA still publishes the old figure. Re-check anything older than about a year.

## Who this is for

Administrators are the primary audience, lenders are the beneficiaries. See
`research/AUDIENCES.md`. This ordering is load-bearing: build for lenders and the site
becomes deal sourcing, which is a crowded lane and breaks the verification loop that
keeps the data current.

## The structured block

`states.json` carries a `structured` object per state for sorting and comparison.
`null` means not verified. It never means "no limit" and must never render as a blank or
a dash. The prose fields stay authoritative; `structured` is a sorting key. Never render
`cap_pct` without `cap_type`, since a 35% cap on loan to value and a 35% cap on eligible
construction costs are different numbers.

## Out of scope for now

County and municipal opt-in coverage. It is the most valuable layer and needs
participating-jurisdiction lists from each administrator. Do not fake it with
state-level shading.

## Voice

Plain sentences. No em dashes. Never use the word "actually".
