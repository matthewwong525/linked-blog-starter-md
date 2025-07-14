Any server can send instructions (as http `Set-Cookie` header fields) to the client.

When a client sees the cookie instructions (`Set-Cookie` header fields), their job is to store them immediately.

Cookies are stored on the client's disk (until they expire).

A cookie has a value, an "HttpOnly" flag, an expiration date, a domain and a path (and some other exotic options you probably don't need).

It's best practice to flag your cookies as "HttpOnly", which instructs the browser to hide said cookies from JavaScript.

After a cookie has been stored, the browser will automatically inject `Cookie` header fields into any http request going out to the domain and path indicated in the cookie, effectively "returning" the cookie value to the server.

The server's job (Sveltekit's job) is to parse those `Cookie` header fields and pass them down in your code.

This is how the web is meant to work, this is how true sessions work, using cookies.

For example, if you want to set a `session-id` cookie, your server would send the following header in a response

`Set-Cookie: session-id=asd-123-qwerty-456; HttpOnly; Domain=my-website.example; Path=/admin; Expires=Wed, 1 Jan 2026 08:00:00 GMT`

This will create a `session-id` cookie available only under `my-website.example/admin`.

When the client gets the response with the `session-id` cookie "instruction", it will create a `session-id` cookie with the value `asd-123-qwerty-456` .

From that moment on, all http requests from the client to `my-website.example/admin`, will ALWAYS include the `session-id` `Cookie`, until the cookie expires.

When does a cookie expire? In the example above it will expire on January 1st, 2026, at 8 in the morning.

Or when the user clears their cookies manually.

The most important thing to understand is that you should NEVER handle cookies yourself on the client.

While running on the client, don't set your own cookies for each request through JavaScript (fetch, xmlhttprequest, etc).

Cookies are supposed to be set by the server and read only by the server.

Basically while writing JavaScript code in your client side, you're supposed to treat cookies as an [IoC](https://en.wikipedia.org/wiki/Inversion_of_control) service.

You should know they exist, you should know how they work because those are useful skills for debugging, but you shouldn't worry about them ever.

Setting cookies, updating cookies, evicting cookies, anything that has to do with cookies, must be handled by the server.

In your specific example, you've got a sveltekit server and a go server.

From what I'm gathering, the go server is the one generating these cookies.

All you have to do is to make sure all http headers are correctly sent to the Go Server and received by the Svelte Client.

So if you're architecture looks something like this:

1. Svelte Client ---- (requests data) ---> Svelte Server
    
2. Svelte Server --- (requests data) ---> Go Server
    
3. Go Server --- (returns data) ---> Svelte Server
    
4. Svelte Server --- (returns data) ---> Svelte Client
    

You need to make sure that in step 2) all `Cookie` header fields are sent to the Go Server, and that in step 3) all `Set-Cookie` header fields are received by the Svelte Server and subsequently also by the Svelte Client.

So:

1. Svelte Client --- (requests data) ---> Svelte Server
    
2. Svelte Server --- (requests data + include `Cookie` header fields) ---> Go Server
    
3. Go Server --- (returns data + include `Set-Cookie` header fields) ---> Svelte Server
    
4. Svelte Server --- (returns data + include `Set-Cookie` header fields, again) ---> Svelte Client
    

Note how in step 1) nothing changes, that's because the browser does it all in your stead.

Pay attention that usually cookie names and values are encoded as url or base64, Go (depending on the server) and SvelteKit will decode them before passing them to you, so you will probably need to encode them back before forwarding those headers.

Good luck.

Reference: https://www.reddit.com/r/sveltejs/comments/1ijol0w/cant_understand_cookies/
