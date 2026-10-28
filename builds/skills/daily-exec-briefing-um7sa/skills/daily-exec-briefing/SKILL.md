---
name: daily-exec-briefing
description: "Build {{EXECUTIVE_NAME}}'s one-doc daily meeting briefing from the {{MAILBOX_EMAIL}} Microsoft 365 calendar. Use when {{ASSISTANT_NAME}} asks for the daily exec briefing or runs /daily-exec-briefing."
---

<!-- exchange:setup -->
## Before you start
This has details to fill in. The first time it runs, ask the user for each one, then use the answer wherever its blank appears:
1. {{EXECUTIVE_NAME}}
2. {{MAILBOX_EMAIL}}
3. {{ASSISTANT_NAME}}
4. {{TIME_ZONE}}
5. {{TIME_ZONE_LABEL}}
6. {{INTERNAL_TEAM_DESCRIPTION}}
<!-- /exchange:setup -->

# Daily Exec Briefing

One doc, one snapshot per real meeting, readable in 90 seconds.

## 1. Pull the day
- Use the Microsoft 365 connector (`outlook_calendar_search`) on {{MAILBOX_EMAIL}} with query `*`, `order: oldest`, `limit: 25`, after 00:00 / before 23:59 of the target day. Default target day = today; if run the evening before (after 5 PM), use tomorrow and say so in one line.
- Page with `nextOffset` until all events are in.
- `read_resource` each kept event for the full body (agenda, pre-read notes).
- Times are in the event's time zone (usually {{TIME_ZONE}}). Show them as {{TIME_ZONE_LABEL}}.

## 2. Keep only real meetings
Skip silently:
- Lunch blocks ("Lunch – Do Not Book", solo lunch holds)
- Personal appointments (doctor, orthodontist, school pickup, kid/family items)
- Focus time, "do not book", travel/drive-time holds, any event titled Hold/HOLD/Tentative
- Cancelled, declined and all-day events

Keep meal meetings that have a guest (e.g. "Breakfast – Founder Intro") and calls with an outside party even if no attendees are listed (e.g. "Co-investor Call – External Fund").

## 3. Fill gaps (light touch)
For meetings with no agenda, search Outlook mail (`outlook_email_search`) for the company or person name. Use only what a source states: related upcoming meetings (IC, term sheet calls, pipeline reviews), prior meetings with the same person, deck/pre-read asks. Never guess. If nothing turns up, write "No agenda on the invite."

## 4. Flag external attendees
Internal = {{EXECUTIVE_NAME}}, {{ASSISTANT_NAME}}, {{INTERNAL_TEAM_DESCRIPTION}}. Everyone else is external.
At the top of each meeting, one line per external guest:
`⚠️ Name — Company (Title)`
- Company/title come from the display name or event title. If missing: `company not listed` / `Name not on invite — Company`.

## 5. Format
Doc title: `Daily Briefing — Tue, Oct 27`
First line: `N meetings · start–end {{TIME_ZONE_LABEL}} · External guests at <times>`

Then, per meeting, `## 9:45 AM · <Meeting title>`, then sections in this exact order:
1. ⚠️ external flags (if any)
2. **Meeting Snapshot** — day, date · time range {{TIME_ZONE_LABEL}} · location. Attendees: list guests other than {{EXECUTIVE_NAME}} ({{ASSISTANT_NAME}} only for the {{EXECUTIVE_NAME}}/{{ASSISTANT_NAME}} sync).
3. **Why This Meeting Matters** — 2 sentences max. Lead with the stakes; tie to what's coming (IC vote, board meeting, Thursday dinner).
4. **Agenda Items** — bullets: `Item — context` (one short clause of context from the invite or mail).
5. **Decisions Needed** — always last, every bullet bolded. If none are clear, use **Watch for: …** grounded in the source, or **None listed on the invite.**

## 6. Rules
- Direct, scannable, no filler. Plain words, no AI phrasing. Whole doc fits one page.
- Never include compensation, legal or personnel details, even if they appear in notes. Valuations and specific deal terms stay out unless they are the agenda item itself.
- Don't extrapolate past what the invite or mail says.

## 7. Deliver
- Create a Claude Doc (Docs type) with the content above and open it.
- If {{ASSISTANT_NAME}} asks for email: save it as a draft (not sent) in {{MAILBOX_EMAIL}}, subject `Daily Briefing — <Day, Mon D>`, with a link to the doc at the bottom. Never send.
- Reply in one line: meeting count, external count, and anything {{ASSISTANT_NAME}} should fix on the calendar (e.g. an invite with no attendees).
