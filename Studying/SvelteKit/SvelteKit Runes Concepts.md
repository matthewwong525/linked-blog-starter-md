
# Props

# Dynamic Components With Parameters (Snippets)

Snippets, and [render tags](https://svelte.dev/docs/svelte/@render), are a way to create reusable chunks of markup inside your components.

```html
{#snippet FormButton(name)}
	<h1>{name}</h1>
{/snippet}

{@render FormButton("Hello World")}
```


