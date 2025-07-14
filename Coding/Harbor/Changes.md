As of June 08, 2025

- **Replaced drawer components with dialogs** for a cleaner, more intuitive user experience.
    
- **Added “Edit Profile” button** to allow quick profile updates.
    
- Introduced a dedicated **profile layout** for improved organization and structure.
    
- **Enhanced all client-side navigations** to be smooth and fluid.
    
- **Event creation** now supports both **drafting** and **publishing** events.
    
- Added **client-side form validations** for event creation to catch errors early.
    
- **Image upload support** has been added to the event posting flow.
    
- **Revamped the header design** to improve responsiveness on all screen sizes.
    
- **Increased padding and spacing** throughout the site for better mobile usability.
    
- Improved **layout responsiveness** on the event creation page.
    
- Adjusted **button padding** for both “Add Event” and “Save Draft” for a more consistent look.
    
- Redesigned the **image drag-and-drop interface** for event creation.
    
- Introduced a **new welcome page** with smooth, engaging animations.
    
- Accessing the `/profile` route now **loads user data on the server**, avoiding slow client-side fetches.
    
- Implemented **authentication cookies** to support secure server-side operations via Firebase Admin SDK.
    
- Secured `/profile` and `/event/create` routes using **server-side hooks**.
    
- The UI now **reactively updates on profile edits** for immediate feedback.
    
- **Auth user profiles now sync with Firestore**, ensuring consistency between services.
    
- The site now **fully supports Server-Side Rendering (SSR)** for faster initial loads and SEO benefits.
    
- The **“Continue with Email”** auth flow has been redesigned to be **dynamic** — users are now intelligently directed based on account existence, eliminating the need for a /onboarding route.
    
- Authentication now uses **API endpoints and Firebase Admin SDK** to securely check if an account exists before login.


---


As of June 10, 2025
- Added a **“Cover Photo”** label to the event creation form.
    
- Event cover image filenames now use **secure, randomly generated UUID v4** values to prevent filename collisions and accidental overwrites.
    
- Improved the **event posting logic** with more robust error handling and clearer control flow.
    
- Fixed dialog trigger buttons so they no longer submit the form unintentionally, preventing unwanted field validation popups.

- Renamed **“Add Event”** button to **“Publish Event”**
    
- Updated icons for both **Draft Event** and **Publish Event** buttons to better reflect their actions


- Added confirmation dialogs when clicking draft event and publish event to avoid users performing actions in case of a misclick
- Introduced new managing events design
- Added 'There are no events available at the moment.' in navigation pages if there's no existing events under that category.


**VALIDATORS**



```
name: string;
dates: EventDate[];
location: {
	name: string;
	address: string;
	city: string;
	lng: number;
	lat: number;
};
category: string;
visibility: string;
ticketing: string;
tickets: {
	name: string;
	description: string;
	dueDate: Date;
	price: {
		currency: string;
		value: number;
	};
	color: string;
}[];
socials: EventSocials[];

export interface EventSocial {
	platform: string;
	value: string;
}

export interface EventDate {
	startDate: Date | null;
	endDate: Date | null;
	tillLate?: boolean;
}
```

**FORM** (For Publishing)
- Event name must exist
- Location must exist
- Dates must exist
- Category must exist
- Visibility must exist
- If ticketing is 'ticketed' then:
	- Tickets must exist
- If socials exist (length > 0) then:
	- URL must also exist

**FORM** (For Drafting)
- Event name must exist

**DATES**
- Start Date must exist and either End Date or Till Late
- If end date exist then end date must be greater than start date.
- If either end date or tillLate exist then there must be start date
- If tillLate is true always remember that end date turns null automatically, I informed this for context.

**INVITEES**
- Person names must be validated (allowed chars only)
- Blank names are not allowed

**TICKETS** (DONE)
- Price must be a valid number and must exist.
- All optional except price.

**PAYMENTS** (DONE)
- Method, name, and number must exist


Image (Optional)

Name

Dates (Optional)
- Start Date
- End Date
- Till Late

Location (Optional)
- Name
- Address
- City
- Longitude
- Latitude

Socials (Optional)
- URL

Short Description (Optional)

About the Event (Optional)

House Rules (Optional)

Invitees (Optional)

Tickets (Optional)

Payments (Optional)


**To be implemented**
- [ ] "Sign in with Google" auth for both desktop and mobile (`/account/login`)
- [ ] Dynamic profile navigation based on account type (personal/organization) (`/profile`)
- [ ] Displaying error after client-side validations (`/event/create`) (**WIP**)
- [ ] Managing events (`/profile`) (**WIP**)
- [ ] Event published page (`/event/success`)
- [ ] Analytics page (`/event/analytics`)
- [ ] Users can view other users (`/profile?id=<id>`)
- [ ] Migrate events data to new schema from Firestore
- [ ] Blank cells must display '--' for all tables (`/event/create`)
- [x] Changing profile picture on (`/profile`)
- [x] Navigation bar for (`/profile`)
- [ ] Field validations for Edit Profile (`/profile`)
- [ ] Updating profile picture must overwrite the image in firebase storage to prevent increase in storage memory size. (`/profile`)
- [ ] Cancel button in Edit Profile Dialog (`/profile`)
- [ ] Adding Bio in (`/profile`)
- [ ] Filtering, sorting, searching, grid view, and list view, updated category icons for (`/profile`) (**WIP**)
- [ ] Responsive event management design in (`/profile`) in all screen sizes
- [ ] Add 'All Day' option for creating event dates
- [ ] Add bold, italic, hyperlink for event descriptions
- [ ] Clicking and viewing events must go back to its previous page history with the "Explore Events" button
- [ ] Add name, username, bio, socials, and school edit profile limit logic validations, and its display.
- [ ] Increase top padding for header
- [x] Change name, description, due date to "Ticket Name", "Ticket Description", "Deadline"
- [x] Change "Form Information" to "Information Needed to Collect"
- [ ] Add Optional Indicator to "House Rules"
- [x] Change location type and its ui to "venueName" and "city" only
- [ ] Add 'To Be Announced', 'Onwards', 'Till Late', 'All Day', 'Not Available', ''
- [ ] Check image url in profile if it still valid, exist, and the response is 200 (GOOD), otherwise fallback to user icon.

**Bugs**
- When signing up, there's no name in (`/welcome`) and cannot access (`/profile`)

**Ideas**
- Public and private tickets and tickets that's assign to a person with permissions
- Event comments

**Soon**
- Image file size optimizations for all image uploads and previews.
- Update and migrate all image banners in both firebase storage and firestore events collection fields with secure v4 UUID's
- Notification Icon that can say "You're approved"
