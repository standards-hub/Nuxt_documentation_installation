# How To Nuxt Docs

Purpose of this document is to provide hands on information on creating and deploying the documentation type web side using the [nuxt-content-docs](https://www.npmjs.com/package/@nuxt/content-theme-docs) template package and [GitHub pages](https://pages.github.com/) capabilities.

The goal is to provide more detail information in order to deliver the promise of the `nuxt-content-docs`:
> Create your documentation with @nuxt/content docs theme in seconds!

## Creating the project

To create a project you can utilise `yarn` or `npm` package manager.

```bash
# Yarn
yarn create nuxt-content-docs <project-name>

# NPX
npx create-nuxt-content-docs <project-name>
```

### Example 

For creating `my-project-docs` use the command:

```bash
npx create-nuxt-content-docs my-project-docs
```
Once the initial project template is downloaded a set of questions to configure the project will be presented. The default answers can be taken if you do not have the prepared the specific ones in advance.
The most important it the selection of the package manager as you must have it installed on your system.
If you have already installed `node` then `npm` is already available. [Yarn](https://yarnpkg.com/) needs to be installed separately.

```bash
✨  Generating @nuxt/content documentation in my-project-docs
? Project name: (my-project-docs)
? Project title: (Nuxt Content)
? Documentation url:
? GitHub repository (owner/name): (nuxt/content)
? Twitter username (@username): (@nuxt_js)
? Package manager: (Use arrow keys)
❯ Yarn
  Npm
```
After selecting the package manager, `npm` in this example, the installation of dependencies will start.

```bash
  Installing packages with npm
```
Once the installation process is done you should change to the newly created folder.

```bash
cd my-project-docs/
```

In order to verify that everything is working as expected run the following command:

```bash
npm run dev
```

The above command will build `development` version of this project and run web server making this web documentation available on your local machine at `http://localhost:3000/` address. Navigate your web browser to this URL and you should see the `nuxt/content` initial documentation page with the information:

> Your documentation has been created successfully!


## Deploy

Since this is a Nuxt project it should follow the deployment recommendations from the official Nuxt documentation. THere are multiple [deployment targets](https://nuxtjs.org/deployments) explain there but the one for the GitHub pages will be the one we will be using in this document.

To deploy via GitHub Actions, create or adjust the workflow which pushes the generated files from the `dist` folder to your default GitHub Pages branch `gh-pages`.

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
