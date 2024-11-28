# Svelte Basics

## 1. Events

In Svelte, events mean that you can connect a function to a DOM element or attribute.

Try this example below in your code to see how it works:

```
<script>
    function handleClick() {
        console.log('Hello, World!');
    }
</script>

<button onclick={handleClick}>Click me</button>
```

___

## 2. Conditionals

In Svelte, we use syntax below  to create conditionals:

```
{#if condition}
    return{};
{:else if condition}
    return{};
{:else}
    return{};
{/if}
```

Try this example below in your code to see how it works:

```
<script>
    let loggin = $state(true);
    let username = $state('Tony');

</script>

{#if loggin}
    <p>Welcome, {username}!</p>
{:else}
    <p>You haven't logged in yet</p>
{/if}
```
___

## 3. Binding Values

In Svelte, binding values mean that you can connect the value of a variable or property to a DOM element or attribute.

### 3.1 Text Binding

Try this example below in your code to see how it works:

```
<script>
	let name = '';
</script>

<main>
	<input type="text" bind:value={name} />
	<h1>Hello {name}!</h1>
</main>
```
___

### 3.2 Checkbox Binding

Try this example below in your code to see how it works:

```
<script>
    let checked = $state(false);
</script>

<main>
    <input type="checkbox" bind:checked={checked} />
    {#if checked}
        <p>Checked</p>
    {:else}
        <p>Not checked</p>
    {/if}
</main>
    
```
___

## 4. Loops

In Svelte, we use syntax below  to create loops:

```
{#each items as item}
    <li>{item}</li>
{/each}
```

Try this example below in your code to see how it works:

```
<script>
    let animeNames = $state(['Gintama', 'Naruto', 'One piece']);
</script>

{#each animeNames as anime}
    <li>{anime}</li>
{/each}
```

It will display the list of anime names which are stored in the `animeNames` array.
___

## 5. Getters and Setters

In Svelte, we can use getters and setters to access and modify the values of a variable. In order to use this, we will need to convert the variables to private properties which can be declared using the `#` symbol.

Try this temperature converter example below in your code to see how it works:

```
<script lang="ts">
	   class Temperature  {
			   #c = $state(0);
			   #f = $state(0);

			 get c() {
				 return this.#c
			 }

			 set c(c) {
				 this.#c
				 this.#f = c * 1.8 + 32
			 }

			 get f() {
				 return this.#f
			 }

			 set f(f) {
				 this.#f
				 this.#c = (f - 32) / 1.8
			 }
		 }

	const temperature = new Temperature();
</script>

<input type="number" bind:value={temperature.c}/> Celsius = 
<input type="number" bind:value={temperature.f}/> Fahrenheit
```
> We used `class` which is a keyword to create an object