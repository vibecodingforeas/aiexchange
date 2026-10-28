---
name: "calendar-meeting-audit"
description: "Scan upcoming calendar events and flag meetings missing implied attendees, meetings with no attendees, and meetings with no agenda. Use when asked to audit, check, or clean up a calendar."
---

# Calendar Meeting Audit

Read-only check of upcoming meetings. Finds three problems:
1. **Missing people** - the title or description names someone who isn't invited.
2. **No attendees** - the event looks like a meeting but nobody else is on it.
3. **No agenda** - a real meeting with nothing in the description.

Never change the calendar during the audit. Fixes happen only after the user confirms each one.

## Inputs (use defaults if not given)
- **Date range:** default is today through the end of the next 5 business days.
- **Calendar:** default is the user's primary calendar. If they name an exec's calendar, audit that one instead.

## Step 1: Pull events
- Use the Google Calendar connector (list_events). If the user works in Outlook, use the Microsoft 365 calendar search instead.
- Get title, time, description, attendees (names, emails, response status), organizer, recurrence, and attachments.
- Skip: all-day events, cancelled events, events the calendar owner declined, and other people's working-location or OOO entries.

## Step 2: Sort each event

**Blocks (skip all checks):** events that are clearly for one person. Signals: lunch, focus, work block, heads down, DNS, hold, busy, OOO, travel, flight, commute, drive, gym, workout, appointment, pickup, reminder, prep, admin time, personal, or a title that is only a task ("Review deck", "Expenses").

**Meetings (run all checks):** everything else, especially titles with 1:1, sync, call, chat, meeting, interview, intro, catch up, check-in, review with, kickoff, "with", "w/", "/", "<>", "x", or a person or company name.

If unsure, treat it as a meeting and mark the flag as "check" rather than a definite problem.

## Step 3: Missing people check
Look in the title and description for people or groups who should be there:
- Names: "{{EXECUTIVE_NAME}} / Sarah 1:1", "Coffee with Tom", "Jane <> Raj intro"
- Companies: "Acme call", "{{COMPANY_NAME}} x Acme"
- Emails or @mentions in the description
- Teams: "Marketing sync", "Legal review"

Match each one against the attendee list:
- A person matches if their name matches an attendee's display name or email (first name to email prefix is fine, e.g. "Sarah" = sarah.lee@...).
- A company matches if any attendee has that company's email domain.
- A team matches if a group address or at least one person from that team is invited. If you can't tell, mark it "check."
- Ignore the calendar owner, rooms, and resources.
- Note if the named person is invited but declined - that's worth flagging too.

## Step 4: No attendees check
Flag any meeting (from Step 2) with zero attendees other than the owner. Say who the title suggests should be there, if anyone.

## Step 5: No agenda check
A description counts as **no agenda** if it is empty or only has conferencing boilerplate (Zoom, Meet, Teams links, dial-ins, "Join with Google Meet").
It counts as **having an agenda** if it has topics, goals, questions, bullet points, or a linked/attached doc (agenda, notes, running doc, deck).

Be practical. Don't flag:
- Blocks from Step 2
- Social events: coffee chat, lunch with, happy hour, team dinner, celebration, birthday
- Recurring 1:1s that link a running notes doc
- Interviews that have candidate info or a scorecard linked

Prioritize flags for meetings with external attendees, 3+ attendees, or 45+ minutes.

## Step 6: Report
Keep it short and scannable. Group by day, in time order. Only list events with a flag.

```
**Calendar audit: [date range]**
[X] meetings checked, [Y] flagged

**Tue, Oct 14**
- 10:00 Acme / {{EXECUTIVE_NAME}} call - 🔴 Missing people: no one from Acme invited
- 1:00 Sync with Jordan - 🟠 No attendees: Jordan not on invite
- 3:00 Q4 planning (6 people) - 🟡 No agenda
```

Key: 🔴 missing people, 🟠 no attendees, 🟡 no agenda. Add "(check)" to any low-confidence flag.

End with one line offering fixes: add the missing attendees, or draft a short agenda for the flagged meetings.

## Fixing (only when asked)
- Adding attendees sends invites. List exactly who will be added to which event and get a clear yes before updating.
- For agendas, draft them in chat first. Only write them to the event description after the user approves.
