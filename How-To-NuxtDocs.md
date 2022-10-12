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
? GitHub repository (owner/name): (jpradocueva/github/documents/jpc/md2html_guidelines)
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
Initialize the repository as a Git repo.

``` bash
git init
```

Then, commit to the GitHub repository all the files creating during the setup:

`$ git add .`

then,

`$ git commit -m 'files created during the setup'`

then,

`$ git push`

The system responds with:

> fatal: No configured push destination.
> Either specify the URL from the command-line or configure a remote repository using

then run the command, e.g.,

`$ git remote add <name> <url>`

and then push using the remote name

`git remote add origin https://github.com/OpenMobileAlliance/oma_working_groups.git`

The system will provide an error.

>fatal: The current branch main has no upstream branch.>
>To push the current branch and set the remote as upstream, use

Then run the command:

`$ git push --force`

This should resolve the issue.

---

` $ git push --set-upstream upstream main`
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

Then, commit all the changes to your local host:

`git add .` and then

`git commit -m "first commit"`

Then, push the content from the local repository to upstream with: (assuming the branch is called `master`

`git push --set-upstream upstream master`

Then, confirm that the setup is correct by running:

`git remote show upstream`

The print out of this command should indicate that the local repository is connected to the upstream.

## Customizing project configuration

The project customizations are achieved by adjusting the following files:

* `static` folder,
  * `content/settings.json`, (if needed),
* `nuxt.config.js`, 
* `tailwind.config.js`, and 
* `package.json`

> Note: each time that `nuxt.config.js` file is modified, you may need to force a reset in the GitHub pages Settings by switching off and on the content in the `Source` section. See below.

### `static` folder
Go to `static` folder and replace the following files (logos) with the ones for the project:
* icon.png
* logo-dark.svg
* logo-light.svg

Also delete the file images:
* preview-dark.png, and
* preview.png

#### `content/settings.json`
If any of the logo names doesn't much the above names, then go to the folder `/content` and update the names accordingly in the file `settings.json`.

See an example of a well formed `settings.json` file, https://github.com/OpenMobileAlliance/dmse-documentation/blob/master/content/settings.json.
In this file you can configure links to: github, twitter, youtube, linkedin, algolia (search), etc.

### `nuxt.config.js`

This configuration file is general Nuxt configuration file. The setup the project `nuxt.config.js` allows you to add or to override the default *theme* config.

An example of how `nuxt.config.js` is structured and adjustment can be find at https://github.com/OpenMobileAlliance/dmse-documentation/blob/master/nuxt.config.js

### `tailwind.config.js`

This project is using the [tailwind](https://tailwindcss.com/) CSS framework for styling.

You can change the default *theme* styling by creating your own `tailwind.config.js` in the root of the project.
The whole *theme* styling is generated around **primary** color in order to be easily adjustable. Take look at [default](https://github.com/nuxt/content/blob/dev/packages/theme-docs/src/tailwind.config.js) styling if you want to learn how to change fonts, typography or other aspects of web page styling.

### `package.json`

* `name` property needs to be udpated to the name of the repository
* `deploy` set it to the correct URL
* `node` is set to version 14.15.1,
* `npm` is set to version 6.14.11

There is a large number of dependencies and devDependencies, it is better to copy the file below and change the above properties.

An example of a well configure `package.json` file can be seen in https://github.com/OpenMobileAlliance/dmse-documentation/blob/master/package-lock.json.

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

With an existing workflow, add the following step to `cd.yml` file on the folder `.github/workflows/cd.yml`. 

```markdown
- name: Deploy
  uses: peaceiris/actions-gh-pages@v3
  with:
    github_token: ${{ secrets.GITHUB_TOKEN }}
    publish_dir: ./dist
```

> Note: if this file `cd.yml` doesn't exist, then add folder and file, `.github/workflows/cd.yml`. 

For a new workflow, paste the following content into a new file called cd.yml in .github/workflows directory:

> Note: Also, in the GitHub repository activate the GitHub Pages by go into `Settings` \ `Pages` and in the `Source` section select:

> ![image](https://user-images.githubusercontent.com/3258579/172229815-0382216f-4b42-4dce-a004-5396143be1b5.png)

> Note: There is no needed for you to create the branch `gh-pages`. This branch will be created automatically by the content in the `cd.yml` file.

### `.github/workflows/cd.yml`. 

An example of the content of this file can be found in https://github.com/OpenMobileAlliance/dmse-documentation/blob/master/.github/workflows/cd.yml

> Note: please note that branch `name`, could be set to `main` or `master` depending of what name you have in your own repository.
> In case you may need to change `master` for `main`, there are two places where this content needs to be udpated:
>  on:
>   push:
>    branches:
>      - main


and

>     steps:
>      - name: Checkout 🛎
>        uses: actions/checkout@main



Add the following content:

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

## Errors

### Missing Youtube Module

Run this command to install `nuxt-youtube-subscribe-module` if missing.

`$ npm install nuxt-youtube-subscribe-module --save`

## Footer, Header is Not Displayed
Some repositories have the ability to display a `Youtube` and `LinkedIn` logo at the header. This is in addition to the traditional `Twitter` and `GitHub` logols.
It was necessary to introduce further functionality to display the `Youtube` and `LinkedIn` logos. This functionality was introduced in a new folder called  `components/global`. 
Example of this folder can be found in this repo, [dmse-documenation](https://github.com/OpenMobileAlliance/dmse-documentation/tree/master/components/global)
