Previous: [206 Compose new tweets](./206-compose-new-tweets.md)

# 207 Upload photo with tweet
Its time we learn how to add photos to our tweet.
The markup below does not have former logic placed. It is supposed to help you understand better where the new elements should be placed.

## Add the button markup
```html

<div class="compose-tweet">

  <avatar></avatar>

  <div class="compose-tweet-content">
    <div class="compose-tweet-input-wrapper">
      <textarea placeholder="What's happening?" class="compose-tweet-input"></textarea>

      <!--
      bind the event listener for change on the input, on change call the function handleFileUpload
      -->
      <input type="file" accept="image/gif,image/jpeg,image/jpg,image/png" class="hide">

      <!-- bind a click listener and call the function triggerFileUppload-->
      <button class="tweet-file-button">
        <i class="fa fa-camera">
        </i>
      </button>
    </div>

    <!--
      Display when photo != ''
    -->
    <div class="uloaded-photos">
      <div class="photo">
        <img :src="photo" alt="Uploaded photo">

        <!-- Add click event that removes the added photo -->
        <button class="fa-stack">
          <i class="fa fa-circle fa-stack-2x"></i>
          <i class="fa fa-times fa-stack-1x fa-inverse"></i>
        </button>
      </div>
    </div>

    <div class="action-buttons">
      <!--
        bind a click listener and call the function triggerFileUppload
      -->
      <button class="tweet-file-button">
        <i class="fa fa-camera"></i>
      </button>

      <div class="tweet-counter">140</div>
      <button class="post-tweet">
        <i class="fa fa-paper-plane-o"></i> Tweet
      </button>
    </div>
  </div>
</div>
```

## Logic add the easy logic
Add the click events suggested

## Logic for adding files

#### `triggerFileUppload()`
When the camera button is pressed. We need to simulate a click `.click()` on the file input since we cannot style the input button otherwise. 

Add a reference on the file input that can be used to call a `click()` event on that element.

#### `handleFileUpload()`
This is what the `handleFileUpload()` should look like.

```javascript
handleFileUpload (e) {
  let reader = new FileReader()
  reader.readAsDataURL(e.target.files[0])

  reader.onloadend = event => {
    this.photo = event.target.result
  }
},
```

#### Spaghetti adjustments are needed!
Make some spaghetti adjustment to the `createNewTweet` event so that it passes the photo or `media_src` to the parents handler. Also solve the spaghetti for the fake `getNewTweetObj()` so that the passed photo / media_src will be added together with the new tweet.


# Next:
[208 Extras](./208-extras.md)
