Previous: [105 Computed properties](./105-computed-properties.md)

![Spamming keyboard](http://afflictor.com/wp-content/uploads/2016/06/carreykeypboardtypewriter.gif)

# Add Todo
A todo list is not for much use if you can't add more things todo? Lets add an input that lets us add new todos!

Add this at the top of the `<ul class="todos-list">` 
```html
<li>
    <input type="text" placeholder="Lägg till din nya uppgift här...">
    <button>+ Lägg till</button>
</li>
```

1. Bind a model to the input called 'newTodo'
2. Bind a click event listener for the button that calls a method that pushes the new todo object to the list. Dont forget to add a todo property where `completed` is false`.
3. When the new todo is added, empty out the input so that you are ready to write in another one.

#### Abort mission!
With vue it's super easy to add great usability for the user. Lets add a nice way to abort/cancel the new todo. Bind an event listener on the input that listens for the `ESC` key to be pressed. When it is pressed, empty out the `newTodo`.

[Read some more about key modifiers.](https://vuejs.org/v2/guide/events.html#Key-Modifiers)

#### Enter to add
While we're at it, remove the `button` completely and add an event listener that listens for when `enter` is pressed on the input.

#### Let's add some style!
Add a class of `add-todo` to the list item that wraps the input.

# Next:
[107 Extras](./107-extras.md)
