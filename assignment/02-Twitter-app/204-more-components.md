Previous: [203 Convert into components](./203-convert-into-components.md)

![You guys give up or are you ready for more?](https://media.giphy.com/media/3ofT5Mzq0fk0ts1vig/giphy.gif)

# 204 More components
You have now successfully extracted your own `<tweet>` component. Lets extract some more!

## Avatar component `<avatar>`
For the avatar image, create a component called `<avatar>` and pass the props:
- size="md"
- type="square"
- :src="tweet.user.picture.thumbnail"

#### Default property values
The component should have default values and some rules for the props. So that if the component is referenced and some props are not set, the component should fall back on some default values, for example, default size: 'md', default type: 'square'. Then, what happens if you remove the passed props..? [Read more about default values here](https://vuejs.org/v2/guide/components.html#Prop-Validation)

#### Computed property for the class
Create a computed property called `classes` and bind that value to the `img` elements class attribute. The computed property should return a string: `return this.size + ' ' + this.type`. This will then set the right classes for the avatars type and size.

## Tweet media component `<tweet-media>`
Create a component called `<tweet-media>`, pass the props:
- :src="tweet.media_src"
- :alt="tweet.text + ' ' + tweet.time"

#### Click the wrapper
Some images are too big to be displayed in the twitter flow. Those images are cropped out by the `.media-wrapper` object. But if we add a class of `expanded` to the `.media-wrapper` the whole image is shown. To test it out, open dev-tools and add the class `expanded` to the `<div class="media-wrapper">` class.

Now we want to control this by the user:

- Set a click event listener on the `media-wrapper` that toggles a boolean variable named `isExpanded`.
- Apply the class `expanded` to the `media-wrapper`-div-element if `isExpanded == true

# Next:
[205 Like my tweets](./205-like-my-tweets.md)
