Previous: [201 Set up the project](./201-setup.md)
# 202 List of tweets
Normally you would get your tweets from an api. But for now you'll be provided with a dummy-data-file that contains a couple of tweets that we'll be working with. 

## 1. Clean up the `App.vue`-file
Begin with cleaning up the `App.vue` file. The whole file should look look like this:

```vue
<template>
  <div id="app">
  </div>
</template>

<script>

export default {
  name: 'app',
}
</script>

<style>
</style>

```

## 2. Import the tweets dummy data
- Copy the [tweets.js](../../resources/twitter-app/tweets.js) file into `twitter-app/static/dummy-data/tweets.js`
- Import the tweets.js file to the `App.vue` file. After that, set the imported tweets in the vue data prop.

```javascript
import tweets from '../static/dummy-data/tweets.js'

export default {
    name: 'app',
    data () {
        return {
            tweets, // this is ES2015 equalent to 'tweets': tweets
        }
    }
}
```

## 3. Pull in some resources
- Copy the [CSS-file](../../resources/twitter-app/twitter-app.css) to the new project folder: `/static/css/twitter-app.css`.
- Copy the [HTML-file](../../resources/twitter-app/index.html) and replace the content inside the `/twitter-app/index.html`

Refresh the site and hopefully you're g2g!

## 4. Display the tweets
Replace the `App.vue` `<template>` with the following markup and follow the instructions in the comments. It wont be pretty, but at least we'll know if things are working!

>### Tip:
>open the dev-tools and check the console for some good pointers when things are not working.

```html
<template>
    <div id="app"> <!-- this is our outer vue container -->
        <ul>
            <!-- Loop through the tweets array and print out each `tweet.text` value -->
            <li></li>
        </ul>
    </div>
</template>
```

## 5. Now lets show off the real deal!
Nice, when you've got that working, lets add the real boilerplate for a tweet. Paste in the following instead of the `<ul>`-block and follow the instructions.
Once this is done, we'll have a much more "real looking twitter app"

```html
<div class="tweets-wrapper">
    <!-- Loop through the tweets array -->
    <div class="tweet">

      <!-- Display this block if "tweet.is_retweet" -->
      <div class="retweet-wrapper">
        <div class="fa-stack fa-xs">
          <i class="fa fa-square fa-stack-2x"></i>
          <i class="fa fa-retweet fa-stack-1x fa-inverse"></i>
        </div>
        <!-- echo out the tweet.retweet_user.name here  -->
        retweeted
      </div>
      <div class="tweet-wrapper">

        <!--
          This is the avatar img of the tweets user. 
          bind the src attribute to the value of tweet.user.picture.thumbnail
          bind the alt attribute to the users name
        -->
        <img src="" class="avatar md square">

        <div class="tweet-content">
          <div class="header">
            <div class="user-name">
              <!-- Print out the tweet.user.name -->
            </div>
            <div class="user-screen_name">
              
              <!-- 
                Print out the tweet.user.screen_name,
                screen_name is what Twitter calls the username themselves
              -->
            </div>
            <div class="time">
                <!-- Print out the time prop -->
            </div>
          </div>
          <div class="text">
            <!-- Print out the text prop -->
          </div>

          <!--
            This is a wrapper for when the tweet contains a photo
            Only show this div if the tweet.media_src is not an empty string
            bind the src attribute to tweet.media_src
            bind the alt attribute to "tweet.text + ' ' + tweet.time"
          -->
          <div class="media-wrapper" alt="">
            <img class="media" src="" alt="">
          </div>
        </div>
      </div>
    </div>
  </div>
```
# Next:
[203 Convert into component](./203-convert-into-components.md)
