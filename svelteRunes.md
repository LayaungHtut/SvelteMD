 Runes

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
>> `$bindable()` can only be used inside a $props() declaration


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

### 1.7 $host();


___