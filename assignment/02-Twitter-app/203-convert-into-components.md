Previous: [202 List of tweets](./202-list.md)
# 203 Convert into component
Now lets extract the whole `<div class="tweet"></div>` element. We want to reference it as `<tweet></tweet>` instead.

1. Create a `src/components/Tweet.vue` component. Cut out the entire `<div class="tweet"></div>` block and paste it inside the `Tweet.vue` `<template>`
1. Create the vue componant instance inside the `<script></script>`
```javascript
export default {
  name: 'tweet' // refers to the component name: <tweet></tweet>
}
```
1. Import and add the `tweet` component to the parent

```javascript
// App.vue
import tweet from './components/tweet.vue'

export default {
    ...
    components: {
      tweet
    }
}
```

4. The `App.vue` template should then look like this:

```html
<template>
    <div id="app"> <!-- this is our outer vue container -->
        <div class="tweets-wrapper">
          <!-- Loop through the tweets array -->
          <tweet></tweet>
        </div>
    </div>
</template>
```

5. But how do we access the active tweet data this way? Well, we need to pass the `tweet` object through a property. So bind a property to the new `<tweet>` element. Like so `<tweet :tweet="tweet">` (also don't forget to add the for loop on the `<tweet>` component)

6. Now you need to set up the `Tweet.vue` file so that you can use the passed tweet data. [Read more about component properties here](https://vuejs.org/v2/guide/components.html#Props)

#### You might want to read more about `keys`-for list rendering:
https://vuejs.org/v2/guide/list.html#key

# Next:
[204 More components](./204-more-components.md)
