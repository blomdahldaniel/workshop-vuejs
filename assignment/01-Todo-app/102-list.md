Previous: [101 Setup](./100-setup.md)

# 102 Create a list

1. Add a variable called `todos` to your Vue data that is an array with at least 8 things you have to do today, even things you have already done. For example:
```javascript
var app = new Vue({
    el: '#vue-container',
    data: {
        header: 'My todo list!',
        todos: [
            {
                text: 'Wake up, plz dont snooze..',
                completed: true,
            },
            {
                text: 'Fall in love with VueJS..',
                completed: true,
            },
            {
                text: 'Become a pro at VuejS!',
                completed: false,
            }......
        ]
    }
})
    // ...
```

1. Create a `<ul>` and inside that, loop over the todos and echo out the `text`. [Read more about list-rendering here.](https://vuejs.org/v2/guide/list.html)
```html
<div id="vue-container">
    <ul>
        <!-- Loop over the todos -->
        <li>
            <!-- Print out the text property -->
        </li>
    </ul>
</div>
```

# Next:
[103 Completed todos](./103-completed.md)
