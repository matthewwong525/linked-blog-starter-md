
# Dates Drawer
Handles the drawer and adds data through `onAdd` function.
Data can be set initially by optional `data` prop.
Can be toggled with optional `show` prop.


```
<DatesDrawer
	bind:type={dateDrawerType}
	bind:data={dateDrawerData}
	bind:show={showDateDrawer}
	onAdd={onAddDates}
	onSave={onSaveDates}
	onCancel={() => {}}
/>
```
# DatesTable
Displays data supplied from data prop.
Handles rows through `onEdit` and `onDelete` function props.F



# FormDrawer
- triggerTitle
- contentTitle
- actionTitle
- cancelTitle
- class
- open
- draggable
- action
- close
- children

```typescript

	const clearInvitees = () => {
		event.invitees = [];
	};

	const editInvitee = (invitee: string, index: number) => {
		inviteesIsEditMode = true;
		inviteesDrawerOpen = true;
		inviteesFieldValue = invitee;
		inviteesEditRowIndex = index;
		inviteesInputTypeValue = 'field';
	};

	const resetInviteeDrawer = (): void => {
		inviteesIsEditMode = false;
		inviteesFieldValue = '';
		inviteesListValue = '';
	};

```


# General Case for Drawer Opening
- Assign editRowIndex from index params
- Open drawer
- Change mode to edit


- [ ] Editing dates
- [ ] Till late toggle for disabling end dates
- [ ] Set location UI and logic
- [ ] Add event must reset all values of fields that are under ticketed when ticketing is set to non ticketed
- [ ] Add event functionality and upload to database
- [ ] Draft event functionality must be uploaded to firestore
- [ ] Draft event and add event must have a dialog popup to confirm
- [ ] The draft and add event buttons must present a loading icon when clicked
- [ ] Event creation page must only be available if signed in otherwise route to auth login/signup page