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
> Note: `<project-name>` is the name of the repository already created in GitHub.

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
? GitHub repository (owner/name): (jpradocueva/md2html_guidelines)
? Twitter username (@username): (@jpradocueva)
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

## Link Local with Upstream Repository

> At this moment you have created a local repository, e.g. `md2html_guidelines` and you want to sync this content with the upstream repository, `https://github.com/jpradocueva/md2html_guidelines.git`, which was created in a separate step.

Add the remote repository in GitHub as a remote `upstream`

`git remote add upstream https://github.com/jpradocueva/md2html_guidelines.git`

Then, push the content from the local repository to upstream with: (assuming the branch is called `master`

`git push --set-upstream master master`

Then, confirm that the setup is correct by running:

`git remote show upstream`

The print out of this command should indicate that the local repository is connected to the upstream.

## Customizing project configuration

The project customizations are achieved by adjusting `nuxt.config.js`, `tailwind.config.js` and `content/settings.json` file.

### nuxt.config.js

This configuration file is general Nuxt configuration file. The setup the project `nuxt.config.js` allows you to add or to override the default *theme* config.

An example of how `nuxt.config.js` is structured and adjustment can be find at https://content.nuxtjs.org/themes/docs#nuxtconfigjs

### tailwind.config.js

This project is using the [tailwind](https://tailwindcss.com/) CSS framework for styling.

You can change the default *theme* styling by creating your own `tailwind.config.js` in the root of the project.
The whole *theme* styling is generated around **primary** color in order to be easily adjustable. Take look at [default](https://github.com/nuxt/content/blob/dev/packages/theme-docs/src/tailwind.config.js) styling if you want to learn how to change fonts, typography or other aspects of web page styling.

### content/settings.json

Use the [settings](https://content.nuxtjs.org/themes/docs#settings) file in `content` folder to adjust the logo image, twitter account or default layout of the documentation among the other *theme* parameters.

## Creating content

Writing the content is the main activity. There are several basic aspects of [writing documentation in Markdown](https://content.nuxtjs.org/writing/#markdown) format.

In addition the nuxt content documentation project provides additional capabilities for more elaborate presentation elements. The *theme* provides some general Vue.js [components](https://content.nuxtjs.org/themes/docs#components) that you can use directly in your markdown content.

Content should be organized in files based on supported [locals](https://content.nuxtjs.org/themes/docs#locales) and desired [routing](https://content.nuxtjs.org/themes/docs#routing). The *theme* default local is `en` so the documents for this local are located in `./content/en/` folder.

Every document must provide set of parameters in  document [front-matter](https://content.nuxtjs.org/themes/docs#front-matter) in order for a *theme* to work properly. The **required** ones are:

* title - The title of the page will be injected in meta tags of the HTML page
* description - The description of the page will be injected in meta tags of the HTML page
* *position* - Number used in sorting the documents in the navigation

List of optional fields are defined [here](https://content.nuxtjs.org/themes/docs#front-matter).

## Deploy

Since this is a Nuxt project it should follow the deployment recommendations from the official Nuxt documentation. There are multiple [deployment targets](https://nuxtjs.org/deployments) explain there but the one for the GitHub pages will be the one we will be using in this document.

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
