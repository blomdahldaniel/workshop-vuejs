Previous: [204 More components](./204-more-components.md)

# 205 Like my tweets!
Let's add some action buttons for every tweet!
We want to be able to like a tweet and also see what tweets that are liked.

## Create a `<tweet-action-buttons>` component
Lets ad another component! This one will be a `<tweet-action-buttons>` that let us interact with the tweet.
Create the component and place it inside the `<tweet>` component right after the `<tweet-media>` component. Pass the `tweet` object to the `tweet-action-button` component.

#### template:
```html
<template>
    <div class="action-buttons">
      
      <!--
        Add an event listener for click and then call the method replyToTweet
        This method should emit and event back to the parent component
      -->
      <button class="reply">
        <i class="fa fa-reply"></i>
        <!-- print out the tweet.reply_count -->
      </button>

      <!--
        Add an event listener for click and then call the method retweetTweet
        This method should emit and event back to the parent component
      -->
      <button class="retweet">
        <i class="fa fa-retweet"></i>
        <!-- print out the tweet.retweet_count -->
      </button>

      <!--
        Add an event listener for click and then call the method likeTweet
        This method should emit and event back to the parent component
        Also add a class of 'active' if the tweet.liked is true
      -->
      <button class="like">
        <i class="fa fa-heart"></i>
        <!-- print out the tweet.like_count -->
      </button>
    </div>
</template>
```

## Listen for the events in the parent:
Start with adding listeners `v-on` to the event names. After that create appropriate methods on the parent that should be called. Start with confirming that it works by printing to the console.

After that, start with adding logic to the method that handles the like click.
For example:
```javascript
// ...
methods: {
    tweetWasLiked (tweet) {
        this.tweet.liked = !this.tweet.liked
        this.tweet.like_count += this.tweet.liked ? 1 : -1
    }
}
```

## That's good for now!
We'll come back to the other buttons in the "Extras" assignment.

# Next:
[206 Compose new tweets](./206-compose-new-tweets.md)
