## DOM Basic Reactivity

Svelte allows you to keep the DOM in sync quite well with your application state *ex. In response to an event*

An event handler in svelte looks kind-of like this for the most part:

```svelte
<button on:click={increment}>
	clicked {count}
	{count === 1 ? 'time' : 'times'}
</button>
```

We will talk about this in further detail in the event handler section and other sections but for now know that you can listen to any DOM event, i.e. *on:click, on:hover, etc . . .* and sets it to a function like I did up above. The curly braces are there to first include the `count` variable which should be specified in the `<script>` tags of your page. This button also includes a ternary expression which is basically an `if-else` statement that specifies if the count is `1` then it will say `clicked 1 time` and if the count is anything else it will say `times`

Here is the Javascript code block for the function `increment` that is very simple
```javascript
<script>
	let count = 0;

	function increment() {
		count += 1;
	}
</script>
```

This is really cool because svelte updates the DOM **Automatically** providing for a very streamlined process of development. 

## Declarations

*Reactive Declarations* are a cool addition to svelte as well. Whenever a variable that you have linked to another variable, or a component that you have linked to something else changes, you can set up a *reactive declaration* so that whenever the *base* variable is updated the *reactive* variable changes as well!

```svelte
let count = 0;
$: doubled = count * 2;
```

***If a reactive statement consists entirely of an assignment to an undeclared variable, Svelte will inject a `let` declaration on your behalf.***

```html
<p>{count} doubled is {doubled}</p>
```

Of course, you could just write `{count * 2}` in the markup instead — you don't have to use reactive values. Reactive values become particularly valuable (no pun intended) when you need to reference them multiple times, or you have values that depend on _other_ reactive values. Because they will always keep their value.


Note that reactive declarations and statements will run after other script code and before component markup is rendered.

## Statements

Just like we can use Reactive values, we can run *reactive statements* as well!

Maybe you need to debug something and you log the value of `count` whenever it changes

```svelte
let count = 0;

$: console.log(`the count is ${count}`);
```

This log statement will run EVERY time count changes! 

You can add *curly braces* `{}` to the  reactive statement to log multiple things at the same time. 

```svelte
$: {
	console.log(`the count is ${count}`);
	console.log(`this will also be logged whenever count changes);
}
```

You can even run logic on the reactive variable like an if block 

```svelte
$: if(count >= 10){
	alert('count is dangerously high!')
	count = 0;
}
```

## Updating Array

One important thing to note is that because svelte's reactivity is triggered by assignments, using array methods like `push` and `splice` won't automatically cause updates. Even if we use something like numbers.push(...) it won't show up on the page until the DOM is reloaded. 





