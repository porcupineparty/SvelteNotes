
Props are used to pass data from one component down to the children of that component. To do that we have to declare *properties* we do that with the `export` keyword. 

```svelte
<script lang=ts>
	export let answer;
</script>


<p>The answer is {answer}</p>
```

To use this information in a child  component you then specify the import of that component like so:

```svelte
<script lang=ts>
	import ComponentName from'./ComponentName.svelte';
</script>

<ComponentName answer={42} />
```

It might seem a little counterintuitive that you are importing the component to set the answer in the other component but it will make sense the more you do it. 

### A Good Way to Think About It

A good way to think about it is that you have your main component, that component imports other components into it's file effectively making these *Nested* components. These nested components can have values passed to them from the main component kind of like stacking on top of each other. 

1. The main component is like a blank large canvas. 
2. One nested component is like dropping another sheet of paper onto the main canvas. But it doesn't have a way *yet* to access the information from the main canvas.
3. The main canvas can pass the nested component information by specifying it within the *Component Tag*. For example if you have just imported your nested component onto the main canvas but it has a variable named `answer` which does not yet have the correct value(declared in the prop): you can specify it in the tag when you declare the nested component:

```MAIN CANVAS COMPONENT
<script>
	import Nested from './Nested.svelte'
</script>

<!--Nested Declaration With Data passed through -->

<Nested answer={42} />
```

**Remember Props are Reactive!**

## Default values

You can set default values for your props very easily! for example:

```svelte
<script>
	export let answer = 'a mystery';
</script>
```

then if you add two components, one being 
specified and the other not then you get the one specified with that value and the other with the default value

```svelte
<Nested answer={42}/>
<Nested />
```

**Note** Each instantiation of the component has it's own state and does not share logic, so these two components have different answers

## Spread props

Props have a really cool mechanism when used with *Javascript objects* which are a lot like *Python dictionaries*

For example lets say we have a javascript object in our **main** component page and we are getting a **Nested** component along with prop information from the nested component

here we specify a Javascript Object named *pkg* on the main page

```Javascript
const pkg = {
	name: 'svelte',
	speed: 'blazing',
	version: 4,
	website: 'https://svelte.dev'
};
```

These values correspond exactly to the prop from the nested component:

```Javascript
	export let name;
	export let version;
	export let speed;
	export let website;
```

We can specify the pkg info and distribute it into the prop like so: 

```svelte
<PackageInfo
	name={pkg.name}
	speed={pkg.speed}
	website={pkg.website}
	version={pkg.version}
/>
```


**Or** A lot more simple and easy method is to specify the prop like so:

```svelte
<PackageInfo {...pkg}/>
```

This automatically fills the values that correspond to the prop without all the excess writing. You just have to make sure that the Javascript object is the same as the Prop information.  


