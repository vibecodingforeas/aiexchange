---
name: "event-venue-sourcing"
description: "Use when {{EXECUTIVE_NAME}} asks to source a venue, find hotels for an offsite or event, or send a hotel RFP: gather missing details, shortlist 5 hotels via Workgrounds, recap the RFP, send only on an explicit yes."
---

# Event Venue Sourcing

{{EXECUTIVE_NAME}}'s standard process for finding a hotel venue for a group event and sending an RFP through Workgrounds.

## Hard rule
Never send an RFP, contact a hotel, or book anything without {{EXECUTIVE_NAME}}'s explicit yes in chat. That covers `create_request` with a confirm_token, `update_request` with a confirm_token, `ask_proposal_question`, `request_proposal_extension`, and any booking. Searching and previewing are fine without asking.

## Step 1: Fill in what's missing
Check {{EXECUTIVE_NAME}}'s message for each item below. Ask only for what's missing, in one round (use AskUserQuestion when available, max 4 questions per call).
- **City** (and preferred area, e.g. walkable downtown)
- **Dates**: check-in and check-out. Room nights are check-in through the night before check-out.
- **Headcount** and rooms needed per night
- **Vibe**: boutique vs. large, star rating
- **Meeting space**: capacity, setup (conference, classroom, theater, U-shape, etc.), A/V, which days, breakouts
- **Meals**: which meals, which days

Also ask before the RFP (Workgrounds requires an answer, never guess):
- If a hotel can only offer part of the room block, is its offer still wanted?
- Is the on-site meeting room a hard requirement?
- If meeting days are ambiguous relative to the room nights (e.g. arrival day vs. checkout day), which days?

## Step 2: Search and shortlist 5
Load the tools with ToolSearch: `select:mcp__Workgrounds__find_hotels,mcp__Workgrounds__get_hotel`.

1. Run `find_hotels` with `location`, a tight `radius_miles` (about 1.5 for "walkable downtown"), `min_star_rating`, `min_event_space_capacity`, and `max_room_count` (about 300 for boutique). Sort by distance.
2. Run `get_hotel` on the strongest candidates to check the actual meeting rooms, not just the largest space. Look for a right-sized main room plus breakouts.
3. Pick the top 5. For each one give: name as a link (the hotel's Workgrounds `url`), stars, room count, and 1-2 lines on why: location, feel, specific meeting rooms with capacities, any catch.
4. Add a short "left out" list for notable hotels that didn't make it, and why (e.g. no private meeting room, not actually downtown, too few rooms).
5. Flag that listed capacities are maximums (usually theater style). For a conference or classroom setup, rooms rated close to the headcount will feel tight.
6. Note that rates and availability come back only after an RFP is sent.

Keep it short and scannable. Plain language, no filler.

## Step 3: Recap the RFP before sending
When {{EXECUTIVE_NAME}} picks hotels, load `select:mcp__Workgrounds__create_request` and call it WITHOUT confirm_token to get the preview. Nothing is sent at this stage.

Show {{EXECUTIVE_NAME}} a plain-English recap:
- Request name and the Workgrounds org it will be filed under
- Hotels, linked
- Room block: rooms per night, dates, total room nights, check-in and check-out
- Whether partial room offers count
- Meeting room: setup, capacity, A/V, days and hours, required or not
- Meals: which, which days, headcount, where served
- Alternative dates (leave empty unless {{EXECUTIVE_NAME}} said they're flexible)
- Questions for hotels (up to 3; suggest useful ones like cancellation/attrition terms or holding breakout rooms)
- **Choices I made that you didn't specify**: always list these (e.g. meeting hours, room type, headcount used for meals vs. room size, request name)

If the preview warns about a possible duplicate request, ask whether it's the same trip; if so, use `update_request` instead of creating a new one.

If a tool call is blocked or fails, say so plainly, confirm nothing was sent, and still show the recap.

## Step 4: Send only on an explicit yes
After {{EXECUTIVE_NAME}} explicitly approves, call `create_request` again with the identical arguments plus the preview's confirm_token. If any argument changed, preview again and re-confirm.

Then reply briefly: which hotels were notified, the org it's under, and a link to the request (`urls.self`). Offer one next step: when proposals arrive, compare them side by side (room rate, meeting room fees, F&B minimums, cancellation terms).
