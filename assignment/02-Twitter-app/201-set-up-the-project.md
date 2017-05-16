Previous: [200 Intro](./200-intro.md)

# 201 Set up the new project with [vue-cli](https://github.com/vuejs/vue-cli)
>**vue-cli** is a simple CLI for scaffolding Vue.js projects. Use vue-cli as a zero-configuration development tool for your Vue apps and component, check out the [docs](https://github.com/vuejs/vue-cli/blob/master/docs/build.md).

>The purpose of official Vue project templates are to provide opinionated, battery-included development tooling setups so that users can get started with actual app code as fast as possible. However, these templates are un-opinionated in terms of how you structure your app code and what libraries you use in addition to Vue.js.

1. Install the `vue-cli` command globally through npm:
```bash
npm install -g vue-cli@latest #bcause we are hard core 
```
2. Create a new project, use the `webpack` template and name the project to `twitter-app`.
```
vue init webpack twitter-app
```
This will trigger the installation process where you set different options for your project. You can also choose to use a js linter if you are all about the syntax-nazi..

Here's a suggested way to answer the install questions:

![vue-cli](http://dobloit.se/images/workshop-yrgo/terminal-vue-cli-install.png)

Continue with:
```bash
cd twitter-app
yarn install # or 'npm install'
npm run dev # to boot up the app on localhost:8080
```

## Explore the structure
Start exploring the structure of the project. I suggest that you start to click around and check out how the project is laid out. At least look at the following files:
- Find the `index.html`, make changes and see what happens in the browser, do you need to refresh after change?
- Find `App.vue`, make changes and see what happens in the browser, do you need to refresh after change?
- Find `Hello.vue` component, make changes and see what happens in the browser, do you need to refresh after change?

# Next:
[202 List of tweets](./202-list.md)
