`+page.server.js` file can export actions, which allow you to `POST` data to the server using `<form>` element.


## PageLoad
Executes code before rendering `+page.svelte` inside `+page.server.ts`.
Used to load data before page loads.
```
export const load: PageLoad = async (): PageData => {
	return {};
}
```

## Request Handler

`export const `
## Create API Routes with `+server.ts`
This route can export functions corresponding to HTTP methods: `GET`, `PUT`, `POST`, `PATCH`, and `DELETE`.

