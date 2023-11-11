Creating the Detail Page
========================

Displaying the Coin Detail Page
-------------------------------

Now that we have displayed our initial listing, and each item in the list contains a link to the detail page, let’s fill in that detail page.

If you remember from the previous lesson, we created a server API route that looks like this

📁**server/api/\[…\].js**

    export default defineEventHandler((event) => {
      return $fetch(`https://api.coinlore.net${event.node.req.url}`)
    })
    

What we need is the part to pass as `${req.url}`.

According to Coinlore, to get a specific coin, the full URL is:

    https://api.coinlore.net/api/ticker/?id={id}
    

So if we wanted to get data for Bitcoin, which has an ID of 90 in Coinlore, our desired URL would be:

    https://api.coinlore.net/api/ticker/?id=90
    

With this in mind, let’s fill in the content of the page. Let’s open the **\[id\].vue** file we created in Lesson 4 and create our setup function that calls the API.

    <script setup>
    	const route = useRoute();                                       
      const { data: coin } = await useFetch('/api/ticker?id=' + route.params.id);
    </script>
    

You will notice that this looks very much like the setup function for the main page, with a couple changes and additions.

First, since we are reading the ID of the coin whose data we want to get from the URL, we need to get that value, and we do it with the `useRoute()` function. This gives us the route definition. Within that route definition, the `params` object contains the `id` value from the URL.

Next we add this value to the URL as `route.params.id`, and call the endpoint using `useFetch()` like we did in the main page, and return that data as the `coin` object from the function.

Next, we need to create our template to display this data.

    <template>
      <div>
        <h2>{{ coin.name }} Detail page</h2>
        <table border="1 px solid">
          <thead>
            <th>Symbol</th>
            <th>Rank</th>
            <th>Price - US $</th>
            <th>Market Cap - US $</th>
          </thead>
          <tr>
            <td>{{ coin.symbol }}</td>
            <td>{{ coin.rank }}</td>
            <td>{{ coin.price_usd }}</td>
            <td>{{ coin.market_cap_usd }}</td>
          </tr>
        </table>
      </div>
    </template>
    

In this case, since we are just displaying data for one coin, we do not need to use a `v-for` loop; instead we just create an HTML table with the data we want to display. In this case, we are just displaying the Name at the top, and then the symbol, rank, price (in US dollars), and market cap values.

Because we returned the `coin`object from the setup function, we need to get the data from the `coin` variable.

And voila!, we are done with our simple app. Next, we will cover how to deploy the app to share it with the rest of the world.

### Lesson Resources

##### Source Code:

*   [Starting Code](https://github.com/Code-Pop/Nuxt-3-Essentials/tree/L5-start)
    
    Required: Node LTS
    
*   [Ending Code](https://github.com/Code-Pop/Nuxt-3-Essentials/tree/L5-end)
