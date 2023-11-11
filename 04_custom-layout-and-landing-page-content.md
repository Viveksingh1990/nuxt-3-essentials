Custom Layout and Landing Page Content
======================================

Now that we have our URL structure created, we are going to work on querying the API and displaying the data.

Custom Layout
-------------

As mentioned previously, we need to create a main layout that has a simple nav bar with a link to the Home page in it, so that we can easily navigate back to the home page from our currency detail pages. To do this, let’s go through the following steps.

1.  Create the `/layouts` directory at the root of the project
2.  In the `layouts` directory, create a Vue component called `default.vue` This file will contain our layout. Because it is named `default`, it will be used for all pages in the site.
3.  All we really need for this site is a menu, so that’s what we will create. Let’s add the following code to the `<template>` section:

    <template>
      <nav>
        <NuxtLink to="/">Home</NuxtLink>
      </nav>
      <main>
        <slot />
      </main>
    </template>
    

There are two things to notice here.

1.  We are using the built-in `<NuxtLink>` component for creating internal links within our site. Because it is built-in, we don’t have to import it in any of our components, which means less code.
2.  We are using the standard Vue slot syntax for displaying the content from our pages. We want to put the slot wherever we want the content to show up in our layout. In this case, we want it to show up as the main content below the main nav, so we put in within the `<main>`tags.

Once you have saved the changes, you will need to stop and restart the dev server for the changes to take effect.

* * *

Adding Content to Main Landing Page
-----------------------------------

Now that the layout is complete, let’s add the content to the main landing page. As we discussed earlier, we want to provide a listing of the top 10 cryptocurrencies available in the Coinlore API. In order to call the API, we first need to create a server API file that calls Coinlore.

### Create API endpoint

First, off of the project root, create a `/server` directory. Within that directory, create an `/api` directory, and wIthin that directory, we will create a file called `[...].js`

The path to this file should look like this

    /server/api/[...].js
    

Within that file, paste the following line:

    export default defineEventHandler((event) => {
      return $fetch(`https://api.coinlore.net${event.node.req.url}`)
    })
    

The part after the `.net` in the URL will vary, depending on whether we are getting a list, or details for a specific currency, so we make that part dynamic.

According to the Nuxt docs, Nuxt will automatically read in any files in the `~/server/api` directory to create API endpoints, so all we need to do is call that URL from within our app, and Nuxt will make a call to that URL.

* * *

Display content in component
----------------------------

Next, let’s open up the `/pages/index.vue` component we created earlier.

Let’s start with pasting in the setup function.

    <script setup>
        const {data} = await useFetch('/api/tickers?limit=10');
    </script>
    

This call is about as small and simple as you can get. Since `useFetch()` is made globally available in Nuxt, all we have to do it use it - no import statements required.

This line just queries our Coinlore API and gets the first 10 results that come back (there are quite a few available, so we don’t want to get the entire list). It then stores all of the return data in the `data` variable, which we can then access in the `<template>`

Next, let’s paste in our template code.

    <template>
      <main>
        <h1>Index Page</h1>
    
        <table border="1 px solid">
          <thead>
          <tr>
            <th>Name</th>
            <th>Symbol</th>
            <th>Price</th>
            <th>Details</th>
          </tr>
          </thead>
          <tr v-for="currency in data.data" :key="data.data.id">
            <td>{{ currency.name }}</td>
            <td>{{ currency.symbol }}</td>
            <td>{{ currency.price_usd }}</td>
            <td>
              <NuxtLink :to="'/currency/' + currency.id">{{ currency.id }}</NuxtLink>
            </td>
          </tr>
        </table>
      </main>
    </template>
    

This is just a basic HTML table that loops through the returned items and creates the table rows.

If you are not familiar with the `v-for` directive in Vue, it allows you to loop through a list of data, such as an array, and display whatever you want for that piece of data. In our case we are just using it to display a row in a table.

The most important column in the table is the `Details` column. This column will display a link to the details page for that currency. To link to other pages, we use the built-in `<NuxtLink>` component. In this case, we just need to specify the target for the link.

If you remember, back in Lesson 3, we created a `/pages/currency/[id].vue` component, where ID is the [`currency.id`](http://currentcy.id) value returned from the API. So for instance, for Bitcoin, which has an ID of 90, the URL we create is `/currency/90`. We then pass this ID to our `[id].vue` component via the URL, where it is used to query the API and get the coin detail.

* * *

Up Next
-------

In the next lesson, we will fill out our detail page component, and display the data for the specific currency.

### Lesson Resources

##### Source Code:

*   [Starting Code](https://github.com/Code-Pop/Nuxt-3-Essentials/tree/L4-start)
    
    Required: Node LTS
    
*   [Ending Code](https://github.com/Code-Pop/Nuxt-3-Essentials/tree/L4-end)
