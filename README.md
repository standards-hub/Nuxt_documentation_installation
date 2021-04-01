# Create and publish a Nuxt.js powered website on Github pages
#### 1.  To get started quickly you can use the create-nuxt-content-docs package.
    `yarn create nuxt-content-docs <project-name>`
#### 2.	cd my-project
#### 3.	Install vue-cli:
    `npm install -g vue-cli`
    `npm install`
#### 4.	Update nuxt.config.js to add a base URL (replace my-project by your project name):
    `router: { base: '/my-project/' },`
#### 5.	Install push-dir:
    `npm install push-dir --save-dev`
#### 6.	Create a deploy command to publish to Github pages by editing package.json file and adding this line at the beginning of the script section:
    `"deploy": "push-dir --dir=dist --branch=gh-pages --cleanup",`
#### 7.	Then commit and push your code to your repository (replace me by your name and my-project by your project name):
      `git init
      `git add .
      `git commit -m "init"
      `git remote add origin https://github.com/me/my-project.git
      `git push -u origin master`
#### 8.	Generate the site and publish it:
    `npm run generate`
    `npm run deploy`
