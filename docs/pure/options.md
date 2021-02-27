# Options Page

## How to save an object into storage

This is the same as in background.js.

First of all you must add storage permission in manifest.json file

```json
//manifest.json
{
...
"permissions": [ "storage" ],
...
}
```

then, in javascript file

```javascript
chrome.storage.sync.set({ key: value }, function () {
  console.log('Value is set to ' + value);
});
chrome.storage.sync.get(['key'], function (result) {
  console.log('Value currently is ' + result.key);
});
```

## How to send a message object to the background.js

```javascript
//options.js >> send message
chrome.runtime.sendMessage({
  type: 'setBadgeText',
  data: 'Hi',
});
```

How to listen from background page [How to listen message in background.js](background?id=how-to-listen-message-in-backgroundjs)

Note: The fields are custom in message object you are free to add any object inside in any case you don't want to use `type` and `data`.

Debug: in order to debug the message in background.js, right click on the extension > "Manage Extensions" > under "Inspect views" click on "background page".
