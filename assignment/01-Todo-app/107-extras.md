Previous: [106 Add todo](./106-add-todo.md)

![matrix](https://media.giphy.com/media/Q9aBxHn9fTqKs/giphy.gif)
# Enter the matrix!

🌶 = Refreshing

🌶🌶 = MmMm.. Spicyy...

🌶🌶🌶 = Daaaiiim that's hot!

🌶🌶🌶🌶 = I CAN'T FEEL MY LEGS! 

## Auto focus 🌶
When the page refreshes or when you enter the page for the first time. Find out a way to autofocus the input at start.

#### Reading tips:
- [Instance-Lifecycle-Hooks](https://vuejs.org/v2/guide/instance.html#Instance-Lifecycle-Hooks)
- [Instance-Lifecycle-Hooks - Mounted](https://vuejs.org/v2/api/#mounted)
- [Register references](https://vuejs.org/v2/api/#ref)

#### Tip:
> you can easily trigger some of the most common events like click() or blur() at a referenced element.

## Remove todo 🌶🌶
We should add the ability to remove a todo. But thus functionality comes with a cost that we need to change things up a bit. Because if we now click anywhere on the `<li class="todo-list-item"></li>` we'll complete the task which is not what we want. So add the following buttons and markup so it, without logic, looks like this. Follow the instructions and add a method that can remove an item from the todos array.
```html
<li class="todo-list-item" v-for="todo in uncompletedTodos">

    <!--
        Add a click event listener that toggles the value of completed
    -->
    <button class="btn-circle complete"></button>
    
    {{ todo.text }}

    <!--
        Add a click event listener that removes the current todo
        I suggest passing the current tweet to he method and then splice the 
        index of that tweet.
    -->
    <button class="btn-circle delete" @click="removeTodo(todo)"></button>
</li>
```

Also add the ability to remove the completed tasks as well.
```html
<li v-for="todo in completedTodos">
    <span class="completed" v-on:click="todo.completed = !todo.completed">
        {{ todo.text }}
    </span>

    <!--
        Add a click event listener that removes the current todo from the todos list
    -->
    <button class="btn-circle delete"></button>
</li>

```


## Add an action bar with more control! 🌶🌶
Lets add some more control and actions to our todo list. Add the following markup between the `<li class="add-todo"></li>` and `<li class="todo-list-item"></li>`
```html
<li class="todos-action-bar">
    <div class="amount-left-todo">
        {{ uncompletedTodos.length }}
        att göra
    </div>

    <!--
        Add a click event listener that calls a method called markAllCompleted.
        Create the method and logic needed
    -->
    <button class="btn-xs complete">
        Avsluta alla
    </button>

    <!--
        Add a click event listener that calls a method called removeAllCompleted.
        Create the method and logic needed
    -->
    <button class="btn-xs delete">
        Radera alla avslutade
    </button>
</li>
```

## Local storage 🌶🌶🌶
Add the list to local storage and sync the data needed when anything changes.

## `vue-transitions` 🌶🌶🌶🌶
Read more about [vue-transitions](https://vuejs.org/v2/guide/transitions.html) and use it to make animation for the lists when an item is added or removed from a list.
