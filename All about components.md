
### 1. **What is a Component?**

In Svelte, a component is a reusable building block of the UI. Each component is defined in its own `.svelte` file, encapsulating HTML, CSS, and JavaScript.

### 2. **Basic Structure of a Component**

A typical Svelte component has three main sections:

- **Script Section**: Contains JavaScript logic.
- **Markup Section**: Contains HTML-like markup.
- **Style Section**: Contains CSS styles scoped to that component.

### 3. **Components are always capitalized**

When importing components you should always capitalize them in order to not bug other typescript or tool imports.

*For Example:* 
```typescript
import ContextOptionsModal from "@/components/ContextOptionsModal.svelte";
```
*See the Quality of Life Stuff file for more info about the @ syntax*

Then to use that same component

```svelte
<ContextOptionsModal />
```

### 4. **Props and Reactive Variables**

- **Props**: You can pass data to components using props, which are declared using the `export` keyword. ***See more about Props in the Props file (under construction)***

- **Reactive Variables**: Variables can be made reactive using the `$:` syntax.


```svelte
<script>
  export let count = 0;
  $: doubled = count * 2; // Reactive variable
</script>
```

### 5. **Slots**

Slots allow you to create flexible components by letting users inject content.

#### Example:

svelte

```svelte

<!-- ParentComponent.svelte --> 
<MyComponent>   
	<p>This is slot content!</p> 
</MyComponent>  
<!-- MyComponent.svelte --> 

<slot></slot>
```


### 6. **Context API**

For sharing data between deeply nested components without prop drilling, you can use Svelte’s context API with `setContext` and `getContext`.

#### Example:

// Provider.svelte
```javascript
<script>
  import { setContext } from 'svelte';
  setContext('key', 'value');
</script>
```

// Consumer.svelte
```javascript
<script>
  import { getContext } from 'svelte';
  const value = getContext('key');
</script>
```

### 7. **Lifecycle Hooks**

Svelte provides lifecycle functions to run code at specific times in a component’s lifecycle:

- `onMount`: Runs when the component is first rendered.
- `beforeUpdate`: Runs before the DOM updates.
- `afterUpdate`: Runs after the DOM updates.
- `onDestroy`: Runs when the component is removed from the DOM.
```typescript
<script>
  import { onMount } from 'svelte';

  onMount(() => {
    console.log('Component mounted');
  });
</script>
```

### 8. **Scoped Styles**

Styles defined in a component are scoped to that component by default, preventing them from affecting other components.