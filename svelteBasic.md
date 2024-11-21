# Svelte Basics

## 1. Reactivity || Runes

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

### 1.2 $derived();

> In Svelte, `$derived()` is a function that is used to create a derived variable. It is usually used to update `$state()` variable.

Try this example below in your code to see how it works:

```
<script>
	let count = $state(0)
	let double = $derived(count * 2);
</script>

<button onclick={() => count++}>
	{double}
</button>
```
___

### 1.3 $props();

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

### 1.4 $effects();

Let's start with an example, shall we?
```
<script>
    let count = $state(0);

    $effect(() => {
        console.log(counted);
    })
</script>

<button onclick={() => count++} >{count}</button>
```

> In Svelte, $effects(); is a function that is used to run code when the component is mounted.
>> i.e, when the value of `count` changes,  function inside $effect(); will be executed, which is logging out `counted` to the console.
___

### 1.5 $bindable();

> In Svelte, `$bindable()` makes a variable easy to connect to the UI, like an input box, so it can change automatically. It helps the child component keep track of that variable. `The parent component` still needs to use `bind:value` to link its own value to the child’s. This way, both the parent and child can update each other automatically.


We will make two files: `Parent.svelte` and `Child.svelte` to understand how it works.

```
<!-- Child.svelte -->

<script>
    let { value = $bindable()} = $props();
</script>

<input bind:value={value} />
```

```
<!-- Parent.svelte -->

<script>
    import Child from './Child.svelte';
    let name = $state('Tony');
</script>

<Child bind:value={name} />
<h3>Hello {name}!</h3>
```
___

### 1.6 $inspect();

> In Svelte, `$inspect()` is a function similar to `console.log()`, and it will console.log every time the value of the variable changes.

I will show you two examples to understand how it works:

```
<script>
	let count = $state(0);
	$inspect(count);
</script>

<button onclick={() => count++}>{count}</button>

```

```
<script>
	let count = $state(0);
	let doubled = $state(count * 2)
	$inspect(count, doubled);
</script>

<button onclick={() => count++}>{count}</button>
<button onclick={() => doubled = count * 2}>{doubled}</button>
```

In the second example, both the `count` and `doubled` will be logged out to the console whenever each of them changes.
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
