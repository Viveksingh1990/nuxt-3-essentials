Installation and Configuration
==============================

Now that we know what Nuxt is, let’s start actually using it. To begin, we need to install it.

Installing
----------

1.  We will be following the installation instructions in the Nuxt 3 Quick Start guide at at [v3.nuxtjs.org](https://v3.nuxtjs.org/getting-started/installation).
2.  Open terminal app of choice - default terminal app, or something like iTerm2
3.  Type `npx nuxi init nuxt3-app` - this will install the app in the `nuxt3-app` directory under the current directory
4.  In terminal, change into `nuxt3-app` directory - `cd nuxt3-app`
5.  Open VS Code by typing `code {project name}` This assumes you have the `code` command installed. If not, you can just do `File → Open`from the VS Code menu, and open the project directory.
6.  In the VS Code terminal , type `yarn install`. This will install all of the dependencies required by the project in the `node_modules` folder.
7.  Start dev server - type `yarn dev -- -o` One thing to notice is how quickly the site builds. By default Nuxt 3 uses Vite, which is a new build tool that replaces Webpack. which was used in previous versions of Nuxt.
8.  The default Nuxt screen is displayed in default browser. This is the default `<NuxtWelcome>` component. Let’s comment that out and replace it with our own text to show that this is the main page (comment out `<NuxtWelcome>`component and replace it with something like `<h1>Welcome to my Nuxt3 App!</h1>`)

Directories
-----------

As shown in the [docs](https://v3.nuxtjs.org/docs/usage/data-fetching), there are a number of available directories at the top level of the directory structure. However, most of them are optional, and you only need to create them if you need them.

The `node_modules` folder is always there, and contains all of the dependencies required by Nuxt and any other libraries you have downloaded via `npm` or `yarn`

One of the powerful features of Nuxt is custom layouts. Using the `/layouts` folder, we can create custom layouts for various part of the site, and then assign a component to use the layout with the `layout` keyword. For instance, you could have a layout for your main page, a layout for a blog post, and layout for an About page, etc.

The `/pages` directory is where we create our URL structure for our app. Using directories and file names, we create the URLs used to navigate the app. This makes it much easier to structure your app than having to create manual configuration using json, as you would in a normal Vue app. We will be creating our files in the `/pages` directory for the remainder of this course.

In our next lesson, we will start building our app out, and we will begin by creating our URL structure using directories and components under the /pages directory.

### Lesson Resources

##### Source Code:

*   [Nuxt 3 Quick Start](https://v3.nuxtjs.org/getting-started/installation)
    
    Required: Node LTS
    
*   [Starting Code](https://github.com/Code-Pop/Nuxt-3-Essentials/tree/L2-start)
    
*   [Ending Code](https://github.com/Code-Pop/Nuxt-3-Essentials/tree/L2-end)
