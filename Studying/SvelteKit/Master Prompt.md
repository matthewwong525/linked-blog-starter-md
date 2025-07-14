
# Svelte 5 + Tailwind v4 — Coding Standards and Rules

---

## 1. Runes
- Always use Svelte 5 runes properly:
  - `$state`
  - `$derived`
  - `$effect`
  - `$props`
  - `$bindable`
- Never use old Svelte 3 syntax like `export let`.

---

## 2. DOM Events
- Use **DOM event attributes** directly on elements (e.g., `onclick={...}`).
- Never use `on:click`, `on:input`, etc.
- Allowed attributes include:
  - `onclick`, `onblur`, `onchange`, `ondblclick`, `ondrag`, `onmousedown`, `onmouseenter`, `onmouseleave`, `onmousemove`, `onmouseup`, and other standard DOM events.
- Never manually use `window.addEventListener` or `removeEventListener`.
- Always attach events through element attributes only.

---

## 3. Child Content (Slot Replacement)
- Always replace `<slot />` with `{@render}`.
- In child components:
  ```ts
  let { children } = $props();
  ```
- To render:
  ```svelte
  {@render children?.()}
  ```
- For multiple content areas, define multiple props — no named slots.

---

## 4. Language and Types
- Always use strict TypeScript:
  ```svelte
  <script lang="ts">
  ```
- Always strongly type every variable, prop, and function explicitly.

---

## 5. Props Typing
- Always inline prop types inside `$props()` destructuring.
- Never define a separate `type` or `interface` for component props.

Correct:
```svelte
<script lang="ts">
	let {
		children,
		title = 'Add New Ticket',
		description = 'Fill in the details for your new ticket',
		submitText = 'Add Ticket',
		cancelText = 'Cancel'
	}: {
		children?: () => any;
		title?: string;
		description?: string;
		submitText?: string;
		cancelText?: string;
	} = $props();
</script>
```

---

## 6. Styling
- Always use Tailwind utility classes for all styling.
- Never create external `.css` files.
- Never define custom CSS classes.
- All styling must be inline with Tailwind utilities.
- Always design with responsiveness and mobile-friendliness by default.

---

## 7. Transitions and Animations

### Usage
- Only use Svelte’s built-in `transition:` directive.
- Transitions must be attached directly to DOM elements inside `{#if}`, `{#each}`, or conditional blocks.

Example:
```svelte
{#if visible}
	<div transition:fade={{ duration: 300, easing: cubicOut }}>Content</div>
{/if}
```

### Requirements
- Always define reasonable `duration` (150–500ms).
- Always use a proper `easing` function.
- Transitions must animate both when elements **enter** and **exit** the DOM.
- Never interrupt user interactions during transitions.
- Always respect user system settings for `prefers-reduced-motion`.
- Transitions should enhance clarity, never cause confusion or distraction.

### Restrictions
- Never use raw CSS `@keyframes`.
- Never manually modify `display`, `visibility`, or other DOM styles.
- Never use external libraries like GSAP, Framer Motion, etc.

### Customizations
- When using custom transitions like `fly`, `blur`, etc., always configure parameters carefully.

Example:
```svelte
{#if open}
	<div transition:fly={{ y: 10, duration: 250, easing: cubicOut }}>Modal</div>
{/if}
```

---

## 8. Easing Functions
- Only use easing functions from `svelte/easing`.
- Never pass easing as a raw string like `'cubic-bezier(...)'`.

Allowed functions:
- `linear`
- `backIn`, `backOut`, `backInOut`
- `bounceIn`, `bounceOut`, `bounceInOut`
- `circIn`, `circOut`, `circInOut`
- `cubicIn`, `cubicOut`, `cubicInOut`
- `elasticIn`, `elasticOut`, `elasticInOut`
- `expoIn`, `expoOut`, `expoInOut`
- `quadIn`, `quadOut`, `quadInOut`
- `quartIn`, `quartOut`, `quartInOut`
- `quintIn`, `quintOut`, `quintInOut`
- `sineIn`, `sineOut`, `sineInOut`

Example:
```svelte
<script lang="ts">
	import { scale } from 'svelte/transition';
	import { cubicOut } from 'svelte/easing';

	let open = false;
</script>

<button type="button" onclick={() => open = !open}>Toggle</button>

{#if open}
	<div transition:scale={{ duration: 250, easing: cubicOut }}>
		Content
	</div>
{/if}
```

---

## 9. Scope and Styling Isolation
- Never directly modify `document.body`, `window`, or `globalThis` inside components.
- Never modify global styles like scroll locking (`overflow: hidden`) inside component code.

Incorrect (forbidden):
```ts
$effect(() => {
	if (isOpen) {
		document.body.style.overflow = 'hidden';
		return () => {
			document.body.style.overflow = '';
		};
	}
});
```

- All scroll locking, styling, and visibility must be controlled inside the component itself through:
  - Tailwind utility classes
  - Conditional rendering (`{#if}`)
  - State-based control

- If global effects are truly necessary, delegate them to a higher-level layout or utility component — never directly in small components.

---

## 10. Form Handling
- Never use `|preventDefault` inside event bindings.
- Always manually call `preventDefault()` in event handlers.

Correct:
```svelte
<form onsubmit={(e) => { e.preventDefault(); handleSubmit(); }}>
```

---

## 11. Accessibility (Clickable Elements)
- Always use native interactive elements like `<button>` or `<a>` for click actions.
- Never attach `onclick` to `<div>`, `<span>`, or other non-interactive elements.
- Never manually add ARIA roles to static elements to fake button behavior.
- Always prefer:

Correct:
```svelte
<button type="button" onclick={...}>Click me</button>
```

- `<button>` automatically supports keyboard accessibility (`Enter` and `Space`).
- Follow official Svelte accessibility warnings:
  - [a11y-click-events-have-key-events](https://svelte.dev/e/a11y_click_events_have_key_events)
  - [a11y-no-static-element-interactions](https://svelte.dev/e/a11y_no_static_element_interactions)

---

## 12. Accessibility (Form Labels)
- Every `<label>` must be properly associated with a form control (`<input>`, `<select>`, `<textarea>`, etc).

Preferred way (using `for` + `id`):
```svelte
<label for="color" class="text-sm font-medium">Color</label>
<input id="color" type="color" class="..." />
```

Alternative way (nest input inside label):
```svelte
<label class="text-sm font-medium">
	Color
	<input type="color" class="..." />
</label>
```

---

✅ **Summary**:  
- No exceptions to these rules.  
- Always prioritize accessibility, clarity, component scope, and maintainability.  
- Consistency across the entire project is mandatory.

---