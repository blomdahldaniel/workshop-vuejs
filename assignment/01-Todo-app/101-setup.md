Previous: [100 Intro](./README.md)

# 101 Setup

1. Create a project folder called `Todo App/` go into that folder and use it as root for the rest of this project.
1. Download the [todo-app.css](../../resources/todo-app/todo-app.css) and store it inside `Todo App/css/todo-app.css`
1. Create a new blank file called `index.html`. Paste in the following:
```html
<!DOCTYPE html>
<html>
<head>
    <title>VueJS - Workshop</title>
    <!-- Google Fonts -->
    <link href="https://fonts.googleapis.com/css?family=Open+Sans:300,400,700" rel="stylesheet">

    <!-- Nothing special, just some simple css -->
    <link rel="stylesheet" href="./css/todo-app.css">
</head>
<body>

</body>
</html>

```
4. We need to get vue and we will use a `cdn` for now. At the bottom of the body tag, add 
```html
<script src="https://unpkg.com/vue"></script>
```
5. Add a Vue instance, add it add within a `<script></script>` section after the `unpkg`-script. [Read more about the vue instance](https://vuejs.org/v2/guide/instance.html)
```html
<script>
    var app = new Vue({
    })
</script>
```
6. Next, create a `div` with the id of `vue-container` so that we can use that as our element where we'll target our Vue logic. Also, tell Vue that it should use this div as its element.
1. After that, make sure you can set the vue data property correct and echo out some test value. For example a `<h1>{{ header }}</h1>`. [Read more about text rendering](https://vuejs.org/v2/guide/syntax.html#Text)

# Next:
[102 Create a list](./102-list.md)
