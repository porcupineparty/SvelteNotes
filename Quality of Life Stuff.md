
## Aliases

There are some things that we can do to make our job a little easier with our project. First we can create an alias for when we specify our components. We can create aliases in the svelte.config.js file 

```javascript
const config = {

    // Consult https://kit.svelte.dev/docs/integrations#preprocessors

    // for more information about preprocessors

    preprocess: vitePreprocess(),

  

    kit: {

        // adapter-auto only supports some environments, see https://kit.svelte.dev/docs/adapter-auto for a list.

        // If your environment is not supported, or you settled on a specific environment, switch out the adapter.

        // See https://kit.svelte.dev/docs/adapters for more information about adapters.

        adapter: adapter(),

        alias: {

            "@": "./src",

        }

    }

};
```

Here we specify that whenever we use the `@` symbol this will point to our `src` directory 

***For Example*** If we want to import a component that is found in the `src/lib/components` file we can specify in our main `+page.svelte` file at the top this line of code that will import our file 

```typescript
import Nested from "@/lib/components/nested.svelte";
```

This way we always have access to our components in a very easy manner.

We can then use the component in our project by using the tag 

```svelte
<Nested />
```

## HTML Tags 

Strings are usually inserted as plain text, but with svelte you can use variables to store HTML strings which can be very useful

*For Example* you might have a string that includes something like this 
```javascript
<script>
	let string = 'this string contains some <strong>HTML!!!</strong>';
</script>
```

You could then use that in a paragraph tag like the one below:


```html
<p>{@html string}</p>
```

**Word of caution:** Svelte doesn't perform any sanitization of the expression inside the `@html` code. This is not an issue if something is trusted but make sure that you manually escape something if it is from untrusted content. 


