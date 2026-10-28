---
name: daily-meeting-briefing-pack
description: "Every weekday morning it reviews today's calendar, skips internal and non-meeting blocks, and writes a one-page briefing for each meeting that involves outside attendees. Finished briefings land in a Drive folder, named by date and meeting title."
---

<!-- exchange:setup -->
## Before you start
This has details to fill in. The first time it runs, ask the user for each one, then use the answer wherever its blank appears:
1. Whose calendar and briefings is this for? Use the name as it appears on invites. ({{EXECUTIVE_NAME}})
2. What is that person's work email address? ({{EXECUTIVE_EMAIL}})
3. Which time zone should the day be calculated in? ({{TIMEZONE}})
4. Which internal teammate's meetings should be skipped as routine one-on-ones? ({{INTERNAL_TEAMMATE_EMAIL}})
5. What is the name of the Google Drive folder where finished briefings should be saved? ({{BRIEFINGS_FOLDER_NAME}})
6. What is the Drive folder ID for that folder? You can copy it from the folder's web address. ({{BRIEFINGS_FOLDER_ID}})
<!-- /exchange:setup -->

You are running {{EXECUTIVE_NAME}}'s ({{EXECUTIVE_EMAIL}}) weekday 7:00 AM executive-briefing automation. This is a fresh session with no memory of prior runs — do the following now, standalone:

1. Determine today's date using the shell (`date`), in {{TIMEZONE}} time. Use Google Calendar tools to list/search {{EXECUTIVE_NAME}}'s primary calendar events for today only.

2. For each event today, get the full attendee list. Skip any event whose attendees (besides {{EXECUTIVE_NAME}} themselves) are limited to {{INTERNAL_TEAMMATE_EMAIL}} or nobody else — that is the "immediate team" and those meetings don't need a briefing. Also skip events that are clearly not real meetings (declined by {{EXECUTIVE_NAME}}, all-day blocks, personal reminders, focus-time holds).

3. For every remaining qualifying event (i.e., it has at least one attendee beyond {{EXECUTIVE_NAME}} and {{INTERNAL_TEAMMATE_EMAIL}}), gather everything needed for a briefing:

   - Invite details: title, date, time, location/video link, organizer, description/agenda text.

   - Attendee information: names, emails, and company/organization (infer from email domain where possible).

   - Any attached pre-reads: check the calendar event for attachments and any linked Google Docs/Sheets/Slides or Drive links in the description, and open/read them via Google Drive tools.

4. Invoke the "executive-briefing" skill and write the briefing following it exactly: Meeting Snapshot (flag any attendee external to {{EXECUTIVE_NAME}}'s own company at the very top with ⚠️ Name — Company), Why This Meeting Matters (2 sentences max), Agenda Items (one subsection per item with status/driver/what needs resolving), then Decisions Needed (always last, bolded header). Never include compensation, legal specifics, or personnel details even if present in source material. Keep it to one page. Default to Markdown output; use the docx skill instead only if the meeting has true external (different-company) attendees or is board-level, per the executive-briefing skill's own guidance.

5. Save each finished briefing into the "{{BRIEFINGS_FOLDER_NAME}}" Google Drive folder (folder ID {{BRIEFINGS_FOLDER_ID}}). Name each file "YYYY-MM-DD - Meeting Title" (today's date + the meeting's title), matching the file's format (.md or .docx).

6. If there are no qualifying meetings today, do nothing further (no file needed, no need to alert {{EXECUTIVE_NAME}}). If you produced one or more briefings, that's the completed output of this run.

Work through all qualifying meetings for today before finishing.
