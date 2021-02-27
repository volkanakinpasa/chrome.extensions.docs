# Content Script

## How to send a message object to the background script

You can send a message from content script to background script

```javascript
chrome.runtime.sendMessage({
  type: 'setBadgeText',
  data: 'Hi',
});
```

In order to listen this message in background script click here [How to listen message in background script](background?id=how-to-listen-message-in-background-script)

## How to listen message in content script

in this senario, once you send a message from background script, can listen it here

```javascript
chrome.runtime.onMessage.addListener(function (message, sender, sendResponse) {
  switch (message.type) {
    ...
    case 'showAlertInContenScript':
      ...
      alert('Messaeg is here');
      break;
    ...
  }
});
```

## How to inject an html/css in DOM
