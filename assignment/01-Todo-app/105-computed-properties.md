Previous: [104 Let's add some style](./104-style.md)

![Computed properties](http://mktcdn.uberflip.com/get-to-work.gif)
# 105 Computed Properties
Okey, now we have a pretty good looking list. But we don't want the completed todos to be clumped up with the todos that is not completed.
Let's keep them separate like this:

```html
<div id="vue-container">
    <ul class="todo-list">

        <li class="todo-list-item"
            v-for="todo in uncompletedTodos"
            v-on:click="todo.completed = !todo.completed"
        >
            {{ todo.text }}
        </li>
    
        <!--
            Only display this lit item if there is no uncompleted todos
        -->
        <li class="empty-placeholder"
        >
            Det finns inga uppgifter att göra!
            <br>
            <small>Njut så länge det varar...</small>
        </li>
    </ul>
    
    <!-- 
        Only display this div if there is no completed todos
    -->
    <div>
        <!-- Print out the number of completed todos -->
        <h3></h3>
        <ul>
            <li v-for="todo in completedTodos"
                v-on:click="todo.completed = !todo.completed"
            >
                <span class="completed">
                    {{ todo.text }}
                </span>
            </li>
        </ul>
    </div>
</div>
```

#### uncompletedTodos and completedTodos ??
If you look closely, I have suggested to loop trough two different lists `uncompletedTodos` and `completedTodos`. These are both computed properties that returns the array of todos that match the names. This is a nice way to be descriptive and distinct. Computed Properties are reliant on other data and is sensitive for when the user is changing the data.

- Add the computed property `uncompletedTodos` return an array of todos that are not completed
- Add the computed property `completedTodos` return an array of todos that are completed

#### Hide and show empty state
We've also added a couple of conditionals for better state handling.

- Display list item `<li class="empty-placeholder"></li>` if `uncompletedTodos.length == 0`
- Hide the uncompleted list `div` wrapper if `completedTodos.length == 0`

# Next:
[106 Add todo](./106-add-todo.md)
