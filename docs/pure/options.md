# Options Page

## How to save an object into storage

This is the same as in background.js. Visit the link [How to save an object into storage](background?id=how-to-save-an-object-into-storage)

## How to send a message object to the background.js

```javascript
//options.js >> send message
chrome.runtime.sendMessage({
  type: 'setBadgeText',
  data: 'Hi',
});
```

Visit the link [How to listen message in background.js](background?id=how-to-listen-message)

Note: The fields are custom in message object you are free to add any object inside in any case you don't want to use `type` and `data`.

## How to set badget text from Option Page

You can only set badget
