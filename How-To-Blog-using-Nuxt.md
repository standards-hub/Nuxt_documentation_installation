# How to create a Blog using Nuxt

Purpose of this document is to provide hands on instructions to create a Blog using [Nuxt](https://nuxtjs.org/) and deploy if on [GitHub pages](https://pages.github.com/) using [GitHub Actions](https://github.com/features/actions).

## Installation

First we create *Blog* project by installing Nuxt.

```bash
# using npm package manager
npm init nuxt-app <blog-project-name>

# using npx
npx create-nuxt-app <blog-project-name>

# using yarn
yarn create nuxt-app <blog-project-name>
```

### Exmaple

In this document we well create `My-Blog` using npm.

```bash
npm init nuxt-app my-blog
```

Once the `nuxt-app` project template is downloaded to your local machi`ne a set of questions will guide you through granurally configuring the `my-blog` project.

```bash
create-nuxt-app v3.7.1
✨  Generating Nuxt.js project in my-blog
? Project name: (my-blog)
# just type ENTER or change the name of your project as you see fit

? Programming language: (Use arrow keys)
❯ JavaScript
  TypeScript
# Move the selection to desired language and press ENTER
# we will use JavaScript in this example

? Package manager: (Use arrow keys)
❯ Yarn
  Npm
# we will use the npm in this example

? UI framework: (Use arrow keys)
❯ None
  Ant Design Vue
  BalmUI
  Bootstrap Vue
  Buefy
  Chakra UI
  Element
  Framevuerk
  Oruga
  Tachyons
  Tailwind CSS
  Windi CSS
  Vant
  View UI
  Vuetify.js
# This is a selection of CSS framework question
# Choose one that is most suitable for your Blog design, recommended by your designer
# we will use Tailwind CSS

? Nuxt.js modules: (Press <space> to select, <a> to toggle all, <i> to invert selection)
❯◯ Axios - Promise based HTTP client
 ◯ Progressive Web App (PWA)
 ◯ Content - Git-based headless CMS
# These modules add additional capabilities to your Blog
# we need Content and we will use Axios to get additional external content

? Linting tools: (Press <space> to select, <a> to toggle all, <i> to invert selection)
❯◯ ESLint
 ◯ Prettier
 ◯ Lint staged files
 ◯ StyleLint
 ◯ Commitlint
 # Linting enable compliance to formatting and style of your application
 # It's recommended as a way to keep productive collaboration
 # We will select all 

 ? Testing framework: (Use arrow keys)
❯ None
  Jest
  AVA
  WebdriverIO
  Nightwatch
# Testing your code is a must in order to have some confidence in code quality
# Since we are only have an example of a Blog we will not include it this time

? Rendering mode: (Use arrow keys)
❯ Universal (SSR / SSG)
  Single Page App
# At this stage we will use Universal rendering mode

? Deployment target: (Use arrow keys)
❯ Server (Node.js hosting)
  Static (Static/Jamstack hosting)
# Since our plan is to deploy as static web site on GitHub pages we select Static

? Development tools: (Press <space> to select, <a> to toggle all, <i> to invert selection)
❯◯ jsconfig.json (Recommended for VS Code if you are not using typescript)
 ◯ Semantic Pull Requests
 ◯ Dependabot (For auto-updating dependencies, GitHub only)
# We are using Visual Studio Code (VC) so the first option is good for us

? Continuous integration: (Use arrow keys)
❯ None
  GitHub Actions (GitHub only)
  Travis CI
  CircleCI
# We are deploying using GitHub Actions, ergo ...

? What is your GitHub username? (your github user name)
# press ENTER or add your GitHub user name

? Version control system: (Use arrow keys)
❯ Git
  None
# We are using git so just press ENTER

# after this last question the installation of needed dependencies wil start
# this will take some time
Installing packages with npm

# Once installation is finished you will see the report like this
🎉  Successfully created project my-blog

  To get started:

	cd my-blog
	npm run dev

  To build & start for production:

	cd my-blog
	npm run build
	npm run start
```

Congratulations, you created your *Blog* project. Now it's time to populate the content. Make your project folder, `my-blog` to current working one and let's move on with the *Blog* content.

```bash
cd my-project
```

## Create Blog Content

### Initial cleaning up

Before we start with the newly created *Blog* content we need to clean up the one provided by the used project template.
Creating the project from the template speed up the creating process but the content put do demonstrate how nuxt works is not needed.

The files that needs to be deleted are:
```bash
content/hello.md
components/NuxtLogo.vue
components/Tutorial.vue
```

Replace the `static/favicon.ico` file with your *Blog* one.

Open the `pages/index.vue` file in your editor and change its content with:

```js
<template>
  <h1>Welcome to My Blog</h1>
</template>

<script>
export default {}
</script>
```

Now you are ready to start your *Blog* for the first time by running following command:

```bash
npm run dev
```

You can save this revision as `initial commit` of your `my-blog`. Bare in mind that we are using the linting of git commits comments as well.
The format of git comments are based on [The Conventional Commits specification](https://www.conventionalcommits.org/en/v1.0.0/).
It's a good practice to format your git commit messages follow easy set of rules for creating an informative and explicit commit history.

### Create *Blog* markdown page

The [@nuxt/content](https://content.nuxtjs.org/) module works by reading the files in `content/` directory. The `@nuxt/content` module can parse markdown, csv, yaml, json, json5 or xml files.

The `@nuxt/content` module gives access to injected variables that can be accessed and shown in page template. The default variables that are injected into document are:

* `body`: body text
* `dir`: directory
* `extension`: file extension (.md in this example)
* `path`: the file path
* `slug:` the file slug
* `toc`: an array containing our table of contents
* `createdAt`: the file creation date
* `updatedAt`: the date of the last file update

The custom injected variables can be added by putting a block of YAML front matter to markdown file. It must be at the top the file and must be a valid YAML format set between three triple dashed lines. For example:

```yaml
---
title: My first  Post
description: Learning how to create a blog
author: Known Well
img: first-post.jpg
alt: my first blog post
---
```


Create an `articles/` folder where the *Blog* articles will be stored.

```bash
mkdir content/articles
```

Now create the first article in a markdown file `content/articles/first-post.md`. Put some initial conntent in it.


```md
---
title: First  Post
description: Learning how to create a blog
author: Known Well
img: first-post.jpg
alt: my first blog post
---
# First Post

This is an example of content of the First post in **My Blog**.
```

To display content in our *Bog* page, we can use nuxt [dynamic pages](https://nuxtjs.org/docs/directory-structure/pages/#dynamic-pages) capability. Create a page named `_slug.vue` inside `pages/blog` folder. This will enable using the `params.slug` variable provided by vue router to get the name of each article.

Inside put the following content:

```js
<template>
  <article>
    <h1>{{ article.title }}</h1>
    <h2>by {{ article.author }}</h2>
    <p>{{ article.description }}</p>
    <img :src="article.img" :alt="article.alt" />
    <p>Article last updated: {{ article.updatedAt }}</p>

    <nuxt-content :document="article" />
  </article>
</template>

<script>
  export default {
    async asyncData({ $content, params }) {
      const article = await $content('articles', params.slug).fetch()

      return { article }
    }
  }
</script>
```

The *index* page will list out our blog posts. Open `pages/index.vue` page and add following content:

```js
<template>
  <div>
    <h1>Blog Posts</h1>
    <ul>
      <li v-for="article of articles" :key="article.slug">
        <NuxtLink :to="{ name: 'blog-slug', params: { slug: article.slug } }">
          <img :src="article.img" />
          <div>
            <h2>{{ article.title }}</h2>
            <p>by {{ article.author.name }}</p>
            <p>{{ article.description }}</p>
          </div>
        </NuxtLink>
      </li>
    </ul>
  </div>
</template>

<script>
  export default {
    async asyncData({ $content, params }) {
      const articles = await $content('articles')
        .only(['title', 'description', 'img', 'slug', 'author'])
        .sortBy('createdAt', 'asc')
        .fetch()

      return {
        articles
      }
    }
  }
</script>
```

Run your *Blog* application and navigate from *index* page to blog article.

## Style your *Blog*

Everything written inside *Blog* markdown content is wrapped inside a `div` with a **class** of `nuxt-content`. This enable easy styling to all elements coming from the markdown file by wrapping them in the `nuxt-content` class.

```html
<style>
  .nuxt-content h1 {
    font-weight: bold;
    font-size: 28px;
  }
  .nuxt-content h2 {
    font-weight: bold;
    font-size: 22px;
  }
  .nuxt-content p {
    margin-bottom: 18px;
  }
</style>
```

All other tags can be styled as normal either using [TailwindCSS](https://tailwindcss.com/), the CSS framework selected during the installation of the project, or adding CSS in the style tag.

The [@tailwindcss/typography](https://github.com/tailwindlabs/tailwindcss-typography) provides a set of `prose` classes that can be used to add beautiful typographic defaults to any vanilla HTML like HTML rendered from Markdown, or pulled from a CMS.

### Layouts

Layouts are used to change the look and feel of Nuxt app. For example to include a sidebar or to provide distinct layouts for mobile and desktop.

The main layout can be altered by adding a `layouts/default.vue` file. The `default.vue` layout will be used for all pages that don't have a layout specified. The minimal `default` layout is shown in the following example:

```js
<template>
  <Nuxt />
</template>
```

The layout template can be enriched with additional HTML content or Vue components, for example:

```js
<template>
  <div class="container mx-auto p-4">
    <AppHeader />
    <Nuxt />
    <AppFooter />
  </div>
</template>
```

Every file in layouts directory will represent a custom layout that is accessible using the `layout` property in the page components.
For example if the `layouts\authors.vue` represent the page layout for presenting the authors then it can be used in `pages/authors.vue` in the following fashion:

```js
<script>
export default {
  layout: 'authors',
  // OR
  layout (context) {
    return 'authors'
  }
}
</script>
```

## Custom Components

Components are what makes up the different parts of the page. They can be reused and imported into pages, layouts and even other components.
Nuxt can auto-import the components you use. To activate this feature put following in `nuxt.config.js` configuration, if it's not already activated:

```js
export default {
  components: true
}
```

### Create custom component

To create the custom component, for example to show information about the blog post author, create `components/Author.vue` file and put the following content in it:

```js
<template>
  <div>
    <img :src="author.image" />
    <div>
      <h4>Author</h4>
      <p>{{ author.name }}</p>
      <p>{{ author.bio }}</p>
    </div>
  </div>
</template>
<script>
  export default {
    props: {
      author: {
        type: Object,
        required: true
      }
    }
  }
</script>
```

### Using custom components

Created component can be used in other pages to show information about the author of the blog post, for example:

```js
<template>
  <article>
    <h1>{{ post.title }}</h1>
    <p>{{ post.description }}</p>

    <nuxt-content :document="post" />

    <author :author="post.author" />
  </article>
</template>
```

More on how Nuxt handle custom components can be find [here](https://nuxtjs.org/docs/directory-structure/components). 

## Assets

The `assets` directory contains un-compiled assets such as Stylus or Sass files, images, or fonts. The special care should be taken when referencing different type of assets in pages, CSS files or as part of the blog building process.

More details can be find at [assets directory](https://nuxtjs.org/docs/directory-structure/assets) page.

The `static` directory is directly mapped to the server root and contains files that won't be changed. All files in this folder will be automatically served by Nuxt through project root URL. Be sure to check [static](https://nuxtjs.org/docs/directory-structure/static) folder documentation to know how to use and configure it if desired.

## Meta tags, SEO and social links

SEO is basically how Google and other search engines can index your content and present it to people searching for certain keywords or phrases. Search engines and social media platforms look for this information by parsing the `<head>` tag of any given website. The following example set the page title to be equivalent to the title of the post. It’ll also use the post title to set proper meta tags for Open Graph (Facebook) and Twitter.

```js
head() {
    return {
      title: this.post.title,
      meta: [
        // Open Graph
        { hid: 'og:title', property: 'og:title', content: this.post.title },
        { hid: 'og:type', property: 'og:type', content: 'article' },
        {
          hid: 'og:image',
          property: 'og:image',
          content: `https://my-blog.com/${this.post.image}`,
        },
        // Twitter Card
        {
          hid: 'twitter:title',
          name: 'twitter:title',
          content: this.post.title,
        },
        {
          hid: 'twitter:card',
          name: 'twitter:card',
          content: 'summary_large_image',
        },
        {
          hid: 'twitter:image',
          name: 'twitter:image',
          content: `https://my-blog.com/${this.post.image}`,
        }
      ]
    }
}
```

In this way Google will have an easier time parsing blog content and have good looking preview cards when sharing links to blog posts on social media.

## Deploy

Since this is a Nuxt project it should follow the deployment recommendations from the official Nuxt documentation. There are multiple [deployment targets](https://nuxtjs.org/deployments) explain there but the one for the GitHub pages will be the one we will be using in this document.

To deploy via [GitHub Actions](https://github.com/features/actions), create or adjust the workflow which pushes the generated files from the `dist` folder to your default GitHub Pages branch `gh-pages`.

With an existing workflow, add the following step:

```markdown
- name: Deploy
  uses: peaceiris/actions-gh-pages@v3
  with:
    github_token: ${{ secrets.GITHUB_TOKEN }}
    publish_dir: ./dist
```

For a new workflow, paste the following content into a new file called cd.yml in .github/workflows directory:

```markdown
name: cd

on: [push, pull_request]

jobs:
  cd:
    runs-on: ${{ matrix.os }}

    strategy:
      matrix:
        os: [ubuntu-latest]
        node: [14]

    steps:
      - name: Checkout
        uses: actions/checkout@master

      - name: Setup node env
        uses: actions/setup-node@v2.1.2
        with:
          node-version: ${{ matrix.node }}

      - name: Install dependencies
        run: yarn

      - name: Generate
        run: yarn generate

      - name: Deploy
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./dist
```

Then commit this changes to your repository. Once complete, you'll see your gh-pages branch updated as well as your site.