# Svelte Transition;

In this section, we will learn about transition in svelte.

In Svelte, we can use the external transition library called `svelte/transition` to add transition to our svelte components.

We can import the transition library in the script like this:

```
import { fade } from 'svelte/transition';
import { blur } from 'svelte/transition';
import { fly } from 'svelte/transition';
import { slide } from 'svelte/transition';
import { crossfade } from 'svelte/transition';
import { scale } from 'svelte/transition';
import { draw } from 'svelte/transition';
```
***One Thing to note is that, we can use the duration in each transtion***

## 1. { fade } transition

> As the name suggests, the `fade` transition is used to fade in or fade out an element.

Try this example below in your code to see how it works:

```
<script>
    import { fade } from 'svelte/transition';
    let show = $state(true);
</script>

<button onclick={() => show = !show}>Show</button>

{#if show}
    <div transition:fade>
        Fading transition
    </div>
{/if}
```

## 2. { blur } transition

> Blur is just like fade, but it blurs out the element instead of fading it out.

Try this example below in your code to see how it works:

```
<script>
    import { blur } from 'svelte/transition';
    let show = $state(true);
</script>

<button onclick={() => show = !show}>Show</button>

{#if show}
    <div transition:blur>
        Bluring transition
    </div>
{/if}
```

## 3. { fly } transition

> Fly is used to fly out an element from one position to another. But unlike fade and blur, we will need to specify the direction the fly: which is `x or y`; to make it work properly.

Try this example below in your code to see how it works:

```
<script>
    import { fly } from 'svelte/transition';
    let show = $state(true);
</script>

<button onclick={() => show = !show}>Show</button>

{#if show}
    <div transition:fly={{ x: 200, duration: 2000}}>
        Flying transition
    </div>
{/if}
```

## 4. { slide } transition

> In this `slide` transition, it would be better if we use another content to display the transition.

Try this example below in your code to see how it works:

```
<script>
	import { slide } from 'svelte/transition';
	let show = true;
  </script>
  
  <button onclick={() => (show = !show)}>Show contents</button>

  {#if show}
	<div class="content" transition:slide>
		contents
	</div>
  {/if}

  <style>
	.content {
		display: flex;
		justify-content: center;
		align-items: center;
		background-color: #ff3e00;
		width: 100px;
		height: 100px;
	}
  </style>
```

## 5. { crossfade } transition

## 6. { scale } transition

> In this scale transition, it scales in and out the element.

Try this example below in your code to see how it works:

```
<script>
	import { scale } from 'svelte/transition';
	let show = true;
  </script>
  
  <button onclick={() => (show = !show)}>Show contents</button>

  {#if show}
	<div class="content" transition:scale>
		contents
	</div>
  {/if}

  <style>
	.content {
		display: flex;
		justify-content: center;
		align-items: center;
		background-color: #ff3e00;
		width: 100px;
		height: 100px;
	}
  </style>
```

## 7. { draw } transition



