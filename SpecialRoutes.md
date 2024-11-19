# Svelte special route files

As we mentioned before, in Svelte, we can use special route files for our apps, like pages, layouts, errors, and server-side logic. These files make routing and handling data easy, without needing extra libraries or complex setup.

## 1. +page.svelte

The `+page.svelte` file is the most fundamental route file in SvelteKit. It is the main component for a page. It defines what users see when they visit a specific URL. This `+page.svelte` file is just like other svelte, but with `+` in front of it.

***NOTED: You can only have one +page.svelte file in each folder***

We will also show you examples of navigation using the `+page.svelte` file.

In `routes` folder, we will create a new folder named `About` and inside this folder, we will create a new file named `+page.svelte`:
```
<!-- // src/routes/+page.svelte -->

<h1>Welcome to SvelteKit</h1>

<nav>
	<li><a href="/About">About</a></li>
</nav>

```
```
<!-- // src/routes/About/+page.svelte -->

<h1>This is the about page.</h1>
```

If you navigate to the about page, you will see that we head to that about page directly which is inside the `About` folder.

***NOTICED: `href="/About"` is the name of the folder.***

___

## 2. +layout.svelte

The `+layout.svelte` file is a special route file that is used to wrap all the pages in a folder. It is used to add common layout elements to all the pages in a folder. We can add a header, a sidebar, a footer, and other common elements that are used across all the pages in a folder. We can also add styles to the layout file.

We use `<slot></slot>` to add the content of the page,which is mainly `+page.svelte`, to the layout file. 

***NOTED: You can only have one +layout.svelte file in each folder***

We will show you how you can use the `+layout.svelte` file in your project.

First, we will create a new file called `+layout.svelte` in the `routes` folder:

```
<!-- // src/routes/+layout.svelte -->

<slot />
```
This `<slot />` is used to add the content of the page to the layout file. And everything you write in the `+layout.svelte` file will be added to all the pages in the folder.

For example:

```
<!-- // src/routes/+layout.svelte -->

<h1>This is the layout which will be add to all the pages.</h1>

<slot />

<footer> This is the layout footer which will be add to all the pages.</footer>
```

If you navigate to any page, you will see that we have a header and a footer.
___

## 3. +error.svelte

The `+error.svelte` is a special file used in Svelte to ***handle errors*** for a specific route or layout. This file typically contains the error page layout, and you can also add styles and custom logic to control how errors are displayed. Whenever an error occurs in a route or layout, Svelte will display the `+error.svelte` file.

```
<h2>Something went wrong</h2>

<style>
   h2 {
	  color: red;
   }
</style>
```

The page will displayed `Something went wrong` whenever there is an error in the page.

We usually use load functions to handle errors in svelte. We will show you how you can use the `+error.svelte` file in your project.

```
<script context="module">
  export function load({ error, status }) {
    let errorMessage = 'Something went wrong!';

    if (status === 404) {
      errorMessage = 'Page not found!';
    } else if (status === 500) {
      errorMessage = 'Internal server error!';
    }

    return {
      props: {
        status,
        message: errorMessage
      }
    };
  }
</script>

<script>
  export let status: number;
  export let message: string;
</script>

<h1>Error {status}</h1>
<p>{message}</p>

<style>
  h1 {
    color: red;
  }
  p {
    font-size: 1.2rem;
  }
</style>
```


