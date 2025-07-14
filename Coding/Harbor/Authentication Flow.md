
# Continue With Email
- After setting the email it will send an mail to the email for confirming the sign in.
- When it comes to UI, it shows a popup to let users know to check their email that was set.
- The button when clicked must be disabled for $N$ seconds with a timer on its label.

Email Sign In Link
- http://localhost:5173/account/signup/callback?apiKey=AIzaSyDtrfaYigKySBJIlib_EKBdG8C_wsLucs8&oobCode=SmaZcGeOVux4uQEP64rq-x1Q6W-3XNuUet4J2vGV2HcAAAGXDzRNbA&mode=signIn&lang=en

# Allowing CORS Policy for Shared Resources

# Protecting Routes and Redirects
- Routes can be protected using hooks.server.ts, which runs on the server **before every page or API endpoint is resolved**. This allows you to intercept requests and redirect or deny access based on authentication or other logic. It is ideal for auth guards, logging, role-based access control, redirects based on user state.

# Cloud Firestore Read and Write Access Rules


# Accessing Firestore with Server Hooks


# Environment Variables


# REFERENCES
## Protecting Routes with Hooks, and User Roles, and Redirects
https://youtu.be/K1Tya6ovVOI

