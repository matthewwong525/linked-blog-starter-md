
# Routes
- event/create
- event/\[id]/edit

# Event/Create
- The page does not require any data loaders.

# Event Form Drawer
- title
- action
- open = $bindable()
- class
- draggable

- **Dates**
	- dateEditTableRow
	- dateDrawerOpen
	- dateDrawerClose
- **Location**
	- locationEditTableRow
	- locationDrawerOpen
	- locationDrawerClose
- **Socials**
	- socialsEditTableRow
	- socialsDrawerOpen
	- socialsDrawerClose
- Visibility
- Category
- Short Description
- About the Event
- House Rules
- Ticketing
- Form Information
- **Invitees**
	- 
- **Tickets**
- **Payments**



day, hour, minute


```
if day is false and hour selected:
	today()
	setHour(hour)

if day selected and hour selected:
	select day
	select hour
```

	


---

## Forcing Onboarding Redirects
- The problem with this is when a user selects a link that uses the `goto` function, it causes client-side navigation which doesn't run or re-run `hooks.server.ts` middleware.
- One case problem is that navigation requires `goto` functions which is faster than `window.location.href` which executes hook redirects and full page reloads.
- Alternatively, we can utilize client hooks `hooks.client.ts` to perform functions before and after navigations. There are two functions `beforeNavigate()` and `afterNavigate()` that can perform user onboarded checks.

### First Case (Using Client Hooks)
Client hooks are executed for every client-side `goto()` navigations.

Expected flow
> [!info] Continue With Email Flow
> 1. Enter email
> 2. Send magic link
> 3. Authenticate and Send POST API request to create a `__session` cookie from Firebase Admin
> 4. Force redirect users to `/onboarding` if its user data `onboarded` is `false` using both client and server hook redirects.

1. The `authStore.userOnboarded` will be updated once in the root `+layout.svelte` with the help of `auth.onAuthStateChanged()` listener in order to perform single firestore read which prevents multiple reads.
2. The user will utilize `beforeNavigate()` to perform an `authStore.userOnboarded` check. If true then it forces the user to redirect to `/onboarding` route.

## Second Case (Email Checks Before Auth)
Firebase Admin allows the server to retrieve users by email with `adminAuth.getUserByEmail()` function.

The `Continue With Email` button authentication flow must redesign to

> [!info] Continue With Email Flow
> 1. Enter email
> 2. Check if user firestore data exist
> 3. If firestore data exist then send magic link and authenticate
> 4. If not exist then proceed to `/onboarding` route then send magic link, authenticate, and create firestore user data


### My Personal Opinion:
For me I feel like the second case works best because at least when the user enters its email, it will not authenticate even if user tries to navigate away from the `/onboarding`, and it's smooth and easy to work with than dealing with client hooks where I have to check onboarded doc before navigations, and track onboarded in authStore.

