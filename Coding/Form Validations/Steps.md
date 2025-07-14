1. **Create the form with HTML and CSS** (as you've done)
    
2. **Use `<form>` with SvelteKit's enhanced form actions**:
    
    - Set up a `+page.server.js` file to handle form submissions
        
    - Define actions in your server file
        
3. **Add client-side validation** (optional but recommended):
    
    - Use JavaScript or libraries like `zod` for schema validation
        
    - Provide immediate feedback to users
        
4. **Handle form submission on the server**:
    
    - Process the form data
        
    - Validate server-side (never trust client-side validation alone)
        
    - Handle errors and return appropriate statuses
        
5. **Provide feedback to the user**:
    
    - Success messages
        
    - Error messages
        
    - Loading states


---

# 1. Creating the UI and Input Bindings
In this code we create the UI with basic HTML elements and a script that holds the input bindings by the input values.
```html
<script lang="ts">
	let username: string = $state('');
	let password: string = $state('');
</script>

<div class="flex min-h-screen w-full items-center justify-center bg-gray-50 p-4">
	<div class="w-full max-w-md">
		<div class="space-y-6 rounded-xl bg-white p-8 shadow-lg">
			<div class="space-y-2 text-center">
				<h1 class="text-3xl font-bold text-gray-900">Welcome back</h1>
				<p class="text-gray-500">Enter your credentials to access your account</p>
			</div>

			<form class="space-y-4">
				<div class="space-y-2">
					<label class="block text-sm font-medium text-gray-700" for="username">Username</label>
					<input
						bind:value={username}
						id="username"
						type="text"
						placeholder="Enter your username"
						class="w-full rounded-lg border border-gray-300 px-4 py-2 outline-none transition focus:border-blue-500 focus:ring-2 focus:ring-blue-500"
					/>
				</div>

				<div class="space-y-2">
					<label class="block text-sm font-medium text-gray-700" for="password">Password</label>
					<input
						bind:value={password}
						id="password"
						type="password"
						placeholder="Enter your password"
						class="w-full rounded-lg border border-gray-300 px-4 py-2 outline-none transition focus:border-blue-500 focus:ring-2 focus:ring-blue-500"
					/>
				</div>

				<div class="flex items-center justify-between">
					<div class="flex items-center">
						<input
							id="remember-me"
							type="checkbox"
							class="h-4 w-4 rounded border-gray-300 text-blue-600 focus:ring-blue-500"
						/>
						<label for="remember-me" class="ml-2 block text-sm text-gray-700">Remember me</label>
					</div>

					<a href="#" class="text-sm text-blue-600 hover:text-blue-500">Forgot password?</a>
				</div>

				<button
					type="submit"
					class="w-full rounded-lg bg-blue-600 px-4 py-2 font-medium text-white transition hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-blue-500 focus:ring-offset-2"
				>
					Sign in
				</button>
			</form>

			<div class="text-center text-sm text-gray-500">
				Don't have an account? <a href="#" class="text-blue-600 hover:text-blue-500">Sign up</a>
			</div>
		</div>
	</div>
</div>

```


# Create Data Loader
Data can be loaded from the server using raw values or loading the data from the database.
```typescript
// +page.server.ts
// Load data from db for example
export const load: PageServerLoad = async (): PageData => {
	return {
		username: 'riniwtz',
		password: 'V9r!pX2#qLmZ7bT'
	};
};
```
To access or load the data object in the client-side, create props in `+page.svelte` file.
```html
<script lang="ts">
	type Props = {
		username: string;
		password: string;
	};
	const { data }: { data: Props } = $props();

	let username: string = $state(data.username);
	let password: string = $state(data.password);
</script>
```

# 2. SvelteKit Form Actions

## The Usual Way
Creating API endpoints for forms uses `RequestHandler` which can be imported with `import type { RequestHandler } from './$types'`.
```typescript
// +server.ts
import type { RequestHandler } from './$types'

type Data = {
	success: boolean
	errors: Record<string, string>
}

// This is not limited to POST, we can also use DELETE
export const POST: RequestHandler = async ({ request }) => {
	// FormData does not require imports
	const formData: FormData = await request.formData();
	// Data can be loaded with const data = formData.get('')

	const data: Data = {
		success: false,
		errors: {}
	}
}
```
In the long run this is tedious because it requires having logic flow for both the client and the server. Therefore, an efficient way to implement this is with **SvelteKit Form Actions**.

## SvelteKit Form Actions
```typescript
// +page.server.ts
import type { Actions } from '@sveltejs/kit';
import type { PageData, PageServerLoad } from './$types';

export const actions: Actions = {
	login: async ({ request }) => {
		const formData: FormData = await request.formData();
		console.log(formData);
	},
	register: async (event) => {}
} satisfies Actions;
```
The `login` and `register` keys are actions that can be called in `+page.svelte` by `<form>` action attribute.
```html
<form method="POST" action="?/login">
	...
</form>
```
As shown here, if a button submits, it appends `?/login` to the url and automatically pass all the input values to the server.

> [!note] <form\> Action Attribute
One thing to note here is that `?login` is a query parameter. To actually call form actions with SvelteKit, we must put `/` between the `?` and the name of the key. Therefore, it becomes `?/login`.

> [!note] <input\> Name Attribute
One thing to also consider is that the `formData` will return an empty array if `<input>` elements inside the `<form>` doesn't have a `name` attribute. 

# Form Action Attribute
We can use the `formaction` attribute for buttons which prevents from running the `action` attribute that was set in `<form>`. 
```html
<form method="POST" action="?/login">
	<!-- If click, it runs the login action -->
	<button type="submit">
		Sign in
	</button>
	
	<!-- If click, it runs the signout action instead of the login account that was in the <form> parent element -->
	<button type="submit" formaction="?/signout">
		Sign out
	</button>
</form>
```

# Fail Method
Inside our action functions we can return a fail whenever we need. The `fail` function is 
```typescript
import type { fail, Actions } from '@sveltejs/kit';

// fail(status: number, data?: Record<string, unknown> | undefined): ActionFailure<Record<string, unknown> | undefined>
// The HTTP status code. Must be in the range 400-599.

// The second argument accepts and creates an ActionFailure object.
return fail(400, {})
```



# 3. Progressive Form Enhancement
