Deployment
==========

Deploying to Netlify
--------------------

Now that the site has been created and is working, we are going to deploy the site to make it publicly available. There are multiple options for deploying a Nuxt site, but for this course, we are going to use a popular host called Netlify.

When deploying to Netlify, there are two options:

1.  Pushing to a repository, and connecting to that repository from Netlify
2.  Dragging and dropping your site output folder to Netlify.

For this example, we will deploy from a Github repository.

First, you will need to create a repository. Create a new repository on Github, and then, per instructions provided there, complete the following steps in your project directory in a terminal window:

1.  `git init`
2.  `git add .`
3.  `git commit -m "first commit"`
4.  `git remote add origin [git@github.com](mailto:git@github.com):{myGitHubUserName/{my-repo}.git` (substitute in your user and repo name)
5.  `git push -u origin master`

Next, you can sign into Netlify using your GitHub account, and select `Import an existing project`. There are three steps to complete.

Under Step 1 `Connect to Git provider`, click on the `Github` button.

In the permissions window that pops up, click the `Authorize Netlify` button.

Under `Step 2 Pick a repository`, select your new repo.

Under `Step 3 - Site Settings and deploy!`, accept the default values (Netlify automatically detects that it is a Nuxt site)

During the build, you are redirected back to the `Site overview` tab. Netlify generates a new URL and displays it at the top left. Click on it and voila! - your site is displayed!!

As we discussed in the first lesson, Nuxt supports SSR and SSG modes. As of the writing of this lesson, Netlify and Nuxt 3 only support SSR (server side rendering) but SSG capabilities will be added in the near future.

We’ve reached the end of our course, and have learned the basics of getting up and running with Nuxt 3. With what we have covered here, you can create many types of websites, such as blogs, brochure sites, or even just personal sites.

Thank you for watching, and have fun building with Nuxt 3.

