
# Cookies
- **What**: Small key-value data stored in the **browser** and sent automatically with every request to the same origin.
- **Where stored**: On the **client** (browser).
- **Use case**: Store session IDs, tokens, preferences, etc.
- **Expires**: Can be session-based or persistent.
- **Secure**: Can be marked as HttpOnly, Secure, SameSite.
- Commonly used for authentication (e.g. session ID or JWT token).

# Sessions
- **What**: A server-stored set of data (session object) tied to a unique session ID, often stored in a **cookie**.
- **Where stored**: Session data is on the **server**, and only the session ID is on the client.
- **Use case**: Store login state, cart items, etc.
- **Expires**: After inactivity or logout.
- Used in traditional server-rendered apps (e.g. Express, Django).

# Tokens (JWT)
- **What**: A self-contained, encoded string (often a **JWT** - JSON Web Token) that carries user info and claims.
- **Where stored**: On the **client**, usually in **cookies** or **localStorage**.
- **Use case**: Stateless authentication (token tells the server who the user is).
- **Expires**: Defined inside the token (exp field).

## SSR (Server-Side Rendering)
- **What**: The server generates the **HTML** on each request (instead of letting the client build it).
- **Use case**: Faster first load, better SEO, secured data access.
- **Where runs**: Code runs on the **server**, not in the browser.
