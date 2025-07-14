
**UI**
- [x] Prevent next button from resetting the scroll in registration form inside /event/
- [x] Implement skeleton loading
- [x] Disable “End Date” picker when “Till Late” is selected.
- [x] Show preview of uploaded event banner image.
- [ ] Display filename and file size below or beside the event banner image.
- [ ] Replace bold, italic, and bullet buttons with shadcn toggle group components.
- [ ] Allow users to select a location via a map.
- [ ] Location drawer must include:
	Location name (editable)
    Read-only latitude and longitude fields.
- [x] Fix ticket creation and editing behavior.
- [x] Ensure correct currency symbol appears based on selected 3-letter currency code.
- [ ] Update visibility icon to reflect current selection (Public vs Private).
- [x] Use preset color palettes throughout the app.
- [ ] Make hours and minutes scrollable in datetimepicker component
- [ ] Ensure AM/PM selection works properly in datetimepicker component.
- [ ] Make sure the design colors of skeleton card is the same as the unloaded image skeleton part
- [x] Allow inviters, tickets, payments, socials, and location forms to render data table
- [ ] Use form actions for draft, and adding event
- [ ] Ensure form state is synced and submitting properly.
- [ ] Implement full form validation.
- [x] Persist event creation form data when tab refreshed or navigated away (save to sessionStorage)
- [ ] Replace tabs with select dropdown for ticketing

**Onboarding**
- [ ] After signing in, always redirect users to /onboarding until onboarding is complete (enforce using hooks.server.ts).
- [ ] Block manual navigation to other routes before onboarding is done.

**Mobile UI**
- [x] Make the “Add Tickets” drawer scrollable for smaller screens (e.g., Nest Hub).
- [ ] Fix navigation burger menu toggle.
- [ ] 
**Chore**
- [x] Organize fields
- [ ] Organize all components


---

**Dates**
- When datetimepicker is selected, it should automatically select the current day with a default time of 12:00 AM

**Event**
- image
- name
- dates
- location
- socials
- visibility
- category
- shortDescription
- aboutEvent
- houseRules
- ticketing
- formInformation
- inviters
- tickets
- payments