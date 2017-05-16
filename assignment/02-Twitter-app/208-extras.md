Previous: [207 Upload photos to new tweets](./207-upload-photos.md)
# Extras
Here are suggestions for how you can improve the twitter app.

🌶 = Refreshing

🌶🌶 = MmMm.. Spicyy...

🌶🌶🌶 = Daaaiiim that's hot!

🌶🌶🌶🌶 = I CAN'T FEEL MY LEGS! 

## Better timestamps for the `<tweet>` 🌶
Now that you have added the `moment.js` library I suggest that you, instead of showing each `<tweet>`s full `time` property instead show the moment [fromNow()](https://momentjs.com/docs/#/displaying/fromnow/) value. I suggest adding a method called `timeFromNow()` and instead of printing out the `tweet.time` property, pass the time string to the method and use `moment.js` to return the `fromNow()` value.

## Store the tweets in local storage  🌶🌶
Instead of importing the `tweets.js` file. Use the localstorage to store and update the tweets.
>Hint: fetch the data when the vue instance is mounted..

#### For convenience - add delete button 🌶
You might add a "delete tweet" button to each tweet so that you can remove the tweets that you don't want.

## Add transitions for added tweets  🌶🌶🌶
Add a list transition for the tweets. This should give a nice slide down effect for when a new tweet is added

## Create a modal component for displaying `tweet.media_src`  🌶🌶🌶
Create a modal look at the [Official Vue modal example](https://vuejs.org/v2/examples/modal.html). Make it so that instead of expanding the media_wrapper. The media should be displayed in a big modal above other content instead.

## Create a modal modal-component 🌶🌶🌶
Create a simple modal component. Take inspiration from this [Official Vue example](https://vuejs.org/v2/examples/modal.html). I suggest that you add the styling to the components `<style></style>`-tags.
The content within the modal should be a `<slot>` so that the content can vary and be dynamic. Read more about [component slots here.](https://vuejs.org/v2/guide/components.html#Single-Slot).

## Retweet modal dialog 🌶🌶🌶🌶
Okey, if you now have a modal component. It should be easy to add the ability to retweet a tweet. Look at the current data structure in the `tweets.js` file. See how retweets are structured there.

When pressing the retweet button, a modal should pop up saying "Are you sure you want to retweet this" and then it should be a preview of the retweet inside the modal. And pressing OK should perform the retweet and add it to the tweets-array.

The same user may not tweet the same thing twice.. (this will be a pretty scetchy and not scaling solution, but make it work!)

You might have to create a better method that can handle the posting of tweets that are retweets and get the fake the new data from that.

