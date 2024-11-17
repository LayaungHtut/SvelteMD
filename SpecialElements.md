# Special Elements

In Svelte, special elements are used to create custom components that behave like HTML elements but with added functionality, like dynamic content, interactivity, and reusability. These custom elements let you organize your app, manage state, and render UI efficiently.
___

## 1. svelte:head

The `svelte:head` element is a special element that is unique to Svelte and is not a standard HTML element.

Anything inside <svelte:head> will be injected into the <head> of the HTML document when the component is rendered.

For example, we can use `svelte:head` to add a title to the HTML document:

```
<svelte:head>
    <title>My App</title>
</svelte:head>
```
___

## 2. svelte:body

The `svelte:body` let you listen to the event happening in the browser body and execute certain code you write when the event happens.

For example, we can use `svelte:body` to make element displayed when we put our mouse on the body:

```
<script>
     let show = $state(false);
</script>

<svelte:body 
		onmouseenter={() => show = true}
		onmouseleave={() => show = false}
	/>
{#if show}
<p>This is body</p>
{/if}
```
___

## 3. svelte:window

The `svelte:window` let you listen to the event happening in the browser window and execute certain code you write when the event happens. 

For example, we can use `svelte:window` to listen to the `resize` event and execute a function when the window is resized:

```
<script>
	let windowWidth = window.innerWidth;

	function handleResize() {
		windowWidth = window.innerWidth
	}
</script>

<svelte:window onresize={handleResize} />

<p>windowWidth is {windowWidth}</p>
```

You can add many of the events like scroll, keydown, keyup, etc. You can use binding methods in the `svelte:window` element. 
___

## 4. svelte:document

Just like `svelte:window`, `svelte:document` let you listen to events which are happening in the document(object).


For example, we can use `svelte:document` to listen to the `onkeydown` event and execute a function when the user presses a key:

```
<script>
	let keyPressed = $state('');

	function keyDownHandler(event) {
		keyPressed = event.key
	}
</script>

<svelte:document onkeydown={keyDownHandler} />

<p>You have pressed: {keyPressed}</p>
```
___

## 5. svelte:element

The `svelte:element` let you adjust the HTML element that is rendered when the component is rendered.

For example, we can use `svelte:element` to change the type of header element like `h1`:

```
<script>
		let headerType = $state('h1');
		let header = $state('This is an adjustable header.');
</script>

<svelte:element this={headerType}>
	 {header}
</svelte:element>

<button onclick={() => headerType = 'h2'} >Change to h2</button>
<button onclick={() => headerType = 'h4'} >Change to h4</button>
```

We can adjust not only tags, but also attributes, classes, and styles.

