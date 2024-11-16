# Svelte Basics

## 1. Reactivity

In Svelte, reactivity means to re-run the code whenever any of the referenced values change.

### 1.1 $state();

> In Svelte, $state(); is a function that is used to create a reactive variable.
>
> > $state(); can be used with any of the numbers, strings, booleans, arrays, and objects.

Try this example using $state(number); below in your code to see how it works:

```
<script>
    let count = $state(0);
</script>

<button onclick={() => count++}>{count}</button>
```
___

### 1.2 $props();

> In Svelte, we use $props(); as a way to pass the data from the parent component to the child component.

Try this example using $props(); below in your code to see how it works:

We will use two components: `Parent.svelte` and `Child.svelte` to understand how it works.

```
<!-- Child.svelte -->

<script>
    let name = $props();
</script>

<h1>Hello {name}!</h1>
```

```
<!-- Parent.svelte -->

<script>
    import Child from './Child.svelte';
</script>

<Child name={'Tony'} />
```

> This mean we can reuse the Child component as many time as we want with different data.
___

## 2. Events

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

## 3. Conditionals

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

## 4. Binding Values

In Svelte, binding values mean that you can connect the value of a variable or property to a DOM element or attribute.

### 4.1 Text Binding

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

### 4.2 Checkbox Binding

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

## 5. Loops

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
