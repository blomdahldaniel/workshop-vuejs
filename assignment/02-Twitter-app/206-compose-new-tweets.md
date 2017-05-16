Previous: [205 Like my tweets](./205-like-my-tweets.md)

# 206 Compose new tweets!
It is time we learn how to write and post our own tweets!

## Before we start! - Add the active users data
Before we start composing a tweet, we need to know who is tweeting!
Add the data for the current signed in user to the `App.vue`:
> This, of course, is also a fake way of doing it!

```javascript
user: {
  verified: false,
  name: 'Vue Newbie',
  screen_name: 'vuenewbie1337',
  picture: {thumbnail: 'https://upload.wikimedia.org/wikipedia/commons/5/5d/Vue.js_Logo.png'}
}
```

## Create a new component `<compose-tweet>`
The component should receive the user variable from the parent as a property

#### template:
```html
<div class="compose-tweet">

    <!--
      Add the avatar component here,
      The size should be "xs"
      The type should be "square"
      The src should be user.picture.thumbnail
    -->

    <div class="compose-tweet-content">
      <div class="compose-tweet-input-wrapper">

        <!--
          Add a textarea here
          Add an event listener for when the textarea is focused, call a method called 'activateEdit'
          Add an event listener for when the textarea is blured, call a method called 'bluredTextarea'
          Bind a class of active when isActive
          Bind a variable called 'newTweetText' to the textarea
        -->
        <textarea class="compose-tweet-input" placeholder="What's happening?"></textarea>
      </div>
      <div v-show="isActive" class="action-buttons">

        <!--
          This is where the number of allowed characters should be visible.
          The tweet may contain 140 characters. When the textarea is empty, display 140, that number is decreasing for every added character, call this number "tweetCounter". The tweetCounter can have a negative number.
          Bind a variable called tweetCounterClass to the class attribute.
          The tweetCounterClass should return 'warning' if tweetCounter <= 20 && tweetCounter > 10
          The tweetCounterClass should return 'superwarning' if tweetCounter <= 10
        -->
        <p class="tweet-counter"></p>

        <!--
          Bind a class of 'disabled' when tweetCounter < 0 || tweetCounter == 140
          Bind a disabled attribute when tweetCounter < 0 || tweetCounter == 140
          Add an event listener for click that calls a method of "createNewTweet"
        -->
        <button class="post-tweet">
          <i class="fa fa-paper-plane-o"></i> Tweet
        </button>

      </div>
    </div>
</div>
```

## Some logic pointers

- The `activateEdit` method should set a truthy value to `isActive`. `isActive` should be false by default.
- The `bluredTextarea` method should set a falsy value to `isActive`.
- The `createNewTweet` method should emit an event called `create-new-tweet` and should pass the `user` object together with the `newTweetText`
- The event `create-new-tweet` on the parent should be handled by a method called `postNewTweet`

The `postNewTweet` method should look like this (and call another method).
```javascript
createNewTweet (user, newTweetText) {
  console.log('the parent received "create-new-tweet"')
  
  // In reality this would send an ajax request to backend to store and retreive the new tweet object
  let tweet = this.getNewTweetObj(user, newTweetText)
  // update the tweets array with the added tweet
  this.tweets = tweet.concat(this.tweets)
},
getNewTweetObj (newTweetText) {
  // this simulates an ajax request that returns the new tweet obj
  // The method returns an array to be able to use concat in a neet way to prepend the array. Normally, the tweets array would be streamed and ordered by date.
  return [{
    id: Math.random().toString(36).substring(7), // sets a random id
    user: {
      verified: false,
      name: this.user.name,
      screen_name: this.user.screen_name,
      picture: {thumbnail: this.user.picture.thumbnail}
    },
    retweeted: false,
    liked: false,
    text: newTweetText,
    media_src: '',
    media_expanded: false,
    time: moment().format('YYYY-MM-DD HH:mm'),
    retweet_count: 0,
    like_count: 0
  }]
}
```

## What is moment..?
But wait..? What is moment? Well, I was lazy and used [moment.js](https://momentjs.com/). It is a neat javascript lib that makes handling dates easy. Just pull it in from npm and then import it. Like this
```bash
yarn add moment # or 'npm install moment --save'
```

Then inside the `.vue` file for `<compose-new-tweet>` add this line above the vue object:
```javascript
import moment from 'moment'
```

# Next:
[207 Upload photos to new tweets](./207-upload-photos.md)
