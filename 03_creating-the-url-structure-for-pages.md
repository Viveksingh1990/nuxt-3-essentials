Creating the URL Structure For Pages
====================================

As we talked about previously, one of the features of Nuxt that makes it so easy to use is that you can use the directory structure of the `/pages` directory and its subdirectories to generate the URL structure for the site. For instance, if I wanted to create a simple `About` page, at [mysite.com/about](http://mysite.com/about), I would just create a file called `about.vue` in the `/pages` directory.

For our project, we are going to create a basic site that displays data on different cryptocurrencies (e.g. Bitcoin, Ethereum, etc). We will be using a site called Coinlore to get our data. Coinlore has a data api. and we will query that api to get data for the various cryptocurrencies.

The site will have two basic pages.

1.  The main landing page, which will display a listing of the currencies for which Coinlore has data.
2.  A detail page for each currency.

Each item on the main page will contain a link to the detail page for that currency. This page will use what is called dynamic routing. This allows us to use one Vue component to display data for many items, using parameters passed into the component via the URL.

* * *

Overriding app.vue
------------------

As we saw earlier, by default, `app.vue` is the main landing page for the site. However, we want to use the routing provided by the `/pages` directory, so we need to override that behavior. To do that, we need to do three things:

1.  Create the `/pages` directory at the root of the project.
2.  Create an `index.vue` component in the `/pages` directory.
3.  Override the content in `app.vue` using the built-in `<NuxtLayout>` and `<NuxtPage>` components.

    <NuxtLayout>
    <NuxtPage/>
    </NuxtLayout>
    

Using the built in `<NuxtPage>` component tells Nuxt to use the content in the `/pages` directory.

* * *

Displaying Details
------------------

Next, we need to create our dynamic page for displaying the details for a cryptocurrency. The URL we want to create is

> [mysite.com/currency/{id}](http://mysite.com/currency/%7Bid%7D)

where `{id}` is the dynamic value passed in to the component that tells us which id to query in the Coinlore API.

So to define the structure, we need to do two things:

1.  Create a `/currency` folder under `/pages`, so the end result is `/pages/currency`
2.  In the `/currency` directory create a Vue component named `[id].vue` (with the brackets)

With this done, we have everything in place to create our URL structure. In the next few lessons, we will fill in the content of these components to display the Coinlore data.

### Lesson Resources

##### Source Code:

*   [Starting Code](https://github.com/Code-Pop/Nuxt-3-Essentials/tree/L3-start)
    
    Required: Node LTS
    
*   [Ending Code](https://github.com/Code-Pop/Nuxt-3-Essentials/tree/L3-end)
